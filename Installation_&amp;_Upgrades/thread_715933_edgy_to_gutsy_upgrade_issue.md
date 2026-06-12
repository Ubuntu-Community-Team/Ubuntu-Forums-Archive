---
title: "edgy to gutsy upgrade issue"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by GhettoPuNKkiD on 2008-03-05
```
erik@hobbes:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  texlive-lang-finnish liborbit2-dev tetex-extra guile-1.6 libaudiofile-dev texlive-lang-latin texlive tetex-base libcrypt-ssleay-perl libhal-storage-dev
  guile-g-wrap libfinance-quote-perl libsgutils1 libgnome-keyring-dev texlive-math-extra libavahi-client-dev texlive-pstricks preview-latex-style
  libmono-cairo2.0-cil texlive-lang-portuguese texlive-lang-french libsvn0 tetex-bin slib texlive-lang-greek libffi4 libreadline5-dev texlive-lang-spanish
  ruby libbonobo2-dev texlive-lang-cyrillic libt1-5 texlive-lang-swedish texlive-latex-extra libhtml-tableextract-perl texlive-publishers
  texlive-bibtex-extra libmono-sqlite2.0-cil guile-1.6-dev libifp4 libidl-dev libart-2.0-dev guile-library libesd0-dev libffi4-dev libgnomecanvas2-dev
  texlive-lang-norwegian texlive-generic-recommended libgwrap-runtime0-dev libhal-dev g-wrap texlive-lang-italian texlive-lang-german libncurses5-dev
  libselinux1-dev texlive-fonts-extra texlive-lang-polish texlive-font-utils texlive-lang-danish texlive-lang-croatian libaahi-glib-dev
  libavahi-common-dev guile-1.6-slib texlive-lang-dutch texlive-lang-hungarian gnucash-common libsepol1-dev texlive-lang-mongolian texlive-lang-vietnamese
  texlive-pictures texlive-lang-czechslovak libnjb5 libgwrap-runtime0 texlive-lang-other
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  hplip
Suggested packages:
  kdeprint gtklp xpp hpijs-ppds hplip-doc hplip-gui
Recommended packages:
  python-reportlab
The following packages will be upgraded:
  hplip
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/300kB of archives.
After unpacking 2142kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 225057 files and directories currently installed.)
Preparing to replace hplip 1.7.3-0ubuntu1.1 (using .../hplip_2.7.12-0ubuntu2~gutsy1_i386.deb) ...
 * Stopping HP Linux Printing and Imaging System                                                                                                      [ OK ] 
Old HPLIP daemon (hpiod) should of stopped, but did not.  Please kill manually before hplip can proceed
dpkg: error processing /var/cache/apt/archives/hplip_2.7.12-0ubuntu2~gutsy1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/hplip_2.7.12-0ubuntu2~gutsy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
erik@hobbes:~$ 


```

I'm having issues with upgrade from Edgy to Gutsy...  I did indeed stop the hplip service.. but I'm still getting this error.. any help would be appreciated!

Thanks!:guitar:

---

### Post by zvacet on 2008-03-05
> I'm having issues with upgrade from Edgy to Gutsy

Of course you have.You can not upgrade from Edgy to Gutsy.You have to do it like this **Edgy>Feisty>Gutsy** One step at the time.Try to backup your data and do fresh install of Gutsy.

---

### Post by GhettoPuNKkiD on 2008-03-05
oh wait wait.. i did have feisty installed before doing this...my bad.... i was lost.. but i did install feisty.. and that worked out fine..

---

