Openscoring-Python
==================

Python client library for the Openscoring REST web service.

# Prerequisites #

* Python 2.7, 3.4 or newer.

# Installation #

Installing a release version from PyPI:

```
pip install openscoring
```

Alternatively, installing the latest snapshot version from GitHub:

```
pip install --upgrade git+https://github.com/openscoring/openscoring-python.git
```

# Usage #

Creating an `Openscoring` object:
```python
from openscoring import Openscoring

os = Openscoring(base_url = "http://localhost:8080/openscoring")
```

Deploying a PMML document `DecisionTreeIris.pmml` as an `Iris` model:
```python
os.deployFile("Iris", "DecisionTreeIris.pmml")
```

Evaluating the `Iris` model with a data record:
```python
arguments = {
	"Sepal.Length" : 5.1,
	"Sepal.Width" : 3.5,
	"Petal.Length" : 1.4,
	"Petal.Width" : 0.2
}

results = os.evaluate("Iris", arguments)
print(results)
```

The same, but wrapping the data record into an `EvaluationRequest` object for request identification purposes:
```python
from openscoring import EvaluationRequest

evaluationRequest = EvaluationRequest("record-001", arguments)

evaluationResponse = os.evaluate("Iris", evaluationRequest)
print(evaluationResponse.results)
```

Evaluating the `Iris` model with data records from the `Iris.csv` CSV file, storing the results to the `Iris-results` CSV file:
```python
os.evaluateCsvFile("Iris", "Iris.csv", "Iris-results.csv")
```

Undeploying the `Iris` model:
```python
os.undeploy("Iris")
```

# De-installation #

Uninstall:
```
pip uninstall openscoring
```

# License #

Openscoring-Python is licensed under the terms and conditions of the [GNU Affero General Public License, Version 3.0](https://www.gnu.org/licenses/agpl-3.0.html).

# Additional information #

Openscoring-Python is developed and maintained by Openscoring Ltd, Estonia.

Interested in using [Java PMML API](https://github.com/jpmml) or [Openscoring REST API](https://github.com/openscoring) software in your company? Please contact [info@openscoring.io](mailto:info@openscoring.io)
