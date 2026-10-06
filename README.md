# DevOps Starter

A simple Python calculator project used to practice **GitHub Actions and CI/CD workflows**.

## Project Structure

```text
devops-starter/
├── calculator.py
├── test_calculator.py
├── requirements.txt
├── README.md
└── .github/
    └── workflows/
        └── ci-security.yml
```

## Calculator

The project contains basic calculator functions such as:

* Addition
* Subtraction
* Multiplication
* Division
* Division-by-zero handling

## Running Tests Locally

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Run the unit tests:

```bash
pytest test_calculator.py
```

## GitHub Actions

This project uses **GitHub Actions** to automatically test the code and perform a security scan.

The workflow is located at:

```text
.github/workflows/ci-security.yml
```

The workflow:

1. Checks out the repository
2. Sets up Python 3.12
3. Installs the dependencies
4. Runs the unit tests with `pytest`
5. Runs a security scan with `Bandit`

### Workflow Triggers

The workflow runs when:

* Code is pushed to the repository
* A pull request is created or updated
* The workflow is manually started using `workflow_dispatch`

## Security Scanning

[Bandit](https://bandit.readthedocs.io/) is used to scan the Python code for common security issues.

The workflow skips Bandit's `B101` check because the unit tests intentionally use Python `assert` statements, which are required by the tests.

```yaml
bandit -r . --skip B101
```

## What I Learned

This project demonstrates the basics of:

* GitHub Actions workflows
* YAML workflow configuration
* Jobs and steps
* GitHub-hosted runners
* Reusable Actions such as `actions/checkout`
* Automated unit testing
* Security scanning
* Manual workflow execution
* Automatic CI triggers
* Debugging failed workflow runs
