---
title: "smallest latex installation"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by MichaelBurns on 2010-03-02
How do I get the absolute smallest latex installation?  Right now, I try texlive-latex-base, but it installs to over 100MB already, and a good portion of that seems to be just for documentation.  At the very least, does anyone know how to install latex without the documentation?

---

### Post by MichaelBurns on 2010-03-21
bump

---

### Post by MichaelBurns on 2010-06-28
bump

---

### Post by kalwisti on 2010-06-28
As far as I know, it is not possible to omit that documentation because it is part of the base install of TeX Live (TL). One of the top level directories of TL is called *texmf*; one of *texmf*'s subdirectories is TEXMFMAIN, which holds configuration files, helper scripts and program documentation. 

For an overview, you might have a look here:

[http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-100002.2](http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-100002.2)
Berry, Karl, ed. "*The TeX Live Guide: TeX Live 2010*."
(See Sections 2.2 and 2.3)

Lucid Lynx has TL 2009 in its repositories. I checked just now and noticed that *texlive* (2009-7) [ca. 215 MB], which is described as being "a decent selection of the TeX Live packages," will pull in *texlive-doc-base* (1 MB), *texlive-latex-base-doc* (41 MB), *texlive-latex-recommended-doc* (15 MB), *texlive-fonts-recommended-doc* (2 MB) and *texlive-pstricks-doc* (58 MB). I don't believe they can be excluded from the download. 

If space is really tight on your hard drive, once you have installed TL, I imagine it could be possible to navigate into the *texmf* tree and delete the documentation. Most of it appears to be stored in

/usr/share/texmf/doc  and
/usr/share/texmf-texlive/doc

However, I do **not** recommend this, as it's potentially risky to alter the standard TL directory structure unless you know what you're doing. You should check with a TeXpert before trying something like that. 

I'm sorry if this isn't the answer you wanted to hear ... TeX is an amazing tool, but is a complex -- and large -- set of programs. (The full install of TeX Live is ca. 1 GB in size). TeXperts are usually meticulous about creating documentation; I think there is an assumption that they expect TeX users to RTFM when in doubt.   

If someone else knows a trick for omitting the basic documentation, I hope that they will chime in.

---

