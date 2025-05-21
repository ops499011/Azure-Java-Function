# Project Title
Azure Functions HTTP Trigger Example

# Description
This project is a simple Java Azure Function that demonstrates an HTTP trigger. It accepts a name via a GET or POST request and returns a greeting message.

# Prerequisites
- Java Development Kit (JDK) 8 or later
- Apache Maven 3.0 or later
- Azure Functions Core Tools (optional, for local development)
- An active Azure subscription (for deploying to Azure)

# How to Run

## Locally
1. Clone this repository.
2. Open a terminal in the root directory of the project.
3. Run the command: `mvn clean package`
4. Run the command: `mvn azure-functions:run`
5. The function will be available at `http://localhost:7071/api/HttpExample`.

## Deploy to Azure
1. Make sure you have the Azure CLI installed and configured.
2. Run the command: `mvn azure-functions:deploy`
   (You might be prompted to log in to your Azure account if you haven't already.)
3. The function will be deployed to your Azure Functions App. You can find the endpoint URL in the Azure portal or in the output of the deploy command.

# How to Use
You can invoke the HTTP trigger using `curl` or any HTTP client.

## Using curl (GET request):
```bash
curl "{your host}/api/HttpExample?name=YourName"
```
Example:
```bash
curl "http://localhost:7071/api/HttpExample?name=World"
```
Output:
```
Hello, World
```

## Using curl (POST request):
```bash
curl -d "YourName" "{your host}/api/HttpExample"
```
Example:
```bash
curl -d "World" "http://localhost:7071/api/HttpExample"
```
Output:
```
Hello, World
```

Replace `{your host}` with the actual host (e.g., `http://localhost:7071` for local execution or your Azure Function App URL).
If the `name` parameter is not provided, the function will return a `400 Bad Request` with the message: "Please pass a name on the query string or in the request body".
