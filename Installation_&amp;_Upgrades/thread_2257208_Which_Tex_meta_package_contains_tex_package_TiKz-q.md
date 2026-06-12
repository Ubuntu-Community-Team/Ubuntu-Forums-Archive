---
title: "Which Tex meta package contains tex package TiKz-qtree?"
date: 2014-12-17
forum: Installation &amp; Upgrades
---

### Post by ken18 on 2014-12-17
I'm currently using Ubuntu 12.04 and have less than texlive-full installed.  I want to use tikz-qtree but can't for the life of me figure out what meta package to install.  In my searches it appears that texlive-pictures is suppose to have it but in my case it's not there (I see tikz-inet and tikz-timing via Synaptic but no other tikz packages).  I also have pgf installed.

What should I do?

Also, to generalize, is there any straightforward way to get a list of available Tex meta packages and what their contents are?  My understanding is that the contents vary by distribution, so may not be easy.  I hope that's not the case.

---

### Post by Impavidus on 2014-12-18
On my 14.04 system it should be available from texlive-pictures. But searching [CTAN]("http://ctan.org/tex-archive/graphics/pgf/contrib/tikz-qtree"), I see that tikz-qtree was initially released in December 2009. Ubuntu 12.04 comes with TeXLive 2009, so I assume it's not included.

There are three ways to solve this problem.
A: You can upgrade your entire system to Ubuntu 14.04 and get TeXLive 2013, in which your package is included (and all other TeX packages are updated). Quite easy, but with a lot of side effects.
B: You can also try managing your TeX packages with [tlmgr]("http://www.tug.org/texlive/doc/tlmgr.html"), entirely bypassing the Ubuntu package manager as far as TeX is concerned, but I don't think that will be easy to set up.
C: The third possibility, and what I would do if only dealing with a few packages, is manually installing tikz-qtree and all of its dependencies. Download the packages from CTAN and install them manually. Most come with detailed instructions in a README or INSTALL file. Some come as an archive that can simply be unpacked in your TeX directory. It's best to put them in a place where they don't interfere with the packages managed by the Ubuntu package manager. I put them in /usr/local/share/texmf/, which is searched by default. Run **sudo texhash** and they will be recognised automatically. If you miss some dependencies, TeX will complain and list the missing (or outdated) dependencies. You can install them manually too.

To get a list of TeX metapackages, you can best use the synaptic package manager. In the lower left pane, click "components" or "parts" or whatever it is named (on my system it has been translated into dutch, but it should be the first option). In the upper left pane, scroll down to "TeX Authoring" and click it. In the upper right pane you'll get a list of TeX related packages. Click one to get a description with its contents in the lower right pane. If looking for a particular TeX package, use the search box in synaptic. All included TeX packages should be mentioned in the description.

---

### Post by ken18 on 2014-12-18
Thanks.  Looks like I need to dig in and figure out how to install it manually.  It's probably not as tough as I imagine.  I was hoping for a simpler solution.

---

### Post by Impavidus on 2014-12-19
This package doesn't come with very detailed instructions. I'd put it in /usr/local/share/texmf/. This directory is in TeX's path by default on Ubuntu. Make separate directories there for the documentation and the actual code. Have a look at the standard texlive directories. On 14.04 it's in /usr/share/texlive/texmf-dist/, but I think it was different on 12.04. The log file from any TeX or LaTeX run can show you the directory from where it loads all packages. Best to make in those new direcories a directory for this package. This will be more convenient if you manually install more packages. Copy all files from the package to these directories. Something like```

/usr/local/share/texmf/doc/tikz-qtree/README
/usr/local/share/texmf/doc/tikz-qtree/tikz-qtree-manual.tex
/usr/local/share/texmf/doc/tikz-qtree/tikz-qtree-manual.pdf
/usr/local/share/texmf/tex/latex/tikz-qtree/pgfsubpic.sty
/usr/local/share/texmf/tex/latex/tikz-qtree/pgfsubpic.tex
/usr/local/share/texmf/tex/latex/tikz-qtree/pgftree.sty
/usr/local/share/texmf/tex/latex/tikz-qtree/pgftree.tex
/usr/local/share/texmf/tex/latex/tikz-qtree/tikz-qtree.sty
/usr/local/share/texmf/tex/latex/tikz-qtree/tikz-qtree.tex
/usr/local/share/texmf/tex/latex/tikz-qtree/tikz-qtree-compat.sty
```But it doesn't matter too much.

Then run **sudo texhash** or **sudo mktexlsr** (the former should be a symlink to the latter) and see whether it works. It should recognise the package, but you may need dependencies. Fortunately dependency hell in tex is not as bad as in the Ubuntu repos, so you should be able to handle it manually.

---

