---
title: "I just went through a nightmare because the Live iso lacks a text installer."
date: 2009-01-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-01-19
My situation: My Jaunty Live USB instance works but is buggy as I run it. I had a rooted Firefox running, but Ubiquity didn't want to work, period.

My solution, running Ubuntu on RAM and fixing the problem: 

1. Pulled out the stick, reinserted, forced dismount, and formated it.

2. Downloaded new daily iso and probono's liveusb tool (usb-creator is horrible, but would've worked) to my laptop's empty hard drive.

3. Created a new Live USB image on stick.

4. ?

5. Profit.


Moral of story: **WHY ISN'T THE TEXT INSTALLER A PART OF THE LIVE ISO?!?!?**

---

### Post by jrusso2 on 2009-01-19
A text install is part of the alternative iso, but I am not sure there is one for Jaunty yet as the distro has not be finalized.

---

### Post by RAOF on 2009-01-19
> **Starks said:**
> ...
Moral of story: **WHY ISN'T THE TEXT INSTALLER A PART OF THE LIVE ISO?!?!?**

Because the text installer (debian-installer) is totally different to Ubiquity.  In particular, it doesn't do what Ubiquity does, which is basically just copy the LiveCD to the target partition.  Instead it basically runs a debootstrap - unpacks, from .debs, a minimal Debian system, then chroots in and installs, using dpkg, the base system.

The upshot is: we'd need to add the *entire* Alternate CD to the LiveCD in order to make that work.  That's obviously not going to happen.

---

### Post by Starks on 2009-01-19
I understand that, but this is not the first time that I've been in a situation with a buggy live usb image.

If Ubiquity fails, I need something to fall back on. 


(P.S. Fedora even allows for a using their DVD iso for Live USB.)

---

### Post by cariboo on 2009-01-19
There are alternate install cd's for Jaunty. Have a look [here]("http://cdimage.ubuntu.com/releases/jaunty/alpha-3/").

Jim

---

### Post by BwackNinja on 2009-01-19
I believe the DVD has both.

---

### Post by Starks on 2009-01-19
cariboo, I know that.

I also know how to mount the alternate iso on my USB key.

My issue is that I don't want to be forced to choose between having a bootable Internet browser for problem solving and a reliable installer.

---

### Post by inportb on 2009-01-20
> **BwackNinja said:**
> I believe the DVD has both.

indeed.

---

### Post by Starks on 2009-01-21
Is it possible to boot the DVD iso on a USB flash drive?

---

### Post by plun on 2009-01-21
> **Starks said:**
> Is it possible to boot the DVD iso on a USB flash drive?

Yup with UNetbootin, great tool !

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Use the second option with a disk image.

With the first option you directly can choose a daily iso and automagic download and make a bootable USB stick.

gparted works just fine for formatting the stick.

---

