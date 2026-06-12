---
title: "Kernel update requires more than 200 additional packages"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by asyr on 2011-12-13
Hi there.

I'm using kubuntu 11.10 and I currently have the  3.0.0.12.14 kernel. From oneiric-updates there is a newer kernel  (linux-image-generic) 3.0.0.14.16 but if I select that I want to update  to this kernel the system selects 264 additional packages for  installation (including Japan, Chinese and more languages), wants to  remove the grub2 and install the grub legacy and several other wired  things.

Any one any idea?

---

### Post by jerrrys on 2011-12-14
This happen to me once and it turned out that the server I was using had problems.

---

### Post by bluexrider on 2011-12-14
> **jerrrys said:**
> This happen to me once and it turned out that the server I was using had problems.
Go to the Software Sources and change the server from Main Server to Other and then choose the Best Server.

```
sudo apt-get update && sudo apt-get upgrade
```after which you can run

```
sudo apt-get dist-upgrade 
```

to get the latest kernel

---

### Post by asyr on 2011-12-15
Here is my repositories:
> # cd /etc/apt; egrep '^deb ' sources.list sources.list.d/*list | cut -d: -f 2-
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric partner
deb [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) oneiric main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free
See also this:
```
# apt-get -s upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

# apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```Any idea?

---

### Post by bluexrider on 2011-12-15
What is not being upgraded is the kernel. So, to upgrade that you want to do this

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by asyr on 2011-12-16
Here it is:

```
# apt-get update
Ign http://security.ubuntu.com oneiric-security InRelease
Ign http://archive.canonical.com oneiric InRelease                             
....
Ign http://packages.medibuntu.org oneiric/non-free Translation-en              
Ign http://packages.medibuntu.org oneiric/non-free Translation-el              
Fetched 72 B in 6s (10 B/s)                                                    
Reading package lists... Done

# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  anthy anthy-common attr auctex btrfs-tools catdvi cl-asdf cl-swank clisp
  clisp-dev clisp-doc cm-super cm-super-minimal common-lisp-controller darcs
  db-util db5.1-util dblatex debhelper debiandoc-sgml debiandoc-sgml-doc
  dh-make doc-base docbook docbook-defguide docbook-dsssl docbook-dsssl-doc
  docbook-mathml docbook-utils dot2tex dovecot-common dvidvi dvipng emacs23
  emacs23-bin-common emacs23-common emacs23-el fdutils feynmf fragmaster
  graphviz graphviz-doc groff grub-legacy-doc iamerican ienglish-common ispell
  jadetex jfsutils kernel-package ko.tex-extra-hlfont lacheck latex-beamer
  latex-cjk-all latex-cjk-chinese latex-cjk-chinese-arphic-bkai00mp
  latex-cjk-chinese-arphic-bsmi00lp latex-cjk-chinese-arphic-gbsn00lp
  latex-cjk-chinese-arphic-gkai00mp latex-cjk-common latex-cjk-japanese
  latex-cjk-japanese-wadalab latex-cjk-korean latex-cjk-thai latex-cjk-xcjk
  latex-sanskrit latex-xcolor latexmk libanthy0 libauthen-sasl-perl libcdb1
  libcgraph5 libconvert-asn1-perl libdigest-hmac-perl libdw1 libffcall1
  libfile-which-perl libgssapi-perl libgvpr1 libkpathsea5 libm17n-0
  libmagick++3 libncurses5-dev libnet-ldap-perl libopagent1 libopts25 libosp5
  libostyle1c2 libotf0 libplot2c2 libpq5 libpstoedit0c2a libqt3-mt
  libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql libroman-perl libsgmls-perl
  libsp1c2 libt1-5 libtext-format-perl libtinfo-dev libuuid-perl
  libxml-namespacesupport-perl libxml-sax-expat-perl libxml-sax-perl
  libyaml-tiny-perl linux-headers-3.0.0-14 linux-headers-3.0.0-14-generic
  linux-image-3.0.0-14-generic linux-source-3.0.0 linux-tools
  linux-tools-3.0.0-14 linux-tools-common linuxdoc-tools linuxdoc-tools-info
  linuxdoc-tools-latex linuxdoc-tools-text lmodern luatex m17n-contrib m17n-db
  m17n-docs mcelog mdadm ncurses-doc ntp ntp-doc openjade opensp oprofile
  oprofile-gui perl-tk pfb2t1c2pfb pgf postfix postfix-cdb postfix-ldap
  postfix-mysql postfix-pcre postfix-pgsql preview-latex-style procmail
  prosper ps2eps psgml pstoedit psutils purifyeps python-pyparsing quota
  realpath sasl2-bin sbcl sbcl-doc sbcl-source scalable-cyrfonts-tex sgmls-doc
  sgmlspl slime sp spell squashfs-tools swath t1-cyrillic t1-oldslavic
  t1-teams t1utils tex-common texinfo texinfo-doc-nonfree texlive texlive-base
  texlive-bibtex-extra texlive-binaries texlive-common texlive-doc-base
  texlive-doc-en texlive-extra-utils texlive-font-utils texlive-fonts-extra
  texlive-fonts-extra-doc texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-generic-recommended
  texlive-lang-african texlive-lang-all texlive-lang-arabic
  texlive-lang-armenian texlive-lang-croatian texlive-lang-cyrillic
  texlive-lang-czechslovak texlive-lang-danish texlive-lang-dutch
  texlive-lang-finnish texlive-lang-french texlive-lang-german
  texlive-lang-greek texlive-lang-hebrew texlive-lang-hungarian
  texlive-lang-indic texlive-lang-italian texlive-lang-latin
  texlive-lang-latvian texlive-lang-lithuanian texlive-lang-mongolian
  texlive-lang-norwegian texlive-lang-other texlive-lang-polish
  texlive-lang-portuguese texlive-lang-spanish texlive-lang-swedish
  texlive-lang-tibetan texlive-lang-ukenglish texlive-lang-vietnamese
  texlive-latex-base texlive-latex-base-doc texlive-latex-extra
  texlive-latex-extra-doc texlive-latex-recommended
  texlive-latex-recommended-doc texlive-luatex texlive-math-extra
  texlive-metapost texlive-metapost-doc texlive-pictures texlive-pictures-doc
  texlive-pstricks texlive-pstricks-doc texlive-xetex texpower
  texpower-examples texpower-manual thailatex tipa transfig
  ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp
  ttf-arphic-gkai00mp ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk
  ttf-dejima-mincho ttf-kiloji ttf-sazanami-gothic ttf-sazanami-mincho
  ttf-thai-tlwg ttf-unfonts-core ttf-unfonts-extra ttf-vlgothic ttf-wqy-zenhei
  w3-dtd-mathml w3c-dtd-xhtml xaw3dg xfig xfig-doc xfig-libs xfs xfsdump
  xfsprogs xindy xindy-rules xmltex xmlto xsltproc
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 266 newly installed, 0 to remove and 0 not upgraded.
Need to get 1210 MB of archives.
After this operation, 2478 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```The point is that I do not want all these packages... (e.g. anthy, or texlive-lang-african)
Why is that?

---

### Post by bluexrider on 2011-12-16
You have obviously installed a program or application that requires those dependencies. It is trying to update what is already on your system. apt-get doesn't know YOU don't want them, it is updating what is currently residing on YOUR system.

If you don't want the update then cancel. If you don't want the packages then remove them.

---

### Post by asyr on 2011-12-16
So, I have a lot of investigation, in order to identify which is the "problematic" package.

I'll inform you when I'll find it.

---

### Post by snowpine on 2011-12-16
The obvious culprit from the looks of things is Texlive. Have you used a PPA, repo, or 3rd-party source for Texlive at any point?

---

### Post by bluexrider on 2011-12-16
> **snowpine said:**
> The obvious culprit from the looks of things is Texlive. Have you used a PPA, repo, or 3rd-party source for Texlive at any point?

The TeX Live software distribution offers a complete TeX system.
It encompasses programs for typesetting, previewing and printing
of TeX documents in many different languages, and a large collection
of TeX macros and font libraries.

This metapackage provides a decent selection of the TeX Live packages
which should suffice for the most common tasks.

The distribution also includes extensive general documentation about
TeX, as well as the documentation accompanying the included software
packages.

You could use synaptic or Ubuntu software center to remove the app

---

### Post by asyr on 2011-12-19
Guys, thanks all a lot for your time.

I posted the same case at kubuntu forums and we manage to solve the problem there.
See here: [http://kubuntuforums.net/forums/index.php?topic=3119705]("http://http//kubuntuforums.net/forums/index.php?topic=3119705")

The problem was the "Treat Suggested Packages As Dependencies" at muon.

---

