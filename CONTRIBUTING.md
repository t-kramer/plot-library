# Contributing to the CBE Building Science Plot Library

Thank you for contributing to the Plot Library!  
This document describes how to add a new plot using GitHub and a Pull Request workflow.

The contribution process is intentionally lightweight:

> Add a `.qmd` file, an image (if needed), and a bibliography entry — then submit a Pull Request.

---

## Overview of the workflow

1. Create a new branch from `main`
2. Add your content:
   - a `.qmd` file for your plot
   - an image (if applicable)
   - a BibTeX entry in `references.bib`
3. Preview locally (optional but recommended)
4. Commit and push your branch
5. Open a Pull Request on GitHub

---

## Step 1: Create a new branch

From your local repo:

```bash
git checkout main
git pull
git checkout -b add-<short-plot-name>
```

Example:

```bash
git checkout -b add-tsv-vs-temp
```

---

## Step 2: Add your plot file

All plot pages live in:

```
pages/plots/
```

Create a new file:

```
pages/plots/my_plot_name.qmd
```

### Required front matter template

Copy and fill in this template at the top of your file:

```yaml
---
title: "Descriptive plot title"
description: "One-line summary shown in the Plot Library cards."
source: "@citationKey"
source-doi: "https://doi.org/..."
tags: "R, Python, Category"
suppress-bibliography: true
---
```

Then add the standard metadata block:

```markdown
::: {.callout-note appearance="minimal"}
**Source:** {{< meta source >}}  
**DOI:** [link]({{< meta source-doi >}})  
**Tags:** {{< meta tags >}}
:::
```

---

## Step 3: Add the plot itself

You have two options:

---

### Option A — Code-generated plot (recommended)

Include code from the repository:

```markdown
```{r}
#| include: src/plots/my_plot_script.R
#| fig-cap: "Caption describing the plot."
#| fig-alt: "Accessible description of the figure."
#| fig-classes: [preview-image]
#| code-fold: true
```
```

Or Python:

```markdown
```{python}
#| include: src/plots/my_plot_script.py
#| fig-cap: "Caption describing the plot."
#| fig-alt: "Accessible description of the figure."
#| fig-classes: [preview-image]
#| code-fold: true
```
```

This:

- runs the script,
- generates the figure,
- uses it as the Plot Library thumbnail,
- displays the code for transparency.

---

### Option B — Static image only

If you cannot include code, place the image next to the `.qmd` file:

```
pages/plots/my_plot_name.png
```

Then embed it:

```markdown
![](my_plot_name.png){.preview-image}
```

---

## Step 4: Add the BibTeX entry

All references are stored in:

```
references.bib
```

Add your citation in proper BibTeX format, for example:

```bibtex
@article{fanger1970,
  title = {Thermal comfort: Analysis and applications in environmental engineering},
  author = {Fanger, Povl Ole},
  year = {1970},
  publisher = {McGraw-Hill}
}
```

The citation key (`fanger1970`) must match the `source:` field in your plot page.

---

## Step 5: Preview locally (recommended)

Run:

```bash
quarto preview
```

Check:

- Does the plot render correctly?
- Does the thumbnail appear in the Plot Library?
- Are the citation and DOI showing as expected?

---

## Step 6: Commit and push

```bash
git add pages/plots/my_plot_name.qmd references.bib
git commit -m "Add plot: <short description>"
git push origin add-my-branch-name
```

---

## Step 7: Open a Pull Request

On GitHub:

1. Open a Pull Request to merge into `main`
2. Add a brief description:
   - What the plot shows
   - Any limitations or caveats
   - Whether the code is final or illustrative

---

## Style expectations

Before submitting, check:

- Title is descriptive and specific
- Description is concise
- Axes are labeled with units
- Caption explains what is shown
- Plot follows the lab's styling guidelines
- Source and DOI are provided where applicable

---

## What not to submit

Please avoid:

- screenshots of code
- unlabeled plots
- undocumented data sources
- hard-coded styling in multiple places
- duplicate plots without justification

---

## Questions?

If you are unsure:

- where your plot fits
- how to structure the page
- whether a contribution is appropriate

Open a GitHub issue or submit a draft Pull Request — feedback is welcome early.

---

## Thank you

The plot library grows through collaboration.  
Every contribution helps make results more consistent, reusable, and understandable.
