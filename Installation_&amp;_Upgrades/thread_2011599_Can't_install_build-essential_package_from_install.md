---
title: "Can't install build-essential package from installation DVD"
date: 2012-06-27
forum: Installation &amp; Upgrades
---

### Post by rb00012 on 2012-06-27
I'm running dual-boot windows 7/ubuntu 12.04 and it's a fresh install (from the standard Ubuntu CD). The computer I'm using also has no network connection so all installs have to be from tar files or similar that I can burn to CD/DVD. 

I need to install cmake, which requires gcc, dpkg-dev etc, and I have always done this using ```
sudo apt-get install build-essential
```I've tried adding an installation DVD to my `/etc/apt/sources.list' using ```
sudo apt-cdrom add
``` which works as expected and the new source shows up (I've also made sure the `cd source' box is ticked in update managers settings). I've then also tried the following before installing from the DVD:
```
sudo apt-get update
sudo apt-get upgrade
```However it will not work. As expected, I receive errors saying that the (internet based) source repos cannot be contacted, so I've also tried it with these extra repos disabled. The error I then receive is something like (from memory, sorry I can't get the exact text here)```
package build-essential is not available, but is referred to by another package
```Either it's not reading the DVD repository properly, or build-essential is not on the DVD (I checked the extra packages on the DVD, but couldn't find the build-essential package anywhere). I suppose my questions are 
    1) Is the build-essential package on the DVD for installation AFTER a CD install?
    2) If not, can I get a .tar version with all the dependencies? And why is build-essential not on the DVD any more?

Please try to advise me without resorting to `re-install ubuntu from the DVD'. If I have to re-install from the DVD so be it, but I'd really rather not. Any help is greatly appreciated.

Cheers,

RIch

---

### Post by Mark Phelps on 2012-06-27
Reinstalling from the DVD is not going to fix the problem.

Common fallacy folks have is presuming that the DVD version has LOTS of packages when, in fact, all it has over the CD version is language packs.

Ubuntu, like most Linux distros, is designed to work WITH persistent internet connections -- when installing stuff.

I was going to refer you to the section in the link below, but when I clicked that link to see what it had, I got an error:

[https://help.ubuntu.com/community/InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware")

Installing without an Internet connection is going to be VERY tedious and difficult -- as you will attempt to install one package and it will complain that you don't have all the dependencies.  You go grab those dependencies, try again -- and find even more dependencies.  This will go on and on until you have ALL the dependencies.

---

### Post by rb00012 on 2012-07-02
Ok thanks for that, I realised that the DVD mostly has extra language packs, but was hoping it would also have build-essential as previous releases of Ubuntu included it.

I've been down that route before, and would rather not spend days going back and forth to get a few MB's here and there. It seems Ubuntu is fine for my online work but not an offline install. Do you know of any other flavours of Ubuntu (or linux) that do include build-essential by default?

Thanks again for your help,

Rich

---

