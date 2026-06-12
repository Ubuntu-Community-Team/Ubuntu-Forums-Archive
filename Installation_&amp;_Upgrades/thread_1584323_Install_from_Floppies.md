---
title: "Install from Floppies?"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by Name141 on 2010-09-29
Is it possible to install using floppies?  Perhaps a floppy installer that'd be like the MinCD  and download most of the data?

My CD-RW just went belly up (quit working) and the machine is 1998 so no USB boot.

---

### Post by mörgæs on 2010-09-29
It is not possible for Ubuntu, but there are other distros which boots from a floppy. I have not tried any of them, though.

Maybe time for new hardware in general? A used 3-4 years old machine should not cost much.

---

### Post by ronnielsen1 on 2010-09-29
I've used UBCD to boot from usb on older computers.

---

### Post by Name141 on 2010-09-29
> **mörgæs said:**
> It is not possible for Ubuntu, but there are other distros which boots from a floppy. I have not tried any of them, though.

Maybe time for new hardware in general? A used 3-4 years old machine should not cost much.

I've had the machine for years, and only the CD drives have died before anything else.  I'm not putting it to pasture till the HD goes out or something.

> **ronnielsen1 said:**
> I've used UBCD to boot from usb on older computers.

I don't see what a CD is going to help if the CD drives is what are broken :confused:

---

### Post by confused57 on 2010-09-29
I believe Debian Etch supports installing from floppies:
[http://archive.debian.org/debian-archive/debian/dists/etch/main/installer-i386/20070308etch7/images/floppy/](http://archive.debian.org/debian-archive/debian/dists/etch/main/installer-i386/20070308etch7/images/floppy/)

I'm not sure if the latest Debian release does.  You should be able to Google & find instructions for installing from floppies.

---

### Post by Name141 on 2010-09-29
> **confused57 said:**
> I believe Debian Etch supports installing from floppies:
[http://archive.debian.org/debian-archive/debian/dists/etch/main/installer-i386/20070308etch7/images/floppy/](http://archive.debian.org/debian-archive/debian/dists/etch/main/installer-i386/20070308etch7/images/floppy/)

I'm not sure if the latest Debian release does.  You should be able to Google & find instructions for installing from floppies.

etch is no longer supported officially.  I guess I could install then install Lenny ?

---

### Post by confused57 on 2010-09-29
If you can get Etch to install, maybe you can change your sources.list from etch to lenny, then do a dist-upgrade?

Maybe you can take the HD out, put it in another computer or external enclosure, then install a distro(depending on the specs of your old pc).

---

### Post by Name141 on 2010-09-29
> **confused57 said:**
> If you can get Etch to install, maybe you can change your sources.list from etch to lenny, then do a dist-upgrade?

Maybe you can take the HD out, put it in another computer or external enclosure, then install a distro(depending on the specs of your old pc).

I think maybe it's more time to take it out to pasture.

It's a Pentium2 450MHz, 320MB SDRAM, 10GB EIDE.

Or maybe just put zsnes and some emulators on it and leave it as is after taking out the NIC.  Perhaps selling the USB2 PCI card, etc.

---

### Post by gordintoronto on 2010-09-29
Have a look at Plop Boot Manager. My reading is that it can create a boot floppy which can switch to a flash drive. (I can't test it; I don't have a floppy drive in my computer.)

With your computer's specs, you might be able to run Lubuntu, but it might be slow.  There are two distros which might work better: Damn Small Linux (DSL) or Slitaz.

DVD writers cost around $20 these days, if you are considering continuing to use the old computer.

---

### Post by mörgæs on 2010-09-29
It is amazing how die-hard Damn Small Linux is in this forum. Its development ground to a halt long time ago, so though it might install and run on this machine, there are most likely lots of security holes in it. 

Slitaz or Lubuntu are good options. There are other here:

[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by mocoloco on 2010-09-29
Found this [https://help.ubuntu.com/community/Installation/WithFloppies]("https://help.ubuntu.com/community/Installation/WithFloppies"), it's old so in your shoes I wouldn't just dive in but probably something along it's lines will work.

---

### Post by mörgæs on 2010-09-29
Whoa, this is old-school. It ends with installing the 2.6.10-kernel, which was used in Ubuntu 5.04. 

If anyone tries with 10.04, please post the results.

---

### Post by Name141 on 2010-09-29
> **gordintoronto said:**
> Have a look at Plop Boot Manager. My reading is that it can create a boot floppy which can switch to a flash drive. (I can't test it; I don't have a floppy drive in my computer.)

With your computer's specs, you might be able to run Lubuntu, but it might be slow.  There are two distros which might work better: Damn Small Linux (DSL) or Slitaz.

DVD writers cost around $20 these days, if you are considering continuing to use the old computer.

> **mörgæs said:**
> It is amazing how die-hard Damn Small Linux is in this forum. Its development ground to a halt long time ago, so though it might install and run on this machine, there are most likely lots of security holes in it. 

Slitaz or Lubuntu are good options. There are other here:

[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)


I don't see putting any money in to the system when this one is a E2160 and Radeon 4670, and I need portal2 next Feb :P

I was thinking I might try to sale some parts and get a E5400 or a cheap Core2Duo for this one.  I dunno.. I don't see putting any money in to the old machine.  Right now it's got Peppermint, and I saved 5.2 GBs when I took off XP with gparted.

I guess I'll keep peppermint one on it.

---

