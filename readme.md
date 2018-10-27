# How to install

There is no special installation required. Once you have LaTeX (on Windows: we recommend MiKTeX) installed, simply run 'build.bat' and your output will be created.

_Note_: you should never have to change any files outside the `content` subfolder (except figures and appendixes in the corresponding subfolders). All files related to your work should reside inside this folder.

# How to set up

All setup is done in `content\config.tex`. This file includes configuration considering meta data of your work as well as several toggles that allow you to change the behaviour of the template. All settings are explained therein using inline comments.

# How to use

Following we will provide a short explanation of several concepts implemented in this template.

## Main body text

Your main body text resides in `content\mainbody.tex`. Of course you can split your work into multiple files. Let's say you have the following content:

```
content
|- mainbody.tex
|- 0_intro.tex
|- 1_chapter.tex
```

If you wish to include your chapters in the correct order, your `mainbody.tex` would look as follows:

```
\documentclass[document.tex]{subfiles}
\begin{document}
\subfile{content/0_intro.tex}
\subfile{content/1_chapter.tex}
\end{document}
```

Please note, that your individual chapter files need to use the same documentclass declaration that is already present in `mainbody.tex`.

## Abbreviations

Abbreviations will automatically be formatted, where the first occurance spells out the full term with the abbreviation in paranthesis and all subsequent uses will only display the abbreviation. An index of all abbreviations used is also created, if abbrevitions are defined in `content\abbreviations.tex`. Please see the example provided. Please also note that only abbreviations used at least once are considered in the index. To use an abbreviation in the text, the command is `\abbreviation{term}`.

## Figures

All figures have to reside in `\figures` or subfolders. There are two commands for including figures. To use a normal inclusion, which also appears in the index, use

`\customfigure{file name in /figures}{description}{width in factor of page width}{label}`

If you wish to include a figure without including it in the index and without displaying a label, use

`\nolabelfigure{file name in /figures}{width in factor of page width}`

## Citation

Biber is used as the citation tool of choice, and APA style is already present in the current setup. The easiest way to use citations is `\autocite{reference}`, which will use author-date-style citations. If you wish to use footnote citations or otherwise change citation behaviour, please read up on the `cite` and `biblatex` packages for latex. Your bibliography must follow Biber format and be present in `references.bib`. Please also see the example provided.