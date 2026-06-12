---
title: "gimp2.0-dev dependancy trouble"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by DirtDawg on 2007-01-27
I'm trying to install a GIMP plug-in that allows for manipulating multiple files. According to the [home page]("file:///home/dirtdawg/installs/dbp-1.1.5/dbp.html"), I need the gimp-devel packages for compiling.

When I try to install libgimp2.0-dev, I get this:
```
libgimp2.0-dev:
 Depends: libgtk2.0-dev but it is not going to be installed
```

But when I try to install libgtk2.0-dev, i get this:
```

libgtk2.0-dev:
 Depends: libxcursor-dev but it is not going to be installed
 Depends: libxfixes-dev but it is not going to be installed
```

Then, when I try to install libfixes-dev I get:
```
libxfixes-dev:
  Depends: libxfixes3 (=1:3.0.1.2-0ubuntu3) but 1:4.0-0ubuntu1 is to be installed
```

My sources.list is as follows:
```

deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## I put this in for AIGLX and Beryl
#deb http://ubuntu.beryl-project.org dapper main
```

What am I missing?

---

### Post by disturbedite on 2007-01-27
this means you need to get a version of libxfixes lower than version 1.4.x.  you can grab it here:
[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfixes/](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfixes/)
try to install it and then give it a go.  hopefully it doesn't conflict with anything newer...

---

### Post by DirtDawg on 2007-01-28
> **disturbedite said:**
> this means you need to get a version of libxfixes lower than version 1.4.x.  you can grab it here:
[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfixes/](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfixes/)
try to install it and then give it a go.  hopefully it doesn't conflict with anything newer...

Thanks for the response. I milled it over a bit and decided against installing an older version of libxfixes as I'm not keen on (possible) breakage. Instead, I downloaded imagemagick from synaptic and wrote a crude Python script to do the heavy lifting. Worked like a champ.

---

### Post by disturbedite on 2007-01-28
> **DirtDawg said:**
> Thanks for the response. I milled it over a bit and decided against installing an older version of libxfixes as I'm not keen on (possible) breakage. Instead, I downloaded imagemagick from synaptic and wrote a crude Python script to do the heavy lifting. Worked like a champ.

whatever works for you.  but you could have just downloaded the appropriate package, and then checked the properties of the package.  it would tell you there what (if anything) it conflicts with.  at least you can do this in kubuntu, i'm not sure about ubuntu.  you right click on the deb package and go to Package Menu -> Show Package Info...
but it was only a suggestion and you did your thing.  no biggie.

---

### Post by DirtDawg on 2007-01-29
> **disturbedite said:**
>   it would tell you there what (if anything) it conflicts with.  at least you can do this in kubuntu, i'm not sure about ubuntu.  you right click on the deb package and go to Package Menu -> Show Package Info...


I didn't know about this. Extremely useful. Unfortunately there is no Package Menu on the right-click in Gnome. I am looking for a Gnome equivilant now. Thanks again.

---

### Post by DirtDawg on 2007-03-06
This problem has reared its ugly head again as I need libgtk2.0-dev to compile GTKpod with mp4 support.

Any other input about this? I never found a "show package info" equivalent.

---

