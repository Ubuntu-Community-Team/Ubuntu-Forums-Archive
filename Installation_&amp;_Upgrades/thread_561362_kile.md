---
title: "kile"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by vcadavez on 2007-09-27
Hello!
I'm trying to use kile in UBUNTU!
However I have error!

PDFTeX] finished with exit status 1

[ViewPDF] The file /home/vc/aulas/morfologia/aulas/morfologia.pdf does not exist; did you compile the source file?

Somebody can help me?

thanks

---

### Post by AdotB on 2007-09-27
I f there is and error,  the pdf wont be created. If there might be a syntax error in your .tex document, look through the "Log & Messages" at the bottom and  click on the red error text to go to that error. 

example:
1 error, 0 warnings, 0 badboxes

---

### Post by vcadavez on 2007-09-27
Hello AdotB!
I have this erros!

what to do?!
[LaTeX] morfologia.tex => morfologia.dvi (latex)
[LaTeX] finished with exit status 1
/usr/share/texmf-tetex/tex/generic/babel/babel.sty:134:Package babel Error: Language definition file portugues.ldf not found. \ProcessOptions*
/usr/share/texmf-tetex/tex/generic/babel/babel.sty:142:Package babel Error: You haven't specified a language option. ...ry to proceed from here, type x to quit.}
/usr/share/texmf-tetex/tex/latex/pdfscreen/pdfscreen.sty:337: Option `pagebackref' has already been used,(hyperref) setting the option has no effect on input line 337. Option `pagebackref' has already been used,(hyperref) setting the option has no effect
/usr/share/texmf-tetex/tex/latex/pdfscreen/pdfscreen.sty:337: Option `backref' has already been used,(hyperref) setting the option has no effect on input line 337. Option `backref' has already been used,(hyperref) setting the option has no effect
/usr/share/texmf-tetex/tex/latex/pdfscreen/pdfscreen.sty:829:File `truncate.sty' not found. \newcounter
[LaTeX] 3 errors, 2 warnings, 0 badboxes

---

### Post by gaussian on 2007-09-27
> **vcadavez said:**
> Hello AdotB!
I have this erros!

what to do?!
[LaTeX] morfologia.tex => morfologia.dvi (latex)
[LaTeX] finished with exit status 1
/usr/share/texmf-tetex/tex/generic/babel/babel.sty:134:Package babel Error: Language definition file portugues.ldf not found. \ProcessOptions*
/usr/share/texmf-tetex/tex/generic/babel/babel.sty:142:Package babel Error: You haven't specified a language option. ...ry to proceed from here, type x to quit.}
/usr/share/texmf-tetex/tex/latex/pdfscreen/pdfscreen.sty:337: Option `pagebackref' has already been used,(hyperref) setting the option has no effect on input line 337. Option `pagebackref' has already been used,(hyperref) setting the option has no effect
/usr/share/texmf-tetex/tex/latex/pdfscreen/pdfscreen.sty:337: Option `backref' has already been used,(hyperref) setting the option has no effect on input line 337. Option `backref' has already been used,(hyperref) setting the option has no effect
/usr/share/texmf-tetex/tex/latex/pdfscreen/pdfscreen.sty:829:File `truncate.sty' not found. \newcounter
[LaTeX] 3 errors, 2 warnings, 0 badboxes


I don't use KILE (I have tried it, but like Emacs+Auctex better), but it looks like your problems are general Latex related. You seem to be missing language definition file for Portuguese  (portugues.ldf). You could try:

1) Search for it in Synaptic (something about TeX and language support). You need to know if you have TeXLive or TeTeX installed (TeXLive I guess is preferred nowadays).
2) As a quick and dirty fix try to google for the file and install it in the same directory as your source file.

Also truncate.sty file is missing. At least in my Mandriva desktop (I don't have access to my Ubuntu laptop now) it is part of TeTeX-installation. Are you sure you have installed all relevant packages for Latex?

---

### Post by vcadavez on 2007-09-27
I was looking for that missing packages and I have it!
so I dont understand why this error! problems on installation?

---

### Post by gaussian on 2007-09-28
> **vcadavez said:**
> I was looking for that missing packages and I have it!
so I dont understand why this error! problems on installation?

Not sure, but sounds it could be a problem with your TeTex installation. Or it could be something completely different.

One note: if you are a Feisty (or Gutsy) user, I think now TeXLive is the preferred LaTeX/TeX-distribution. You could try replacing TeTex with that.

---

### Post by AdotB on 2007-09-29
> Not sure, but sounds it could be a problem with your TeTex installation. Or it could be something completely different.

One note: if you are a Feisty (or Gutsy) user, I think now TeXLive is the preferred LaTeX/TeX-distribution. You could try replacing TeTex with that.

Changing your latex-distribution might be a good idea, but at least make sure the latex-distribution you are using is up to date.

If you have 'truncate.sty', try copying it into the same directory as you .tex file.
and i think hyperref is pdf only, so make sure your using PDFLaTeX, not LaTeX

---

