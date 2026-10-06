# Ensemble Methods

A hands-on look at ensemble learning in Python. You combine several models through voting, averaging, and stacking, train and tune an XGBoost classifier, compare classification algorithms on a real census dataset, and finish by building the AdaBoost algorithm from scratch.

## Learning Objectives

By the end of this repository, you should be able to:

- Build voting and averaging ensembles that combine several base classifiers.
- Implement a stacking classifier, both with scikit-learn and from its component steps.
- Train an XGBoost classifier and tune its hyperparameters.
- Compare multiple classification algorithms on a real dataset and select the strongest.
- Apply preprocessing steps (log transforms, one-hot encoding, scaling) before modelling.
- Implement the AdaBoost algorithm from scratch.

## Learning Path

Work through the notebooks in order.

| File / Folder | Description |
|---|---|
| [**1 - Combining Models**](1_voting_ensemble_methods.ipynb) | Combine classifiers with max voting, soft voting, averaging, weighted averaging, and stacking. |
| [**2 - XGBoost**](2_applying_xgboost.ipynb) | Prepare data, train an XGBoost classifier, and make predictions on the diabetes dataset. macOS users: see the [OpenMP caution](#6-open-the-notebooks) in Setup first. |
| [**3 - Classification Comparison**](3_comparison_classification_algorithms_exercise.ipynb) | Exercise: preprocess the census data, compare several classifiers, and tune the best one. |
| [**4 - AdaBoost from Scratch (Optional)**](4_optional_adaboost_python.ipynb) | Build the AdaBoost algorithm step by step in pure Python. |

### Additional Folders and Files

| File / Folder | Description |
|---|---|
| [**Data**](data.zip) | The datasets, bundled as a zip (unzip it during setup). |
| [**Solutions**](solutions/) | Reference solutions. |
| [**Visualisation Helpers**](visuals_script.py) | Plotting helpers used across the notebooks. |
| [**pyproject.toml**](pyproject.toml) | Project configuration and dependencies. |
| [**uv.lock**](uv.lock) | Dependency lock file. |

## Setup

> [!NOTE]
> Throughout these steps, text in angle brackets like `<repo-name>` is a **placeholder**. Replace it including the `< >` brackets with your own value. For example, `cd <repo-name>` becomes `cd ds-ensemble-methods`.

### 1. Create the Repository from the Template

Click **Use this template** on GitHub.

When creating the repository:

- Set yourself as the **Owner**
- Choose a repository name
- Disable **Include all branches**
- Click **Create repository**

> [!IMPORTANT]
> If you are working in pairs or groups, only **one person** should complete this step.

---

### 2. Add Collaborators (Pairs/Groups Only)

If working with teammates:

1. Open the repository on GitHub
2. Go to **Settings → Collaborators**
3. Add your teammates as collaborators
4. Share the repository link with your team

Teammates should accept the invitation before continuing.

---

### 3. Clone the Repository

Copy the SSH URL from the **Code** button on GitHub, then run:

```bash
git clone <copied-ssh-url>
```

The copied SSH URL will look like `git@github.com:<your-username>/<repo-name>.git`.

---

### 4. Move into the Project Folder and Install Dependencies

This installs all dependencies and creates a virtual environment in (`.venv/`).

```bash
cd <repo-name>
uv sync
```

---

### 5. Unzip the Data

The datasets are bundled in `data.zip`. Extract them into a `data/` folder before running the notebooks. This command uses the environment from `uv sync`:

```bash
uv run python -c "import zipfile; zipfile.ZipFile('data.zip').extractall()"
```

---

### 6. Open the Notebooks

> [!NOTE]
> Make sure you open VS Code from the project root so it automatically detects the environment created by `uv sync`.

Launch VS Code in the project root folder:

```bash
code .
```

Then open a notebook and select the Python environment created by `uv sync` as the kernel.

> [!CAUTION]
> macOS only: `uv sync` installs XGBoost but not the system OpenMP runtime it links against. If [notebook 2](2_applying_xgboost.ipynb) reports that `libxgboost.dylib` could not be loaded, install it once with `brew install libomp`. The Linux and Windows wheels bundle OpenMP, so no extra step is needed there. See the [XGBoost installation docs](https://xgboost.readthedocs.io/en/stable/install.html) for the official note.

## References & Further Reading

- [**Scikit-learn: Ensemble Methods**](https://scikit-learn.org/stable/modules/ensemble.html): User guide covering voting, stacking, boosting, and bagging.
- [**Scikit-learn: StackingClassifier**](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.StackingClassifier.html): API reference for the stacking estimator used in notebook 1.
- [**XGBoost Documentation**](https://xgboost.readthedocs.io/en/stable/): Official documentation for the gradient-boosting library.
- [**The Random Forest Algorithm (MLU-Explain)**](https://mlu-explain.github.io/random-forest/): A visual, intuitive explanation of why combining many models works.


