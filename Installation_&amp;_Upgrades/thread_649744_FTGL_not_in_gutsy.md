---
title: "FTGL not in gutsy?"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by alienjon on 2007-12-25
So I'm totally lost here. I'm doing some development which has brought me into the opengl realm and in some of the examples and things I've been working with FTGL is required. For some reason, though (and despite the lack of issues this forum and google as a whole has shown) I don't have the ftgl-dev package on my system. I upgraded to Kubuntu 7.10 a few weeks ago and I can't seem to find the package in apt nor any similar problems in the world-wide-web.

---

### Post by logos34 on 2007-12-25
is this it?

> $ apt-cache search ftgl-dev
ftgl-dev - Library to render text in OpenGL using FreeType

$ apt-cache show ftgl-dev
Package: ftgl-dev
Priority: optional
Section: universe/devel
Installed-Size: 960
Maintainer: Marcelo E. Magallon <mmagallo@debian.org>
Architecture: amd64
Source: ftgl
Version: 2.1.2-3
Depends: libfreetype6-dev, libgl1-mesa-dev | libgl-dev, libglu1-mesa-dev | libglu-dev, g++
Filename: pool/universe/f/ftgl/ftgl-dev_2.1.2-3_amd64.deb
Size: 134982
MD5sum: 72e073fbcd30e0d5768555f1ef116a0a
SHA1: 3751ab3bdf89d73dd1fe203c39cb9df0c0fb428a
SHA256: d6d2e53f04d1ba8fd6fc953e9e1a559928f322cfaf2b3967c5bba8f6c633867a
Description: Library to render text in OpenGL using FreeType
 FTGL binds OpenGL and FreeType together in order to offer and easy to use
 and flexible text rendering library.  It offers several rendering modes:
 as polygons, outlines, bitmaps and textures.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by alienjon on 2007-12-25
That would be it, but it isn't on my system.  The first commend you provided, for instance, doesn't return or otherwise output anything and the second gives:

```
W: Unable to locate package ftgl-dev
E: No packages found
```

---

### Post by forestpixie on 2007-12-25
it should be in universe, either check your sources.list or post it here

Edit - you can find it here anyway

```
http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Ff%2Fftgl%2Fftgl-dev_2.1.2-3_i386.deb&md5sum=9d88847fadea44bba50907e19576bd4d&arch=i386&type=main
```

---

### Post by alienjon on 2007-12-25
```
# 
# deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted

# deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.cs.utah.edu/ubuntu/ gutsy main restricted
deb-src http://ubuntu.cs.utah.edu/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ubuntu.cs.utah.edu/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.cs.utah.edu/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://ubuntu.cs.utah.edu/ubuntu/ gutsy-security main restricted
deb-src http://ubuntu.cs.utah.edu/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://ubuntu.cs.utah.edu/ubuntu/ gutsy-security universe
deb http://ubuntu.cs.utah.edu/ubuntu/ gutsy-updates restricted main multiverse universe
deb-src http://ubuntu.cs.utah.edu/ubuntu/ gutsy-updates restricted main multiverse universe
deb http://ubuntu.cs.utah.edu/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://ubuntu.cs.utah.edu/ubuntu/ gutsy-proposed restricted main multiverse universe
deb http://ubuntu.cs.utah.edu/ubuntu/ gutsy-backports restricted main multiverse universe
deb-src http://ubuntu.cs.utah.edu/ubuntu/ gutsy-backports restricted main multiverse universe
deb http://ubuntu.cs.utah.edu/ubuntu/ gutsy-security multiverse
```

---

### Post by forestpixie on 2007-12-25
well thats a bit odd - looks ok to me and I guess it looks ok to you as well - expect logos will be back - maybe he/she can see why it doesn't show up

in the meantime can you get it from the package site - I downloaded it ok from there

---

### Post by alienjon on 2007-12-25
Ya, I downloaded it to the laptop (I'm at work right now so I can't connect to the internet through that computer) although I can't do anything else with it, I don't think (please correct me there if I'm wrong in that, I'm a Gentooer at heart and new to the debian-based distros :-p)

---

### Post by forestpixie on 2007-12-25
once you've downloaded it , dbl click it and it should be fine - if it needs to satisfy dependencies it'll be looking to go online

You might find that it says there a version on the software channel - which would be decidedly odd as you can't get it with apt-get - but hey ho it's xmas

---

### Post by alienjon on 2007-12-25
Hmm, double clicking the file only opens it in Ark. I'm not sure what the command-line version would be (I figured something starting with `deb` or maybe `dpkg` but nothing I'm seeing seems to be what I'm looking for)

---

### Post by logos34 on 2007-12-25
sudo dpkg -i <packagename.deb>

---

### Post by forestpixie on 2007-12-25
how do you get it to deal with the dependencies using dpkg -i - I thought that was the way, but it doesn't do the dependencies?

Edit - sudo apt-get install -f  did it in a roundabout  way

---

### Post by alienjon on 2007-12-25
Thanks. I figured it was something like that (I tried apt-get's 'install', but to no avail, but I figured it was something like that) Anyway, now that's installed, but my concern is still there of other packages that "don't exist" on my computer for whatever reason. Could it be a bad headers list or bad mirror for some reason?

---

