---
title: "texlive needs updating badly - expl3 and related package issues"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by SmithWillSuffice on 2012-02-02
Could the maintainers of texlive help please?  I'm trying to use the package mdframed, but it loads xparse and this seems broken.  The error shows up after loading l3file.sty or l3num.sty, but seems to trace back to xparse.sty as far as I can tell, but the root cause may go deeper.

The bug is similar to the one reported here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568321]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568321")

I haven't found a fix for this, and anything i did would be a total kludge.

Also, mdframed was not in the ubuntu repos, so had to be installed manually from CTAN source.  So I suspect this package, or it's RequiredPackages, is incompatible with the older version of texlive distributed with ubuntu.  I am currently testing a fresh install of texlive from TUG to see if this will resolve the errors I am encountering.  If it doesn't then I guess it isn't a ubuntu package maintenance issue but something bad with texlive that hasn't been reported or fixed correctly.

The only other similar info I can provide is this report here:
[http://permalink.gmane.org/gmane.comp.tex.latex.latex3/1974]("http://permalink.gmane.org/gmane.comp.tex.latex.latex3/1974")

---

### Post by SmithWillSuffice on 2012-02-03
Solved.

Yep, upgrading to 
```
pdfTeX 3.1415926-2.3-1.40.12 (TeX Live 2011)
kpathsea version 6.0.1

```
did the trick.  The Ubuntu package (which in 11.10 is TeX Live 2009) should be upgraded asap IMHO.

The manual install of texlive is easy with a fast internet connection, but did require setting a few environment variables manually, TEXDIR and TEXMFLOCAL, and adding TEXDIR to my PATH.

---

