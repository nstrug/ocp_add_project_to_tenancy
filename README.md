# ocp_add_project_to_tenancy

## Description:

This role adds a list of projects to an existing tenancy.

## Behaviour:

**Feature:** Add projects to a tenancy

As a PaaS Operator
I want to add a list of projects to an existing tenancy
so that developers can work on a set of related projects

- **Scenario:** A customer requests new projects
- **Given:** there is a valid service account token
- **Given:** there is an existing tenancy
- **Given:** there is a list of projects to create
- **When:** the role is executed
- **Then:** the requested projects are created
- **Then:** the projects are labelled as belonging to the tenancy
 
## Configuration:

A list of the external variables used by the role.

| Variable  | Description  | Example  | Default |
|---|---|---|---|
| **tenancy**  | The name of the tenancy |  mytenancy | (none) |
| **projects**  | List of projects to create | proj1,proj2,proj3  |  (none) |
| **ocp_token**  | Token for a serviceaccount with permission to create projects | (none)  |
| **ocp_uri**  | URI for the cluster API | https://localhost:8443/  |

## Testing and Usage:

The role can be tested using a simple playbook as follows:

```
---
- hosts: masters[0]
  name: Testing ocp_add_project_to_tenancy
  roles:
    - ocp_add_project_to_tenancy
  vars:
    - tenancy: existingtenancy
    - projects:
      - alpha
      - beta
      - gamma
      - delta
    - ocp_token: eyJhbGci...

```
