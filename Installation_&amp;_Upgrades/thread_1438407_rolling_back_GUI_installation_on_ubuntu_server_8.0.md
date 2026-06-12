---
title: "rolling back GUI installation on ubuntu server 8.04 LTS"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by araruna on 2010-03-25
Hi, guys.

I, someday in my life, tried to add GUI to my installation of ubuntu server 8.04 LTS (don't ask me why, :D ).
The problem is, I gave up before the instalation had finished, and some packages became broken.
Now, everytime I try to install a new package, aptitude forces me to also install the dependencies of the previously "installed" packages, like abiword, xinit and so on.

The worst part: I don't remember what package I used to try this installation (x-window-system-core, gnome, gnome-core, {k,x,}ubuntu-desktop...).

Does anybody have any suggestions??? I must fix this as soon as possible, because this server is already at production... :(

The output from aptitude is listed below (just the list of suggested [imposed] packages):
```
The following NEW packages will be automatically installed:
  abiword abiword-common abiword-help abiword-plugins aspell aspell-en 
  dictionaries-common doc-base docbook-xml dvipdfmx gnome-icon-theme 
  hicolor-icon-theme imagemagick latex-beamer latex-xcolor latex-xft-fonts 
  libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a 
  libart-2.0-2 libaspell15 libatk1.0-0 libatk1.0-data libcairo2 libcroco3 
  libdatrie0 libdjvulibre15 libdrm2 libenchant1c2a libfontenc1 libfs6 
  libgail-common libgail18 libgd2-noxpm libgdome2-0 libgdome2-cpp-smart0c2a 
  libgl1-mesa-glx libglade2-0 libgnomecanvas2-0 libgnomecanvas2-common 
  libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data 
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgraphviz4 libgsf-1-114 
  libgsf-1-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common 
  libgtkmathview0c2a libhunspell-1.1-0 libice6 libjasper1 libkpathsea4 
  liblcms1 liblink-grammar4 libmagick10 libopenexr2ldbl libots0 
  libpango1.0-0 libpango1.0-common libpixman-1-0 librsvg2-2 librsvg2-common 
  libscrollkeeper0 libsm6 libt1-5 libthai-data libthai0 libwmf0.2-7 
  libwpd-stream8c2a libwpd8c2a libx11-6 libx11-data libxau6 libxaw7 
  libxcb-xlib0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 
  libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxkbfile1 
  libxmu6 libxmuu1 libxpm4 libxrandr2 libxrender1 libxslt1.1 libxt6 
  libxtrap6 libxtst6 libxv1 libxxf86dga1 libxxf86misc1 libxxf86vm1 
  link-grammar-dictionaries-en lmodern perl-tk pgf prosper python-psyco 
  scrollkeeper sgml-data shared-mime-info tetex-bin tex-common texlive 
  texlive-base texlive-base-bin texlive-base-bin-doc texlive-common 
  texlive-doc-base texlive-fonts-recommended texlive-fonts-recommended-doc 
  texlive-generic-recommended texlive-latex-base texlive-latex-base-doc 
  texlive-latex-recommended texlive-latex-recommended-doc texlive-pstricks 
  texlive-pstricks-doc tipa x-ttcidfont-conf x11-apps x11-common 
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils 
  xauth xbase-clients xdg-utils xfonts-base xfonts-encodings xfonts-utils 
  xinit xsltproc xutils xutils-dev xvfb
```


Thank you all. ;)

---

### Post by zvacet on 2010-03-25
Maybe this is not most elegant way to do it but install that packages.After that with 

```
apt-cache search
```

find witch desktop (or other package witch pull all those dependencies) you installed.Remove it with (**please check first that command is right**).For example if it is xubuntu-desktop

```
sudo taskel remove xubuntu-desktop
```

---

### Post by araruna on 2010-03-25
Well, I already tried to remove all those packages I mentioned which install GUI to ubuntu server via *aptitude remove*. None of them is installed, but aptitude still wants to install the other ones...

Should I allow them to be installed and after manage to uninstall them?

Thanks :D

---

### Post by zvacet on 2010-03-25
> Should I allow them to be installed and after manage to uninstall them?

Yes,I think it is the only way,because if you don´t install that packages you will not be able to install anything.

EDIT: If you want to see witch desktop you installed (for example xubuntu-desktop)

```
apt-cache show xubuntu-desktop
```

In my case it look like this

> ~$ apt-cache show ubuntu-desktop
Package: ubuntu-desktop
Priority: optional
Section: metapackages
Installed-Size: 56
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Architecture: i386
Source: ubuntu-meta
Version: 1.175


and after that long list of dependencies.Pay attention on **Installed-Size: 56**

---

### Post by zvacet on 2010-03-25
Easier way to find out witch desktop you installed is to type

```
tasksel -t
```

---

