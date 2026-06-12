---
title: "LaTeX font map and pdf inclusion"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by jpprost on 2008-05-27
Hi,

I'm faced with a puzzling LaTeX failure caused by pdfpages. Can't think of new ideas for fixing it, so maybe you'll have suggestions. I suspect it comes from my installation. Here's the message I get:

<use myfile.pdf, page 1> [1 <./myfile.pdf{/var/lib/texmf/
fonts/map/pdftex/updmap/pdftex.map}
Error: pdflatex: pdf inclusion: invalid reference
==> Fatal error occurred, the output PDF file is not finished!
[PDFLaTeX] finished with exit status 255


What triggers the problem is the following call:

\includepdf[pages=-]{myfile.pdf}


The problem most likely comes from something that went wrong in my installation, since I was used to successfully use \includepdf quite commonly, but the command just does not succeed at all anymore. Not even on different other projects which used to compile just fine. And of course, I can't see what went wrong...

Among other attempted fixes, here are a few things I've done:
(i) dummy file with just an \includepdf and of course \usepackage{pdfpages}
(ii) all sorts of pdf files in the \includepdf
(iii) refreshing font maps, with the following commands:

> sudo texhash
> sudo update-updmap
> sudo updmap

(iv) re-installing LaTeX and fonts pkgs (using APT's 're-install' option: I'd like to avoid removing and re-installing everything from scratch)
(v) system upgrade

A few config details, fyi:
- Ubuntu Feisty (7.04)
- TeXLive 2005.dfsg.3-1 (plus various extras)
- texlive-pdfetex 2005.dfsg.2-12ubuntu1
- Kile 1:1.9.3-1ubuntu1

Any suggestions welcome...

Cheers,
JP

---

### Post by jlenain on 2008-08-11
Hello,

Could you tell us what command you are using to compile your LaTeX file ?

If you use ```
latex
```, then you're problem is normal since latex can only handle PostScript (ps) and Encapsuled PostScript (eps) files, and cannot include PDF files.
You should use the ```
pdflatex
``` command in order to use the pdfpages package. But in this case, all your figures should NOT be in PS or EPS, but rather in PNG, JPG or PDF formats. But maybe you already know that...

Cheers
JP

---

### Post by hugmenot on 2008-08-12
How about leaving out [pages=-] to test?

---

### Post by jlenain on 2008-08-13
OK, sorry, jpprost seems to use pdflatex, and not latex to compile.
In that case, I have no idea.
Leaving the option out [pages=-] would just insert 1 page of the PDF file, instead of all the pages, but it won't fix the problem at the compilation of the document.

Cheers

---

