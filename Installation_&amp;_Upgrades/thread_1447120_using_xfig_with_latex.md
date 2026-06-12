---
title: "using xfig with latex"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by madeel on 2010-04-04
I want to use xfig to include graphics in latex file.

I export the file as 'combined ps/latex (both parts)'

It created three files: 

myfile.fig 
myfile.pstex
myfile.pstex_t

And then I compile the following latex code:

\documentclass{article}
\usepackage[dvips]{graphicx}
\usepackage{color}
\usepackage{psfig}
\begin{document}
\input{myfile.pstex_t}
\end{document} 

The problem is that it is not including the figure drawn, only labeling. myfile.pstex_t has the reference to the graphic file. Please help!

---

