---
title: "pre-removal script returned error exit status 1"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by shaoxuan on 2011-03-08
Hello,

I'm using ubuntu 10.10 maverick, a package named lmodern is not required by the system, but it can't be remove or purged as follow:

```
yurippe@Neptune:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lmodern
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 46.7MB disk space will be freed.
Do you want to continue [Y/n]? Y

(Reading database ... 264790 files and directories currently installed.)

Removing lmodern ...
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
dpkg: error processing lmodern (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 lmodern
E: Sub-process /usr/bin/dpkg returned an error code (1)
yurippe@Neptune:~$
```

I have tried:

```
sudo apt-get autoclean
sudo apt-get clean
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

all without any error, but lmodern can't be removed.

Now how can I do to remove this unneeded package? Thanks.

---

### Post by tommcd on 2011-03-09
The lmodern package is apparently a font package and should do no harm.
[http://packages.ubuntu.com/maverick/lmodern](http://packages.ubuntu.com/maverick/lmodern)
 If you want to remove it, try: ```
sudo apt-get remove lmodern
``` or
```
sudo apt-get remove --purge lmodern
```
Be careful before hitting *yes*. APT may want to remove some dependencies that you need.
You could always just reinstall lmodern if APT removes some dependencies that you need.

---

### Post by shaoxuan on 2011-03-09
> **tommcd said:**
> The lmodern package is apparently a font package and should do no harm.
[http://packages.ubuntu.com/maverick/lmodern](http://packages.ubuntu.com/maverick/lmodern)
 If you want to remove it, try: ```
sudo apt-get remove lmodern
``` or
```
sudo apt-get remove --purge lmodern
```
Be careful before hitting *yes*. APT may want to remove some dependencies that you need.
You could always just reinstall lmodern if APT removes some dependencies that you need.

Thanks for your reply.:)

yes, lmodern package is no harm for the system, but it's not needed by any packages, so it's better to remove it to regain disk space.

I have tried the commands you suggested, but the output was as the same as before, so any ideas?

Thanks.

---

### Post by tommcd on 2011-03-09
Post the output of: ```
sudo apt-get remove --purge lmodern
```
Also install *aptitude* from the Ubuntu repositories. Aptitude used to be part of a standard Ubuntu install. (It seems that the Ubuntu developers, in their infinite wisdom, have decided that aptitude is no longer needed. This is in spite of the fact that aptitude is the recommended package manger in Debian, which is Ubuntu's parent).
Then post the output of: ```
aptitude search lmodern
```
This will show the state of any lmodern* packages that you may have on your system.

---

### Post by shaoxuan on 2011-03-09
> **tommcd said:**
> Post the output of: ```
sudo apt-get remove --purge lmodern
```
Also install *aptitude* from the Ubuntu repositories. Aptitude used to be part of a standard Ubuntu install. (It seems that the Ubuntu developers, in their infinite wisdom, have decided that aptitude is no longer needed. This is in spite of the fact that aptitude is the recommended package manger in Debian, which is Ubuntu's parent).
Then post the output of: ```
aptitude search lmodern
```
This will show the state of any lmodern* packages that you may have on your system.

Thanks for your reply.:D

the remove --purge output:

```
yurippe@Neptune:~$ sudo apt-get remove --purge lmodern
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lmodern*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 46.7MB disk space will be freed.
Do you want to continue [Y/n]? Y

(Reading database ... 264977 files and directories currently installed.)

Removing lmodern ...
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
W: type1: Category not found.
dpkg: error processing lmodern (--purge):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 lmodern
E: Sub-process /usr/bin/dpkg returned an error code (1)
yurippe@Neptune:~$
```

The output of aptitude search:

```
yurippe@Neptune:~$ aptitude search lmodern
idA lmodern                         - scalable PostScript and OpenType fonts bas
yurippe@Neptune:~$
```

It seems that there is only one package correlates with lmodern.

Any ideas? Thanks.

---

### Post by tommcd on 2011-03-09
I have just booted my Xubuntu 10.10 install to check out this lmodern package. I do not have the lmodern package installed. Therefore, it must have been installed as a dependency for something else on your system.

Do you have any third party repositories installed on your system? This includes those all too problematic PPA repos that seem to cause so many problems around here.

---

### Post by shaoxuan on 2011-03-09
> **tommcd said:**
> I have just booted my Xubuntu 10.10 install to check out this lmodern package. I do not have the lmodern package installed. Therefore, it must have been installed as a dependency for something else on your system.

Do you have any third party repositories installed on your system? This includes those all too problematic PPA repos that seem to cause so many problems around here.

Thanks for the reply.

I have installed the texlive-full Bundle before:

(without using third party PPA repository to install this bundle)

```
yurippe@Neptune:~$sudo apt-get install texlive-full
```

But the installation process is not successful, due to error with cm-super and cm-super-minimal packages, the texlive-full bundle (95 packages or so) failed to install. So I have to remove them all. The lmodern package is installed along with texlive-full bundle, but it can't be removed. All other packages correlate with texlive-full are removed successfully.

---

### Post by tommcd on 2011-03-09
> **shaoxuan said:**
> 
I have installed the texlive-full Bundle before:
(without using third party PPA repository to install this bundle)
What version of Ubuntu are you using? The lmodern package is not listed as a dependency of texlive-full on Ubuntu 10.10 or 10.04:
[http://packages.ubuntu.com/maverick/texlive-full](http://packages.ubuntu.com/maverick/texlive-full)
[http://packages.ubuntu.com/lucid/texlive-full](http://packages.ubuntu.com/lucid/texlive-full)
This is likely why you are having problems. You must have gotten that lmodern package from somewhere. Do you know if you installed it from anywhere else than the standard Ubuntu repos?
> **shaoxuan said:**
>  
But the installation process is not successful, due to error with cm-super and cm-super-minimal packages, the texlive-full bundle (95 packages or so) failed to install. So I have to remove them all. The lmodern package is installed along with texlive-full bundle, but it can't be removed. All other packages correlate with texlive-full are removed successfully.
Post the output of: ```
aptitude search texlive-full
```
Per japs you could try switching to another Ubuntu mirror.

---

### Post by shaoxuan on 2011-03-09
> **tommcd said:**
> What version of Ubuntu are you using? The lmodern package is not listed as a dependency of texlive-full on Ubuntu 10.10 or 10.04:
[http://packages.ubuntu.com/maverick/texlive-full](http://packages.ubuntu.com/maverick/texlive-full)
[http://packages.ubuntu.com/lucid/texlive-full](http://packages.ubuntu.com/lucid/texlive-full)
This is likely why you are having problems. You must have gotten that lmodern package from somewhere. Do you know if you installed it from anywhere else than the standard Ubuntu repos?

Post the output of: ```
aptitude search texlive-full
```
Per japs you could try switching to another Ubuntu mirror.

Hello, I'm using ubuntu 10.10 maverick.

I think lmodern is a recommanded package by texlive-full, not dependency, but it was installed along with texlive-full:

```
yurippe@Neptune:~$ LANG=en-US
yurippe@Neptune:~$ sudo apt-get install texlive-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cm-super cm-super-minimal context dvipng feynmf fragmaster lacheck
  latex-beamer latex-cjk-all latex-cjk-chinese
  latex-cjk-chinese-arphic-bkai00mp latex-cjk-chinese-arphic-bsmi00lp
  latex-cjk-chinese-arphic-gbsn00lp latex-cjk-chinese-arphic-gkai00mp
  latex-cjk-common latex-cjk-japanese latex-cjk-japanese-wadalab
  latex-cjk-korean latex-cjk-thai latex-cjk-xcjk latex-sanskrit latex-xcolor
  latexmk luatex musixtex pgf preview-latex-style prosper ps2eps tex4ht
  tex4ht-common texlive-base texlive-bibtex-extra texlive-binaries
  texlive-common texlive-doc-base texlive-doc-bg texlive-doc-cs+sk
  texlive-doc-de texlive-doc-en texlive-doc-es texlive-doc-fi texlive-doc-fr
  texlive-doc-it texlive-doc-ja texlive-doc-ko texlive-doc-mn texlive-doc-nl
  texlive-doc-pl texlive-doc-pt texlive-doc-ru texlive-doc-si texlive-doc-th
  texlive-doc-tr texlive-doc-uk texlive-doc-vi texlive-doc-zh
  texlive-extra-utils texlive-font-utils texlive-fonts-extra
  texlive-fonts-extra-doc texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-formats-extra texlive-games
  texlive-generic-extra texlive-generic-recommended texlive-humanities
  texlive-humanities-doc texlive-lang-african texlive-lang-arabic
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
  texlive-latex-recommended-doc texlive-latex3 texlive-luatex
  texlive-math-extra texlive-metapost texlive-metapost-doc texlive-music
  texlive-omega texlive-pictures texlive-pictures-doc texlive-plain-extra
  texlive-pstricks texlive-pstricks-doc texlive-publishers
  texlive-publishers-doc texlive-science texlive-science-doc texlive-xetex
  thailatex tipa
Suggested packages:
  fontforge context-nonfree context-doc-nonfree auctex hbf-cns40-b5 hbf-jfs56
  ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp
  ttf-arphic-gkai00mp hbf-kanji48 ttf-dejima-mincho ttf-kiloji ttf-baekmuk
  ttf-sazanami-gothic ttf-sazanami-mincho ttf-unfonts-extra ttf-vlgothic pmx
  m-tx dvidvi purifyeps xindy texpower passivetex jadetex xmltex
  scalable-cyrfonts-tex
Recommended packages:
  lmodern
The following NEW packages will be installed:
  cm-super cm-super-minimal context dvipng feynmf fragmaster lacheck
  latex-beamer latex-cjk-all latex-cjk-chinese
  latex-cjk-chinese-arphic-bkai00mp latex-cjk-chinese-arphic-bsmi00lp
  latex-cjk-chinese-arphic-gbsn00lp latex-cjk-chinese-arphic-gkai00mp
  latex-cjk-common latex-cjk-japanese latex-cjk-japanese-wadalab
  latex-cjk-korean latex-cjk-thai latex-cjk-xcjk latex-sanskrit latex-xcolor
  latexmk luatex musixtex pgf preview-latex-style prosper ps2eps tex4ht
  tex4ht-common texlive-base texlive-bibtex-extra texlive-binaries
  texlive-common texlive-doc-base texlive-doc-bg texlive-doc-cs+sk
  texlive-doc-de texlive-doc-en texlive-doc-es texlive-doc-fi texlive-doc-fr
  texlive-doc-it texlive-doc-ja texlive-doc-ko texlive-doc-mn texlive-doc-nl
  texlive-doc-pl texlive-doc-pt texlive-doc-ru texlive-doc-si texlive-doc-th
  texlive-doc-tr texlive-doc-uk texlive-doc-vi texlive-doc-zh
  texlive-extra-utils texlive-font-utils texlive-fonts-extra
  texlive-fonts-extra-doc texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-formats-extra texlive-full
  texlive-games texlive-generic-extra texlive-generic-recommended
  texlive-humanities texlive-humanities-doc texlive-lang-african
  texlive-lang-arabic texlive-lang-armenian texlive-lang-croatian
  texlive-lang-cyrillic texlive-lang-czechslovak texlive-lang-danish
  texlive-lang-dutch texlive-lang-finnish texlive-lang-french
  texlive-lang-german texlive-lang-greek texlive-lang-hebrew
  texlive-lang-hungarian texlive-lang-indic texlive-lang-italian
  texlive-lang-latin texlive-lang-latvian texlive-lang-lithuanian
  texlive-lang-mongolian texlive-lang-norwegian texlive-lang-other
  texlive-lang-polish texlive-lang-portuguese texlive-lang-spanish
  texlive-lang-swedish texlive-lang-tibetan texlive-lang-ukenglish
  texlive-lang-vietnamese texlive-latex-base texlive-latex-base-doc
  texlive-latex-extra texlive-latex-extra-doc texlive-latex-recommended
  texlive-latex-recommended-doc texlive-latex3 texlive-luatex
  texlive-math-extra texlive-metapost texlive-metapost-doc texlive-music
  texlive-omega texlive-pictures texlive-pictures-doc texlive-plain-extra
  texlive-pstricks texlive-pstricks-doc texlive-publishers
  texlive-publishers-doc texlive-science texlive-science-doc texlive-xetex
  thailatex tipa
0 upgraded, 124 newly installed, 0 to remove and 0 not upgraded.
Need to get 960MB of archives.
After this operation, 1690MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
yurippe@Neptune:~$
```

The output of aptitude search texlive-full:

```
yurippe@Neptune:~$ aptitude search texlive-full
p   texlive-full                    - TeX Live: metapackage pulling in all compo
yurippe@Neptune:~$
```

Thanks.

---

### Post by shaoxuan on 2011-03-09
Is there any way to remove the unneeded lmodern package? Thanks.

---

### Post by tommcd on 2011-03-10
I just installed lmodern on my system. I was able to remove it with.
```
sudo apt-get remove --purge lmodern
```
I did not want to try installing texlive-full because according to your post #9 here it installs a total of 124 packages (Yikes!!).
Your output from "*aptitude search lmodern*" gives this:
**idA lmodern**
The **i** means that it is installed.
The **d** means that the pending action is to delete it. This is due to you running: ```
sudo apt-get remove --purge lmodern
```
The **A** means that it was automatically installed, usually as a dependency for another package.
A **p** means a package is purged (i.e., not installed).
You could try to remove the stubborn lmodern package with:
```
sudo dpkg --remove --force-remove lmodern
```
Some searching around has found a similar problem when installing texlive-pstrick-doc:
[http://ubuntuforums.org/showthread.php?t=1597294](http://ubuntuforums.org/showthread.php?t=1597294)
The user "fixed" it by adding the repo for 10.04; but I would not recommend that.

---

