---
title: "Install Ubuntu *from within a running linux system*?"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by d11wtq on 2006-09-12
Hi,

I have two 300GB hard disks in my system in the office.

One of these is completely empty, and the other has Linux on it from which I am booted into my system now (ArchLinux -- it really sucks).

Is there any way I can install Ubuntu onto the second disk ready to reboot cleanly into my new system?  I ask so that I can carry on working whilst the install goes on and pretty much update grub then reboot into Ubuntu.

I have tried mounting the image as a loop device but I have no idea what to do from there.

(I'm not looking user mode linux if anybody suggests that :P  I already have that running).

Cheers,

d11

---

### Post by navilon on 2006-09-12
Try:

[http://www.vmware.com](http://www.vmware.com)
[http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)

---

### Post by d11wtq on 2006-09-12
Hi thanks but what I actually meant was to do the *real* install inside of linux, onto a second hard disk, then reboot into that new linux install.

I'm sure it must be possible because I do it with Gentoo regularly due to the way the gentoo install works but I can't figure out what I need to run on the ISO image I have mounted as loopback in order to start to installer running.

Hints? :)

---

### Post by navilon on 2006-09-12
Hmm, well you chould do chroot while your under the live ubuntu CD.

May I ask what company you work for that has linux as its main OS?

---

### Post by NewbieLearnLinux on 2006-09-12
the LiveCD has required the user to install "inside Linux". If you wanna install "outside" , you may download the InstallCD at Ubuntu's ISO download section...

---

### Post by d11wtq on 2006-09-12
Heh... I work for the council and I choose my own OS.  Nobody was going to make me use windows.  I'm a programmer writing for web apps on linux servers so I need this environment anyway.

The Live CD... once I'm chrooted into that I still have the same problem don't I?  Or does the Live CD contain an installer? :)  I've never used it before.

---

### Post by d11wtq on 2006-09-12
> **NewbieLearnLinux said:**
> the LiveCD has required the user to install "inside Linux". If you wanna install "outside" , you may download the InstallCD at Ubuntu's ISO download section...

Nice one cheers :)

I'm back at home now but I have shell access to my computer at work so I'll give it a go remotely :)

---

