# Operationaliing Machine Learning

This project is part of the Udacity Azure ML Nanodegree.
In this project, we use Microsoft Azure to configure a cloud-based machine learning production model, deploy it, and consume it. We also create, publish, and consume a pipeline. 

## Summary
This dataset contains data about customers who are contacted to market banking products. We seek to predict if the customer will buy the product. The dataset has 21 columns out of which 20 are used as input features and 1 target column. Input features include information about customer such as age, job type, marital status, education, housing, information about contacts made with customer, outcome of previous campaign etc. Target column indicates if the customer has subscribed to term deposit. Possible values of target column are yes / no.

## Architectural Diagram
![Screenshot](Screenshots/ArchitectureDiagram.png)

## Key Steps
*	The first step is automated ML experiment. We execute this step using a Jupyter notebook. Initially we create a new compute cluster of type Standard_DS12_V2.
![Screenshot](Screenshots/Compute.jpg)

*	Then we create an Azure dataset for the bank marketing data that is available in public domain.
![Screenshot](Screenshots/BankMarketing&nbsp;Dataset.jpg)

*	We create an automated ML run for a classification experiment providing automlconfig and automlstep. The run is submitted. It generates and tests a number of machine learning models. 
![Screenshot](Screenshots/AutoMLmoduleCompleted.jpg)

*	Upon completion it shows the best model of the run. The best model generated in our case is MaxAbsScaler,LightGBM with metric AUC_Weighted 0.94505
![Screenshot](Screenshots/BestModelSummary.jpg)

*	The next step is to deploy the best model. We deploy this model using Azure Container Instance. We get a model endpoint.
![Screenshot](Screenshots/BestModelDeployed.jpg)

*	We need logs for the run. So we use a python script logs.py to enable Application Insights which lets us retrieve log files. 
![Screenshot](Screenshots/EndpointApplicationInsightsEnabled.jpg)

*	The next step is Swagger documentation. We use a script swagger.sh to run an instance of swagger container on port 9000. Then we use a python script to run a Python server on port 8000. It needs a file swagger.json in the same directory. We use a browser to interact with the swagger instance running with the documentation for the HTTP API of the model.
![Screenshot](Screenshots/swagger1.jpg)

*	The next step is to consume model endpoints. We use scoring URI and key of the deployed model to execute a Python script endpoints.py. This script sends a sample POST request to the model. 
![Screenshot](Screenshots/endpointdotpy_output2.jpg)

*	The next step is to benchmark the model. We use a script benchmark.sh that uses Apache benchmark. The output contains information for Requests per second, time per request etc.

*	The next step is to create, publish and consume a pipeline. We again use the Jupyter notebook for this purpose.  It creates and publishes a pipeline. 
![Screenshot](Screenshots/pipelineInNotebook.jpg)

*	We can view the progress of the pipeline using Use Run Details widget
![Screenshot](Screenshots/pipelineInStudio.jpg)

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:



