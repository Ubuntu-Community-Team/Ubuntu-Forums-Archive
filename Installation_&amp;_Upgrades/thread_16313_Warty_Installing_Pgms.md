---
title: "Warty: Installing Pgms"
date: 2005-02-20
forum: Installation &amp; Upgrades
---

### Post by tromik on 2005-02-20
According to the Guide, I should simply be able to install somthing like acrobat with **sudo apt-get install X** but I get a message such as X can not be found. I though I was missing some files but I have updated and upgraded.

The only application I was able to install in this way was XMMS. 

Are these files on the Warty CD and not being read? Am I supposed to have downloaded another update?

Thanks for the help.

Sorry if this is in the wrong forum.

---

### Post by CyrilleMortreux on 2005-02-20
[QUOTE=tromik]According to the Guide, I should simply be able to install somthing like acrobat with **sudo apt-get install X** but I get a message such as X can not be found. I though I was missing some files but I have updated and upgraded.

The only application I was able to install in this way was XMMS. 

Are these files on the Warty CD and not being read? Am I supposed to have downloaded another update?

Thanks for the help.

Sorry if this is in the wrong forum.[/QUOTE]

1- Change your /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse

2- "apt-get update"

3- "apt-get install X"

4- Before, you may look for this X

"apt-cache search X" will help you.

---

### Post by tromik on 2005-02-20
Thanks, but I'm still having the problem:

```
sudo apt-get install acroread
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package acroread
tromik@ubuntu:~ $

``` 

Thanks again for the help.

Just ask for any info you think think you might need; I'm really new to this.
---------------------------------------------------------------------------------------------------------------------------------
EDIT

Ok, I figured it out, thatnks for pointing me in the right direction, to the sources.list

---

### Post by CyrilleMortreux on 2005-02-20
badlieutenant:/home/cyrille# apt-cache search acrobat
xpdf - Portable Document Format (PDF) suite
xpdf-common - Portable Document Format (PDF) suite -- common files
xpdf-reader - Portable Document Format (PDF) suite -- viewer for X11
xpdf-utils - Portable Document Format (PDF) suite -- utilities
gpdf - Portable Document Format (PDF) viewer
xpdf-i - Portable Document Format viewer for X11, with decryption support
acroread - Adobe Acrobat Reader: Portable Document Format file viewer
acroread-debian-files - Debian specific parts of Adobe Acrobat Reader
acroread-plugin - Adobe Acrobat(R) Reader plugin for mozilla / konqueror
xpdf-chinese-simplified - Portable Document Format (PDF) suite -- simplified Chinese language support
xpdf-chinese-traditional - Portable Document Format (PDF) suite -- traditional Chinese language support
xpdf-japanese - Portable Document Format (PDF) suite -- Japanese language support
xpdf-korean - Portable Document Format (PDF) suite -- Korean language support

badlieutenant:/home/cyrille# apt-get install acroread
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
  acroread-debian-files
The following NEW packages will be installed:
  acroread acroread-debian-files
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 9186kB of archives.
After unpacking 26,0MB of additional disk space will be used.
Do you want to continue? [Y/n]


Well, I am usng the hoary sources. You may use them just for that package.

---

