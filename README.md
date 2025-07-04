# The Ideology Studies Hexagon

![The ideology studies hexagon](/hexagon.png)

## Key

CogSci original key from [here](https://www.researchgate.net/figure/The-Cognitive-Science-hexagon-in-1978-Vertices-represent-contributing-disciplines_fig1_295395918): 

> The “Cognitive Science hexagon” in 1978. Vertices represent contributing disciplines. Lines joining vertices represent the following interdisciplinary collaborations: 1 cybernetics; 2 neurolinguistics; 3 neuropsychology; 4 simulation of cognitive processes; 5 computational linguistics; 6 psycholinguistics; 7 philosophy of psychology; 8 philosophy of language; 9 anthropological linguistics; 10 cognitive anthropology; and 11 evolution of brain. Continuous lines represent consolidated collaborations; unnumbered dotted lines, in-progress ties between philosophy and computer science, neuroscience and anthropology as of 1978 (Adapted from the Sloan Report, pp. 3-ff)

Ideology studies revision: 1' historical materialism; 2' Michael Freeden's semiotic-inspired morphological concept-centred model; 3' political social psychology; 4' behavioural economics; 5' undefined ; 6 psychology of language; 7 philosophy of psychology; 8 philosophy of language; 9 anthropological linguistics; 10 cognitive anthropology; 11 political anthropology.  

## Description

A visual depiction of the connections between the different disciplines implicated in Ideology Studies, written in [TikZ](https://en.wikibooks.org/wiki/LaTeX/PGF/TikZ).

 Forked from the original Cognitive Sciences hexagon written by [Olivia Guest](https://oliviaguest.com), at [cogsci-hexagon](https://github.com/oliviaguest/cogsci-hexagon) which is based on the [Sloan Foundation report on the Cognitive Sciences, 1978](https://digitalcollections.library.cmu.edu/node/31966).

## Generating the pdf from the TeX file in Windows

I used the following stack. [VS Code](https://code.visualstudio.com/download) as IDE with the [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) extension. [MikTex](https://miktex.org/download) for a Windows TeX installtion - this also requires a Perl installation, so used [Strawberry Perl](https://strawberryperl.com/). Verify your paths and installs from the vscode terminal with

```powershell
pdflatex --version
perl --version
```

and refer to the LaTeX Workshop extension documentation to build the pdf from the TeX file via the IDE. Alternatively, from the vscode terminal in your working directory, run

```powershell
pdflatex -quiet .\main.tex
```

## Generating the png from the pdf in Windows

The quick and dirty solution is to open the pdf, either in the VS Code viewer, a browser or the TeXworks app you get with MikTeX

```powershell
texworks .\main.pdf
```

and then use a screencap utility like Windows Snip & Sketch (WIN+SHIFT+S) crop by hand and save as a png.

The programmatic version involves installing yet more applications, namely [ImageMagick](https://imagemagick.org/script/download.php) and [GhostScript](https://www.ghostscript.com/releases/gsdnld.html). Obviously you want to cut your cloth to measure, depending on how many more TikZ -> PNG operations you anticipate doing in the near future.

If you do decide to go down the ImageMagick + GhostScript for Win route, then the command you need to generate the png, with a non-transparent (the default), white background is

```powershell
magick -density 300  main.pdf -background white -flatten -alpha off hexagon.png
```

Be careful, unlike more common unix/linux commands, the order of the -options and files is semantically important with ImageMagick - at least with the latest version 7. That -density 300 option needs to be *in front* of the source pdf because it affects the resolution of how the image is scanned from the origin (the default is 75 DPI, which is horrible). But don't put any of the other options before the source file, otherwise you'll get errors. The [ImageMagick documentation](https://usage.imagemagick.org/basics/#why) explains (or tries to!) how this is all supposed to work. But it's pretty involved and, from experience, is byzantine enough to confuse most of the LLM chatbots out there (mind you the backwards-compatibility breaking changes in the IM CLI argument template can only confuse statistical machines trained on all the available input, if most of the corpus has the outdated info). Just be aware that this toolset is very powerful, but has a steep learning curve. So if you're in a hurry, you're better off going with the quick and dirty option above! :wink:
