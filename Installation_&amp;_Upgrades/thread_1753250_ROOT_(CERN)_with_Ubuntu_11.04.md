---
title: "ROOT (CERN) with Ubuntu 11.04"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by davoudi on 2011-05-08
Hello,

 I have recently made a fresh installation of Ubuntu 11.04 with Gnome 3. Everything works fine until I installed root (cern) 5.28.00d on my machine. The installation was not straightforward, read here: [http://root.cern.ch/phpBB3/viewtopic.php?f=3&t=12628&p=54759#p54759](http://root.cern.ch/phpBB3/viewtopic.php?f=3&t=12628&p=54759#p54759) until the last release. Now I am facing with the following error when I try to run root (cern) : 
Couldn't find font "-adobe-helvetica-medium-r-*-*-10-*-*-*-*-*-iso8859-1",
trying "fixed". Please fix your system so helvetica can be found,
this font typically is in the rpm (or pkg equivalent) package
XFree86-[75,100]dpi-fonts or fonts-xorg-[75,100]dpi.

I Installed the extra packages suggested at [http://root.cern.ch/phpBB3/viewtopic.php?f=3&t=12627](http://root.cern.ch/phpBB3/viewtopic.php?f=3&t=12627) but the error still persist. This is the outcome of ps -aef | grep xfs

114       1050     1  0 May07 ?        00:00:00 /usr/bin/xfs -daemon -user debian-xfs -droppriv
root      1065     1  0 May07 ?        00:00:00 /usr/bin/xfstt --daemon --notcp
davoudi   4916  1954  0 15:30 pts/0    00:00:00 grep --color=auto xfs

Any help is appreciated.

---

### Post by finitybeyond on 2011-05-15
Did you get this error when running configure? I also had issues trying to build ROOT on Natty x86_64. You have to manually set the --with flags for the X libraries because they are in /usr/lib/x86_64-linux-gnu now for some reason. Try redoing your build from the beginning. I have written a tutorial here:

[http://cometpeak.com/2011/05/building-and-installing-root-on-ubuntu-11-04-x86_64/](http://cometpeak.com/2011/05/building-and-installing-root-on-ubuntu-11-04-x86_64/)

Also, which architecture are you running? In any case, I was able to successfully build ROOT on Natty x86_64.

---

### Post by davoudi on 2011-05-16
> **finitybeyond said:**
> Did you get this error when running configure? I also had issues trying to build ROOT on Natty x86_64. You have to manually set the --with flags for the X libraries because they are in /usr/lib/x86_64-linux-gnu now for some reason. Try redoing your build from the beginning. I have written a tutorial here:

[http://cometpeak.com/2011/05/building-and-installing-root-on-ubuntu-11-04-x86_64/](http://cometpeak.com/2011/05/building-and-installing-root-on-ubuntu-11-04-x86_64/)

Also, which architecture are you running? In any case, I was able to successfully build ROOT on Natty x86_64.

I used the latest version of ROOT (5.28.00d). This version has no problem with configuring, compiling and installing. This error just appear when I run root. I will try your tutorial soon. Thanks.

---

