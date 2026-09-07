# 🧬 PyRNA-Lab

### AI-Powered RNA Secondary Structure Prediction Toolkit

**PyRNA-Lab** is an open-source Python toolkit for RNA sequence analysis and AI-assisted RNA secondary structure prediction.

It combines **Python, PyTorch, computational biology, and an interactive Pygame interface** into a simple research and educational environment for experimenting with RNA sequences.

---

## ✨ Features

* 🧬 RNA sequence input and analysis
* 🤖 AI-powered RNA secondary structure prediction
* 🧠 PyTorch neural-network model
* 🔗 RNA base-pair prediction
* 📐 Secondary structure representation
* 📊 Sequence length statistics
* 🔬 Selected base-pair scores
* 🖥️ Interactive graphical interface
* 🌙 Dark / Light theme
* 📋 Copyable model output
* 🖱️ Text selection with mouse
* ⌨️ Keyboard shortcuts
* 📜 Scrollable sequence and output areas
* 📦 Python package available through PyPI
* ⚡ `pyrna` command-line launcher
* 🔓 Open-source project

---

# 🚀 Installation

PyRNA-Lab can be installed directly from PyPI.

### Requirements

* Python `3.10` or newer
* PyTorch
* NumPy
* Pandas

Install the package:

```bash
pip install pyrna-lab
```

For AI dependencies:

```bash
pip install pyrna-lab[ai]
```

---

# 🖥️ Launching PyRNA-Lab

After installation, simply run:

```bash
pyrna
```

The PyRNA-Lab graphical interface will open automatically.

You do not need to navigate into the project directory or manually execute `app.py`.

---

# 🧬 Using PyRNA-Lab

## 1. Enter an RNA sequence

When the application starts, the RNA input area is displayed on the left side.

You can:

* Type an RNA sequence manually
* Paste a sequence from the clipboard
* Select text with the mouse
* Move through the sequence with the keyboard
* Delete characters
* Select all text
* Copy selected text
* Cut selected text
* Scroll horizontally and vertically

The input field does **not automatically modify your text**.

PyRNA-Lab does not automatically:

* Convert lowercase to uppercase
* Remove spaces
* Remove new lines
* Filter characters
* Truncate the input

The original user input remains unchanged.

---

# 🧪 Supported RNA Bases

The current AI prediction model accepts the standard RNA bases:

```text
A
C
G
U
```

Examples:

```text
GGGAAAUCCCGGAUUU
```

```text
AUGCUAGCUAGCUA
```

```text
GGCAUCGGAUCC
```

If an unsupported character is present, PyRNA-Lab reports an error instead of silently modifying the sequence.

For example:

```text
Invalid RNA base: X
```

---

# 🤖 Running an AI Prediction

After entering an RNA sequence, click:

```text
Predict Structure
```

PyRNA-Lab then:

1. Reads the provided RNA sequence.
2. Encodes RNA bases numerically.
3. Sends the encoded sequence to the PyTorch model.
4. Evaluates potential nucleotide pairs.
5. Applies valid RNA pairing rules.
6. Builds a secondary structure representation.
7. Displays the predicted structure.
8. Displays selected base pairs and their scores.
9. Generates a complete copyable output.

---

# 🔗 RNA Base-Pair Rules

PyRNA-Lab currently considers the following base pairs:

```text
A - U
U - A

C - G
G - C

G - U
U - G
```

These correspond to standard Watson-Crick pairings plus the GU wobble pairing used by the current prediction workflow.

---

# 🧠 AI Model

PyRNA-Lab loads its trained neural-network model from:

```text
rna_pair_model.pth
```

The model is loaded automatically when the application starts.

The interface displays the model status:

```text
● AI READY
```

when the model loads successfully.

If the model cannot be loaded, the interface displays:

```text
● MODEL ERROR
```

and prediction is disabled.

---

# 📏 Current Model Limitation

The current trained model supports a maximum of:

```text
128 bases
```

This is a **model limitation**, not an input-field limitation.

The application itself does not restrict the amount of text that can be entered.

However, if the sequence is longer than 128 bases, PyRNA-Lab will not run the prediction and will display:

```text
The current AI model supports up to 128 bases
```

---

# 📐 Predicted Structure

After a successful prediction, PyRNA-Lab displays the generated RNA secondary structure in the:

```text
PREDICTED STRUCTURE
```

panel.

The structure uses bracket notation such as:

```text
((...))
```

and may contain additional bracket types depending on the generated structure.

The interface visually distinguishes structural brackets and unpaired positions.

---

# 📊 Prediction Statistics

After prediction, the application displays three statistics.

### RNA Length

Shows the number of bases in the input sequence.

Example:

```text
RNA LENGTH
16
```

### Base Pairs

Shows the number of selected base pairs identified by the prediction workflow.

Example:

```text
BASE PAIRS
5
```

### Model

Displays:

```text
AI RNA
```

to indicate that the RNA AI model is being used.

---

# 📋 Model Output

The right side of the interface contains a complete model-output area.

After prediction, it contains:

```text
RNA SEQUENCE
============

[RNA sequence]


PREDICTED STRUCTURE
===================

[Predicted structure]


SELECTED BASE PAIRS
===================

Position     Score
------------------------
  1 -  16      0.842
  2 -  15      0.731
```

The exact results depend on the input sequence and model prediction.

---

# 🔗 Selected Base Pairs

Each selected pair contains:

* First nucleotide position
* Second nucleotide position
* Model score

For example:

```text
Position     Score
------------------------
  1 -  16      0.842
  2 -  15      0.731
```

Positions are displayed using **1-based indexing**, meaning the first nucleotide is position `1`.

---

# 📋 Copying Results

The model output is read-only.

You cannot modify the generated model output.

However, you can select and copy it.

### Mouse

Drag across the output text to select it.

### Select everything

Press:

```text
Ctrl + A
```

### Copy

Press:

```text
Ctrl + C
```

The selected output can then be pasted into another application.

---

# ⌨️ Keyboard Shortcuts

## RNA Input

| Shortcut       | Action                    |
| -------------- | ------------------------- |
| `Ctrl + A`     | Select all input          |
| `Ctrl + C`     | Copy selected input       |
| `Ctrl + X`     | Cut selected input        |
| `Ctrl + V`     | Paste                     |
| `Ctrl + Enter` | Run prediction            |
| `Escape`       | Clear input and results   |
| `Left Arrow`   | Move cursor left          |
| `Right Arrow`  | Move cursor right         |
| `Home`         | Move to beginning         |
| `End`          | Move to end               |
| `Up / Down`    | Scroll                    |
| `Page Up`      | Scroll up                 |
| `Page Down`    | Scroll down               |
| `Backspace`    | Delete previous character |
| `Delete`       | Delete next character     |

---

## Model Output

| Shortcut    | Action               |
| ----------- | -------------------- |
| `Ctrl + A`  | Select all output    |
| `Ctrl + C`  | Copy selected output |
| Mouse drag  | Select output        |
| Mouse wheel | Scroll output        |

The output area does not allow typing, pasting, cutting, deleting, or modifying the model-generated result.

---

# 🧹 Clearing the Workspace

Click:

```text
Clear
```

or press:

```text
Escape
```

while working inside the RNA input.

This resets:

* RNA sequence
* Prediction output
* Predicted structure
* Base-pair count
* RNA length
* Previous sequence
* Scroll position
* Status message

The application returns to:

```text
Ready
```

---

# 🌙 Dark and Light Themes

PyRNA-Lab includes two visual themes.

### Dark

The default theme provides a dark interface with a gold visual accent.

### Light

Click the theme button in the upper-right corner to switch to the light interface.

The button changes between:

```text
● Bright
```

and:

```text
● Dark
```

depending on the current theme.

The theme can be switched at any time.

---

# 🖱️ Scrolling

Scrollable areas are available for longer content.

### RNA Input

The sequence editor supports:

* Vertical scrolling
* Horizontal scrolling
* Mouse wheel
* Shift + mouse wheel

### Model Output

The output area supports:

* Vertical scrolling
* Horizontal scrolling
* Mouse wheel
* Shift + mouse wheel

This allows longer sequences and prediction outputs to be inspected without modifying the generated data.

---

# 🔬 Example Workflow

A typical workflow is:

```text
1. Launch PyRNA-Lab
        │
        ▼
2. Enter RNA sequence
        │
        ▼
3. Click "Predict Structure"
        │
        ▼
4. Sequence encoding
        │
        ▼
5. PyTorch AI model
        │
        ▼
6. Base-pair evaluation
        │
        ▼
7. Structure generation
        │
        ▼
8. View predicted structure
        │
        ▼
9. Inspect base pairs & scores
        │
        ▼
10. Copy results if needed
```

---

# 🧪 Example

Start PyRNA-Lab:

```bash
pyrna
```

Enter:

```text
GGGAAAUCCCGGAUUU
```

Then click:

```text
Predict Structure
```

PyRNA-Lab will process the sequence and display:

* RNA length
* Selected base pairs
* Pair scores
* Predicted secondary structure
* Complete copyable output

---

# 🐍 Python Package Usage

PyRNA-Lab can also be imported as a Python package.

```python
import pyrna_lab as rna

print(rna)
```

The package can therefore be used as part of a Python environment in addition to its graphical application.

---

# 💻 Running from Source

Clone the repository:

```bash
git clone https://github.com/paknahad91/PyRNA-Lab.git
```

Enter the project:

```bash
cd PyRNA-Lab
```

Install it in editable mode:

```bash
pip install -e .
```

Launch the application:

```bash
pyrna
```

---

# 📁 Project Structure

```text
PyRNA-Lab/
│
├── rna_lab/
│   ├── app.py
│   ├── pair_model.py
│   ├── structure.py
│   │
│   ├── rna_model.pth
│   ├── rna_pair_model.pth
│   └── baseline_paired_unpaired.pth
│
├── README.md
├── pyproject.toml
└── ...
```

---

# 🛠️ Technology Stack

| Technology | Role                          |
| ---------- | ----------------------------- |
| Python     | Core programming language     |
| PyTorch    | AI / neural-network inference |
| Pygame     | Graphical user interface      |
| NumPy      | Scientific computing          |
| Pandas     | Data processing               |
| PyPI       | Python package distribution   |

---

# 🧬 Architecture Overview

```text
                 PyRNA-Lab
                     │
          ┌──────────┴──────────┐
          │                     │
    Graphical UI           Python Package
          │                     │
       Pygame              pyrna_lab
          │
          ▼
    RNA Sequence
          │
          ▼
    Sequence Encoding
          │
          ▼
     PyTorch Model
          │
          ▼
    Pair Evaluation
          │
          ▼
   Structure Generation
          │
       ┌──┴───┐
       ▼      ▼
 Structure   Base Pairs
       │      │
       └──┬───┘
          ▼
      Model Output
```

---

# ⚠️ Error Messages

## `Please enter an RNA sequence`

The input field is empty.

Enter an RNA sequence before running prediction.

---

## `Invalid RNA base: X`

The sequence contains a character that the current model does not support.

Use:

```text
A
C
G
U
```

---

## `The current AI model supports up to 128 bases`

The sequence contains more than 128 positions.

Shorten the sequence or use a future model version that supports longer sequences.

---

## `AI model is not ready`

The trained model could not be loaded.

Check that the model file is included correctly in the installation.

---

## `Prediction failed`

An unexpected error occurred while running the prediction pipeline.

Check the terminal output for additional technical information.

---

# 🔐 Input & Output Behavior

PyRNA-Lab intentionally keeps the user's input unchanged.

The application does not silently:

* Uppercase the sequence
* Remove spaces
* Remove line breaks
* Filter characters
* Modify the original sequence

Validation occurs when prediction is requested.

The generated model output is read-only and can only be selected and copied.

---

# 🎯 Project Vision

PyRNA-Lab aims to provide an accessible computational environment for experimentation with:

* RNA sequence analysis
* RNA secondary structure prediction
* Machine learning
* Deep learning
* Computational biology
* Scientific programming
* AI-assisted biological research

The project is designed to make experimentation with RNA and AI approachable for students, developers, researchers, and computational biology enthusiasts.

---

# 🔬 Research Direction

Future research and development may explore:

* Improved RNA structure prediction
* Larger training datasets
* More advanced neural architectures
* Model benchmarking
* Better sequence representations
* Uncertainty estimation
* Explainable AI
* Longer sequence support
* Additional RNA analysis tools

These are research directions and should not be interpreted as features currently implemented in version `1.0.0`.

---

# 📌 Project Status

**Version:** `1.0.0`

**Development Status:** Alpha / Research Project

PyRNA-Lab is an evolving research-oriented project. APIs, models, and internal implementation details may change in future releases.

---

# 📦 Package Information

**Package name:**

```text
pyrna-lab
```

**Python import:**

```python
import pyrna_lab
```

**Command-line launcher:**

```bash
pyrna
```

---

# 🌐 Links

### GitHub

https://github.com/paknahad91/PyRNA-Lab

### PyPI

https://pypi.org/project/pyrna-lab/

---

# 👨‍💻 Author

**Mohammad Paknahad**

PyRNA-Lab is an independent project focused on combining:

> **Python + AI + RNA + Computational Biology**

---

# 📄 License

PyRNA-Lab is released under the **MIT License**.

---

# ⭐ Support PyRNA-Lab

If you find PyRNA-Lab useful:

* ⭐ Star the GitHub repository
* 🐛 Report bugs
* 💡 Suggest improvements
* 🔬 Experiment with the toolkit
* 🧬 Use it for educational and research purposes

---

<div align="center">

## 🧬 PyRNA-Lab

### Python • AI • RNA • Computational Biology

**Built with Python. Powered by PyTorch.**

**Version 1.0.0**
Mohammad Paknahad 2026 (c)
</div>
