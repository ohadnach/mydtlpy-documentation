## Introduction  
This tutorial will help you get started with FaaS.  
1. Prerequisites  
2. Basic use case:  Single function  
    1.1 Deploy a function as a service  
    1.2 Execute the service manually and view the output  
3. Advance use case: Multiple functions  
    3.1 Deploy several functions as a package  
    3.2 Deploy a service of the package  
    3.3 Set trigger events to the functions  
    3.4 Execute the functions and view the output and logs  
  
First, log in to the platform by running the following Python code in the terminal or your IDE:  

```python
import dtlpy as dl
if dl.token_expired():
    dl.login()
```
Your browser will open a login screen, allowing you to enter your credentials or log in with Google. Once the "Login Successful" tab appears, you are allowed to close it.  
  
This tutorial requires a project. You can create a new project, or alternatively use an existing one:  

```python
# Create a new project
project = dl.projects.create(project_name='project-sdk-tutorial')
```

```python
# Use an existing project
project = dl.projects.get(project_name='project-sdk-tutorial')
```
Let’s create a dataset to work with and upload a sample item to it:  

```python
dataset = project.datasets.create(dataset_name='dataset-sdk-tutorial')
item = dataset.items.upload(
    local_path=[
        'https://raw.githubusercontent.com/dataloop-ai/tiny_coco/master/images/train2017/000000184321.jpg'],
    remote_path='/folder_name')
# Remote path is optional, images will go to the main directory by default
```
