---
title: "Not able to install some packages. apt-get getting stuck."
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by m4enigma on 2010-09-29
Hello,

I am not able to install kile on Ubuntu 10.10 Maverick using apt-get or Synaptic package manager. The installation gets stuck at 0% saying waiting for headers and after a while gives the following error :

```
Err http://in.archive.ubuntu.com/ubuntu/ maverick/main texlive-base all 2009-10
  Connection failed
```I am however able to install other packages through apt-get.

Please help.

---

### Post by garvinrick4 on 2010-09-29
> **m4enigma said:**
> Hello,

```
I am not able to install kile on Ubuntu 10.10 Maverick using apt-get or Synaptic package manager. The installation gets stuck at 0% saying waiting for headers and after a while gives the following error :

[CODE]Err http://in.archive.ubuntu.com/ubuntu/ maverick/main texlive-base all 2009-10
  Connection failed
```I am however able to install other packages through apt-get.

Please help.[/CODE]```
 There is no nothing in maverick/main texlive-base all 2009-10 


All though here is my maverick in universe
Looks like KDE package:

rick@rick-laptop:~$ aptitude show kile
Package: kile                            
State: not installed
Version: 1:2.1.0~svn1112278beta4-2ubuntu1
Priority: optional
Section: universe/tex
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 11.5M
Depends: kdebase-runtime, libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libkdecore5 (>=
         4:4.4.85), libkdeui5 (>= 4:4.4.4), libkfile4 (>= 4:4.4.4), libkhtml5
         (>= 4:4.4.4), libkio5 (>= 4:4.4.4), libkjsapi4 (>= 4:4.4.4), libkparts4
         (>= 4:4.4.4), libkrosscore4 (>= 4:4.4.4), libktexteditor4 (>= 4:4.4.4),
         libnepomuk4 (>= 4:4.4.4), libqt4-dbus (>= 4:4.5.3), libqt4-network (>=
         4:4.5.3), libqt4-script (>= 4:4.5.3), libqt4-svg (>= 4:4.5.3),
         libqt4-xml (>= 4:4.5.3), libqtcore4 (>=
         4:4.7.0~beta1+git20100522-0ubuntu4), libqtgui4 (>= 4:4.5.3),
         libsoprano4 (>= 2.4.63+svn1134879+dfsg.1), libstdc++6 (>= 4.1.1),
         konsole, texlive-base-bin, texlive-latex-base
Recommends: asymptote, context, dblatex, dvipdfmx, dvipng, ghostscript,
            imagemagick, kbibtex | pybliographer | gbib | jabref, konqueror |
            firefox, latex2html, lilypond, okular | evince | gv, psutils,
            tex4ht, texlive-metapost, texlive-xetex, zip
Suggests: kile-doc, texlive-doc-base, aspell | ispell | hspell
Conflicts: ktexmaker2 (< 1.8)
Replaces: ktexmaker2 (< 1.8)
Description: KDE Integrated LaTeX Environment
 Kile is a user-friendly LaTeX source editor and TeX shell for KDE. 
 
 The source editor is a multi-document editor designed for .tex and .bib files.
 Menus, wizards and auto-completion are provided to assist with tag insertion
 and code generation.  A structural view of the document assists with navigation
 within source files. 
 
 The TeX shell integrates the various tools required for TeX processing. It
 assists with LaTeX compilation, DVI and postscript document viewing, generation
 of bibliographies and indices and other common tasks. 
 
 Kile can support large projects consisting of several smaller files.
Homepage: [http://kile.sourceforge.net](http://kile.sourceforge.net)

rick@rick-laptop:~$ 


```

---

### Post by m4enigma on 2010-09-29
I have already installed Kile in 10.04 running gnome.

---

