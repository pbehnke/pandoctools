# Best Python/Jupyter/PyCharm/VSCode/Atom experience + report generation with Pandoc filters

(*__backup of__ [__the reddit post__](https://www.reddit.com/r/datascience/comments/9pj8k9/best_pythonjupyterpycharm_experience_report/)*)

I'm going to share with you my favourite way of using Python and Jupyter for research and reports. And it's not simply using Jupyter. I want to write code in PyCharm and use Pandoc filters for reports.

* Write code in [PyCharm](https://www.jetbrains.com/pycharm/) - best python IDE with code [completion](https://www.jetbrains.com/help/pycharm/auto-completing-code.html), [inspection](https://www.jetbrains.com/help/pycharm/code-inspection.html), quick documentation pop ups (Ctrl+Q, Alt+MouseButton2), quick navigation to declaration (Mouse Button2),
* [Atom editor](https://atom.io/) + [hydrogen](https://atom.io/packages/hydrogen) + [MagicPython](https://atom.io/packages/MagicPython) for interactive code execution and instanty seeing plots, dataframes and more,
* Sync Atom with PyCharm via [file-watcher](https://atom.io/packages/file-watcher) (but first disable PyCharm safe write: Settings → Appearance and Behavior → System Settings → Synchronization → Use "safe write"),
* With this combo you also may need to [reload imported custom external modules in Hydrogen](https://github.com/kiwi0fruit/pandoctools/blob/master/docs/tips.md#reload-imported-modules-in-hydrogen),
* Write Unicode fast in Atom via [sugartex-completions](https://atom.io/packages/sugartex-completions),
* Export Hydrogen document to static Markdown document or Jupyter notebook or docx via [Pandoctools](https://github.com/kiwi0fruit/pandoctools) based on [Pandoc](https://pandoc.org/) (or export to PDF but this unfortunately needs tuning...),
* During export via Pandoctools use any pandoc or text filter like [pandoc-crossref](https://github.com/lierdakil/pandoc-crossref) (so you can have cross-references for equations, figures and tables), [SugarTeX](https://github.com/kiwi0fruit/sugartex) LaTeX transpiler or a custom filter via [panflute](https://github.com/sergiocorreia/panflute),
* Pandoctools stores [reusable profiles](https://github.com/kiwi0fruit/pandoctools/tree/master/pandoctools/cli) that define text conversion (written as cross-platform bash pipeline with CLI text filters),
* Preview static Markdown in Atom via [markdown-preview-plus](https://atom.io/packages/markdown-preview-plus),
* Run Pandoctools from Atom via cross-platform [unix-filter](https://atom.io/packages/unix-filter) ([setup pandoctools in unix filter](https://github.com/kiwi0fruit/pandoctools/blob/master/docs/atom.md#unix-filter)),
* ...
* more details about tuning [Atom packages](https://github.com/kiwi0fruit/pandoctools/blob/master/docs/atom.md) and [using Pandoctools](https://github.com/kiwi0fruit/pandoctools).

### Example

There is an [**example**](https://github.com/kiwi0fruit/pandoctools/blob/master/examples/notebook.py) (from [here](https://github.com/kiwi0fruit/pandoctools/tree/master/examples)) that can be edited in PyCharm, interactively run in Atom+Hydrogen and exported via Pandoctools.

### VS Code

Or you can use VS Code instead of PyCharm. Everything seems to work out of the box except you need to install `pylint` to **each** Python env you are going to use. If you would run Jupyter in Atom/Hydrogen then you can disable Jupyter functionality in VS Code: "**Data Sciense: Enabled**" (this would hide annoying "run cell" inserts). 

### Atom

Or you can do everything in Atom Editor. For this you need to install [ide-python](https://atom.io/packages/ide-python) (+ enable pylint there), install [python-tools](https://atom.io/packages/python-tools), install `python-language-server` to each working Python environment and tune `pylint` globally: edit or create `~/.pylintrc` file:

```ini
[MESSAGES CONTROL]
disable=bad-continuation,missing-docstring,pointless-string-statement,invalid-name,too-many-locals,too-many-arguments
[FORMAT]
max-line-length=119
```
Create it on Windows:

```bat
cd /d %UserProfile%
echo bla > .pylintrc
```
