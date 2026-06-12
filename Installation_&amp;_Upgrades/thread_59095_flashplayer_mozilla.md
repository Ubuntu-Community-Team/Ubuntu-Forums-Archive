---
title: "flashplayer mozilla"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by Beej on 2005-08-22
Reinstalled Hoary recently after breezy stopped working and realising I was a bit above my head. I've been going through the usual reinstallation proceedure, using the ubuntu guide as a walkthrough. I cant seem to get flashplayer mozilla to install through synaptic or apt.

here's the content of my sources.list

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://www.csd.uwo.ca/~mfgalizi/debian](http://www.csd.uwo.ca/~mfgalizi/debian) hoary unichrome
deb-src [http://www.csd.uwo.ca/~mfgalizi/debian](http://www.csd.uwo.ca/~mfgalizi/debian) hoary unichrome

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted




Anybody any ideas where I'm going wrong? 

Thanks,

Beej

---

### Post by Swab on 2005-08-22
[QUOTE=Beej]Reinstalled Hoary recently after breezy stopped working and realising I was a bit above my head. I've been going through the usual reinstallation proceedure, using the ubuntu guide as a walkthrough. I cant seem to get flashplayer mozilla to install through synaptic or apt.

here's the content of my sources.list



Anybody any ideas where I'm going wrong? 

Thanks,

Beej[/QUOTE]

I just use the linux installer from flash.com ... didn't even know flash player was in any of the repositories..

---

### Post by Beej on 2005-08-23
Downloaded and working, thanks for the pointer. Was definately in the repo's before. Anybody know if it's been removed for some reason?

---

### Post by SymGeosis on 2005-08-26
I have the same problem with flash as well as Sun JRE, lame, mjpegtools and a few others I'm sure. It's rather annoying but I suspect that all of those might be legally questionable some how.

EDIT:

I found the problem, somehow I had managed to not add multiverse to my sources list. Kinda embarassing actually.

---

