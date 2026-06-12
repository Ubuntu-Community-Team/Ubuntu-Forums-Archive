---
title: "xelatex can't load Tex Gyre Bonum"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by Iwiki on 2012-05-08
This is a sample document.  I am running Ubuntu 10.04 
\documentclass{article}
\usepackage{fontspec}
\setromanfont{TeX Gyre Bonum}
\begin{document}
Je suis un test!
\end{document}

> xelatex bonjour.tex

(/usr/share/texmf-texlive/tex/xelatex/fontspec/fontspec.cfg))kpathsea: Invalid fontname `TeX Gyre Bonum', contains ' '

! Font \zf@basefont="TeX Gyre Bonum" at 10.0pt not loadable: Metric (TFM) file or installed font not found.
\zf@fontspec ...ntname \zf@suffix " at \f@size pt \unless \ifzf@icu \zf@set@... l.3 \setromanfont{TeX Gyre Bonum}

I can make this compile by commenting out '\setromanfont{TeX Gyre Bonum}'  Why can't xelatex find TeX Gyre Bonum?

---

