# SIIwD
Seeking Interactive Insights with Data

## Working Area

Creating a Quarto workspace in VS Code primarily involves opening a folder where your Quarto projects and files reside. VS Code automatically treats the opened folder as a workspace.

Here's how to effectively set up and manage a Quarto workspace in VS Code:

- **Open a Folder:**
    
    - Launch VS Code.
    - Go to `File > Open Folder...` (or `Cmd+Shift+P` on macOS and search for "Open Folder").
    - Navigate to and select the parent directory of your Quarto project (e.g., the folder containing your `.qmd` files, or the root of a Quarto website or book project).
    - Alternatively, open your terminal, navigate to the desired project directory, and type `code .` to open the current folder in VS Code.
    
- **VS Code Workspace Recognition:**
    
    - Once you open a folder, VS Code automatically recognizes it as a workspace. It will remember your open files, editor layout, and other workspace-specific configurations.
    
- **Install the Quarto VS Code Extension:**
    
    - If you haven't already, install the official Quarto extension from the VS Code Marketplace. This extension provides features like:
        - Syntax highlighting for `.qmd` files.
        - Commands for rendering and previewing Quarto documents.
        - Visual editor support.
        - Integration with Quarto's features like citations and cross-references.
    
- **Configure Virtual Environments (if applicable):**
    
    - If you are using Python with Quarto and managing dependencies with virtual environments (like `venv` or `conda`), ensure VS Code is configured to use the correct interpreter.
    - VS Code should automatically detect `venv` environments within the workspace.
    - For `conda` environments, you may need to explicitly select the interpreter using the `Python: Select Interpreter` command in VS Code's Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P`).
    - If Quarto itself is installed within a `conda` environment, launch VS Code from a terminal where that `conda` environment is activated for VS Code to detect the Quarto installation. 
    

By following these steps, you establish a functional Quarto workspace in VS Code, enabling efficient authoring and rendering of your Quarto projects.


### 🖥️ Step 3: Register Environment with VS Code

#### Option A: Use Python Extension (Recommended)

1. Open **VS Code**.
    
2. Press `Ctrl+Shift+P` → choose `Python: Select Interpreter`.
    
3. Select the interpreter path for `my_new_env`. If it doesn’t show up:
    
    - Use “Enter interpreter path” → Browse to:
        
        ```
        <conda_root>/envs/my_new_env/bin/python   # macOS/Linux
        <conda_root>\envs\my_new_env\python.exe   # Windows
        ```
        

#### Option B: Set Workspace `.vscode/settings.json`

Inside your workspace folder, open or create `.vscode/settings.json`, and add:

json

```
{
  "python.pythonPath": "/path/to/conda/envs/my_new_env/bin/python"
}
```

This ensures VS Code remembers the interpreter for this workspace.

### ✅ Bonus: Make It Stick

- Keep the `.vscode` folder in your Git or project directory so that others (or future-you) get the same environment.
    
- You can use `conda env export > environment.yml` to save the full spec, and rehydrate it elsewhere with:
    
    bash
    
    ```
    conda env create -f environment.yml
    ```
    

### Notes.
```bash
conda create --name my_siiwd --clone mygeocompy
conda activate my_siiwd
(my_siiwd) (my_siiwd) PS Q:\__coding_scientometrics__\_2025_\siiwd> python -m ipykernel install --user --name siiwd --display-name "Python (siiwd)"
Installed kernelspec siiwd in C:\Users\Hante\AppData\Roaming\jupyter\kernels\siiwd
```


### _quarto.yml
```yml
book:
  chapters:
    - 00-errata.qmd

  appendices:
    - 31-datasets.qmd
    - 41-LLMs_UIs.qmd
    - 43-WebUI_essentials.qmd
    - 45-_essentials.qmd
    - 47-Gradio_essentials.qmd
    - 61-deploy.qmd
    - 63-Github_essentials.qmd
    - 65-Huggingface_essentials.qmd
    - 81-python_essentials.qmd
    - 83-Pydantic_essentials.qmd
    - 85-Pandas_essentials.qmd
    - 87-Panel_essentials.qmd
    - 99-references.qmd

bibliography: references.bib

format:
  pdf:
    documentclass: krantz
    include-in-header: latex/preamble.tex
    include-before-body: latex/before_body.tex
    include-after-body: latex/after_body.tex
    keep-tex: true
    callout-appearance: simple
```
