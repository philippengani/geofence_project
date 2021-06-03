# Geofence Coding test

## Solution

### Choice of language and tools

Python was chosen as the programming language for building this API as it is widely used in backend development and has
powerful API frameworks such as **flask, Django and fastAPI.** The API framework used here is fastAPI as it is modern
and very high performant while being compatible with open standards for APIs. Other frameworks used include pydantic and
SQLAlchemy.

Furthermore, the database used for this micro api was SQLite because it is simple and python has integrated support for
it, hence facilitating the testability of the API. In the case of a production environment, PostgreSQL would have been
the database chose.

### Project design

The structure of the project follows the best practices as it facilitates understanding and maintainability. All
important functions are put the "api" package and each are called in the "main" python file.

#### 1. Models

The "`models.py`" file describes the structure of the patient model stored in the database. Patient attributes stored in
the database included values such as the **id, email, first_name, last_name, birthdate and sex**. In order to optimize the
database, the url of the patient was not stored in the database as it could be easily created with the `uri` and `id`, when
a request is made to the server.

#### 2. Schemas

The schemas used by the api are defined in the "`schemas.py`" file. Each schema is defined using python objects and
pydantic. It should be notes that the patient schema object used when creating a new patient is the "PatientBase" object
as it provides a clear understanding of the fields and types required to create a new patient. The "`id`" of a new patient
is only added when a patient is created.

Also, other schemas defined here are the `pagination` object and `HttpError`. The pagination schemas is used to create an
object containing information on the current and next page url. On the other hand, the HttpError schema is used to
define the structure of data returned by the server when any error occurs.

## Improvements

1- An optional variable "page" was added to the route used to the information of 10 patients. This facilitates exploring
the patient data for a specified page. If no page number is specified, the server will return data on the first 10
patients instead.

2- The exception handler was customized to return errors in a better format (provided by the `HttpError` schema). In this
case of missing fields, the api will return specific details on the missing required data.

3- The route "`/generate`" was added to facilitate the generation of 100 fake patient profiles. Thereby providing valuable
data to test the API.

## How to run

To run the API, follow these steps:

1- Install all packages in the requirements files:

`pip install -r requirements.txt`

2- Run the main python file :

`python main.py`

3- Create the 100 fake patient profiles by going to the route `/generate`.

If successful the response will be `{"result": "Successfully created the 100 fake profiles"}`

4- Since the fast api supports the openAPI standard, the API can be tested by using the route `/docs`


## Task Description

You're being given a swagger specification file which describes a micro api. The goal of the coding challenge is to
implement it with the language, frameworks and database of your choice.

## Task Description

* We expect a solution using any tools or libraries you believe are relevant to the completion of the tasks;
* We expect you to explain in the deliverable the choices that you made in term of tools & design;
* We will pay **a lot of attention** to code quality, maintainability, testability and best software engineering
  practices;
