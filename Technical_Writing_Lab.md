
# Technical Writing Lab Assignment

**Student Name:** Patrick Basoma

## Exercise A: User Manual Procedure

### Title: Creating a Python Virtual Environment and Installing a Package

### 1. Purpose
This procedure explains how to create a Python virtual environment, activate it, and install the Requests package.

### 2. Prerequisites
- A computer running Windows.
- Python installed.
- Visual Studio Code or Git Bash.
- An internet connection.
- Basic computer literacy.

### 3. Procedure

**Step 1: Open Git Bash.**

Action: Open Git Bash on your computer.

Expected result: The terminal window opens.


**Step 2: Create the project folder.**

Action: Run `mkdir python_project`.

Expected result: A folder named `python_project` is created in the current directory.

**Step 3: Enter the project folder.**

Action: Run `cd python_project`.

Expected result: The terminal moves into the project folder.

**Step 4: Create the virtual environment.**

Action: Run `python -m venv venv`.

Expected result: A folder named `venv` is created.

**Step 5: Activate the virtual environment.**

Action: Run `source venv/Scripts/activate`.

Expected result: The terminal displays `(venv)`.

**Step 6: Install the package.**

Action: Run `python -m pip install requests`.

Expected result: The Requests package installs successfully.

**Step 7: Verify the installation.**

Action: Run `python -m pip show requests`.

Expected result: The package name, version, and installation location are displayed.

### 4. Screenshot Description
Include a screenshot showing the Git Bash terminal after running `python -m pip show requests`. The screenshot should display the Requests package information and the `(venv)` prompt.

### 5. Troubleshooting
Problem: Python is not recognized.

Solution: Install Python from https://www.python.org/downloads/windows/. During installation, enable Add Python to PATH. Open a new terminal and run `python --version`.

### 6. Conclusion
The virtual environment was created and activated successfully, and the Requests package was installed and verified.

# Exercise B: API Reference Entry

## Endpoint: Create a New Task

**HTTP Method:** POST

**Endpoint Path:** `/v1/projects/{project_id}/tasks`

### Description
This endpoint creates a new task in a project management application. The user must be authenticated and have permission to create tasks in the selected project.

### Path Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| project_id | String (UUID) | Yes | Identifies the project where the task will be created. |

### Query Parameters
No query parameters are required.

### Request Body Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| title | String | Yes | The task title, from 1 to 200 characters. |
| description | String | No | Additional task details, up to 5,000 characters. |
| assignee_id | String (UUID) | Yes | Identifies the user assigned to the task. |
| due_date | String (YYYY-MM-DD) | Yes | The task deadline. |
| priority | String | Yes | Task priority: low, medium, or high. |

### Required Headers

- `Authorization: Bearer YOUR_ACCESS_TOKEN`
- `Content-Type: application/json`

### Example Request Body

```json
{
  "title": "Prepare monthly project report",
  "description": "Collect project updates and prepare the report.",
  "assignee_id": "660e8400-e29b-41d4-a716-446655440001",
  "due_date": "2026-11-15",
  "priority": "high"
}
```

### Successful Response: 201 Created

```json
{
  "id": "770e8400-e29b-41d4-a716-446655440002",
  "project_id": "550e8400-e29b-41d4-a716-446655440000",
  "title": "Prepare monthly project report",
  "description": "Collect project updates and prepare the report.",
  "assignee_id": "660e8400-e29b-41d4-a716-446655440001",
  "due_date": "2026-11-15",
  "priority": "high",
  "status": "open",
  "created_at": "2026-10-29T09:20:00Z"
}
```

### HTTP Response Codes

| Code | Meaning |
|---|---|
| 201 | Task created successfully. |
| 400 | Request is malformed or invalid. |
| 401 | Authentication is missing or invalid. |
| 403 | User lacks permission to create tasks. |
| 404 | Project not found or not accessible. |
| 409 | Project state prevents task creation. |
| 415 | Unsupported request content type. |
| 422 | Request fields fail validation. |
| 429 | API rate limit exceeded. |
| 500 | Unexpected server error. |

### Example Error Response

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "The request contains invalid fields.",
    "details": [
      {
        "field": "priority",
        "message": "Priority must be low, medium, or high."
      }
    ]
  }
}
```
# Peer Critique

1. Are the instructions clear and easy to follow?
2. Does each procedure step describe one action and its expected result?
3. Are the screenshot description and troubleshooting note useful?
4. Are the API parameters and headers clearly documented?
5. Are the JSON examples correctly formatted?
6. Are the HTTP response codes explained clearly?

## Feedback
The document is well organized and uses clear headings and examples.
One improvement would be to test the instructions with a beginner to identify unclear steps.