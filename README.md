# SapaJari-Flask Documentation
Welcome to our SapaJari-Flask API

# Flask App Deployment using Google App Engine (GCP)

This repository contains a Flask application that can be deployed to Google App Engine using GCP. It provides step-by-step instructions on how to set up and deploy your Flask application on GCP.

## Prerequisites

Before you begin, ensure that you have the following prerequisites:

- A Google Cloud Platform (GCP) account
- Google Cloud SDK installed on your local machine
- Python 3.x installed on your local machine
- Git installed on your local machine

## Deployment Steps

Follow these steps to deploy your Flask application using Google App Engine on GCP:

1. Clone the Flask application repository to your local machine using the following command:
```bash
git clone https://github.com/ywauran/sapajari_flask.git
```

2. Open a terminal or command prompt and log in to your Google Cloud account using the following command:
```bash
gcloud auth login
```

3. Create a new project in the Google Cloud Console if you haven't done so already.
4. Set up your project ID in the Google Cloud SDK:
```bash
gcloud config set project <YOUR-PROJECT-ID>
```

5. Navigate to the cloned repository directory:
```bash
cd sapajari_flask
```

6. Create a new virtual environment for your Flask application:
```bash
python3 -m venv venv
source venv/bin/activate
```

7. Install Flask and any other required dependencies:
```bash
pip install -r requirements.txt
```

8. Create a new file called `app.yaml` in the project directory. This file will define the App Engine configuration:
```bash
touch app.yaml
```

9. Open the `app.yaml` file in a text editor and add the following content:
```bash
runtime: python39
entrypoint: gunicorn -b :$PORT app:app

automatic_scaling:
    target_cpu_utilization: 0.65
    min_instances: 1
    max_instances: 10

instance_class: F4_1G

handlers:
    - url: /.*
      script: auto

```

10. Deploy your Flask application to App Engine using the following command:
 ```bash
 gcloud app deploy
 ```

11. During the deployment process, you may be prompted to select a region for your App Engine application. Choose the region that is closest to your target audience.

12. Once the deployment is complete, you will be provided with a URL where your Flask application is accessible.

Congratulations! You have successfully deployed SapaJari Flask application using Google App Engine on GCP. You can now access your application using the provided URL.
