---
title: "Transcode/DVD::Rip Nightmare"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by erikcore on 2005-10-14
Has anyone figured out how to install transcode on Breezy?

I should mention, my errors in synaptic looked like this...

transcode:
  Depends: libpng12-0 (>=1.2.8rel-4) but 1.2.8rel-1ubuntu3 is to be installed
  Depends: libstdc++6 (>=4.0.2) but 4.0.1-4ubuntu9 is to be installed

---

### Post by erikcore on 2005-10-14
I should add that I started trying to track down and install/update the dependencies that were named in the error messages.  This only led to a dead end with synaptic reporting broken packages and two things that depend on each other to be installed, but without one or the other, neither can be installed.

Someone please help me with this.

---

### Post by shenki on 2005-10-14
not sure how co- dependencies work, but if you do a 'apt-get install prog1 prog2', does that work?

---

### Post by erikcore on 2005-10-14
I haven't tried that, basically because I've been hunting down individual deb packages into order to upgrade beyond what is available through synaptic.

---

### Post by Nolgthorn on 2005-10-16
Is there no solution to this yet? This is the farthest I've gotten after reading everything on this forum.

In my sources.list I've added/changed this part:

> # Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse

# Extra
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

When I try and install dvdrip I get "Depends: transcode (>=2:0.6.14) but it is not installable". There is no solution. Huh. I don't mean "huh" I mean "grrrrr."

---

### Post by hsolis on 2005-10-24
Exatrly the same problem
The following packages have unmet dependencies:
  dvdrip: Depends: transcode (>= 2:0.6.14) but it is not installable

help!!!
h

---

### Post by essexman on 2005-10-24
[quote=Nolgthorn]Is there no solution to this yet? This is the farthest I've gotten after reading everything on this forum.

In my sources.list I've added/changed this part:



When I try and install dvdrip I get "Depends: transcode (>=2:0.6.14) but it is not installable". There is no solution. Huh. I don't mean "huh" I mean "grrrrr."[/quote]

I'm installing transcode and dvdrip with no problem, via synaptic with this sources.list:
```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## Hoary Extras (October 16 2005: Breezy Extras are not curently available)
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

if it works for me, it should work for everyone.

Best of luck

---

### Post by freedom on 2005-10-26
well I have 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
in my sources list but only thing I can install about transcode is transcode-doc package. :confused:

---

### Post by essexman on 2005-10-26
[quote=freedom]well I have 
deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-extras main universe multiverse restricted
in my sources list but only thing I can install about transcode is transcode-doc package. :confused:[/quote]

Have you tried adding multiverse to the standard breezy archive?

```
 deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse 
```

I just looked in the [archive]("http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode_1.0.1-0.0ubuntu1_i386.deb") and it is there.

---

