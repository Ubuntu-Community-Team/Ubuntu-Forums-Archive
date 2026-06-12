---
title: "LMC(moviefly)"
date: 2005-06-01
forum: Installation &amp; Upgrades
---

### Post by rickympl on 2005-06-01
Hi, I would like to know if anyone is able to install the Ant Movie Catalog version for Linux, which is LMC or Moviefly written in Python, the Link to the page is [LMC](https://savannah.nongnu.org/projects/lmc/) 

there is a .deb file in their page, but I can't seem to install it because it keeps on complaining about some packages that it needs, but the pk-ubuntu is installed instead, and so on.

Maybe it´s just me, that doesn't know how to install it. ](*,) 

I would like some help on this please.

This is the output when I try installing it with Synaptic:

lmc:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
 Recommends: transcode but it is not going to be installed

This is my source.list file : 
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

deb [ftp://ftp.real-time.com/linux/real-time](ftp://ftp.real-time.com/linux/real-time) unstable custom
deb-src [ftp://ftp.real-time.com/linux/real-time](ftp://ftp.real-time.com/linux/real-time) unstable custom

deb [http://freevo.sourceforge.net/debian](http://freevo.sourceforge.net/debian) unstable main
#deb [http://marillat.free.fr/](http://marillat.free.fr/) unstable main

deb [http://www.mpe.mpg.de/~ach/kubuntu/hoary](http://www.mpe.mpg.de/~ach/kubuntu/hoary) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/hoary](http://www.mpe.mpg.de/~ach/kubuntu/hoary) ./ 

deb [http://www.master-ai.uni-karlsruhe.de/~merkosh/lmc/debian/sarge](http://www.master-ai.uni-karlsruhe.de/~merkosh/lmc/debian/sarge) ./
deb-src [http://www.master-ai.uni-karlsruhe.de/~merkosh/lmc/debian/sarge](http://www.master-ai.uni-karlsruhe.de/~merkosh/lmc/debian/sarge) ./

deb [http://debian.xmixahlx.com/packages/unstable/](http://debian.xmixahlx.com/packages/unstable/) ./
deb [http://debian.jones.dk](http://debian.jones.dk) woody misc

deb [http://www-users.cs.umn.edu/~sdier/debian](http://www-users.cs.umn.edu/~sdier/debian) updates/wup/ 



Thank you.

---

### Post by xiownthisplacex on 2006-11-15
Well, it is easier to use winE, download ant movie catalog and in the terminal write: wine "file name downloaded"

that should install ant movie catalog in ubuntu..

---

