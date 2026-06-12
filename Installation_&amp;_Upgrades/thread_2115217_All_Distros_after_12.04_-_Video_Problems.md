---
title: "All Distros after 12.04 - Video Problems"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by danxaz on 2013-02-12
I have had success installing every ubuntu distro until 12.10.  Now when I try to use 12.10, either Ubuntu, Xubuntu, Lubuntu, etc. I have black and red bars running horizontally on the screen.  I can still see the desktop and the everything behind the bars and it seems to be running smoothly.  I even tried running the latest version of Fedora with the same outcome.  It happens whether running the system from a live usb or full install.  I have a Gateway Laptop MX3228, with Intel Celeron M 1.5 GHZ. Display is 1280 x 768.  Please let me know if you need more info.  Thanks!

---

### Post by dino99 on 2013-02-12
if its a fresh install:
- boot into recovery mode , then watch logs (.xsession-error; dmesg; xorg.0.log)
- or test with some boot option
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

if its a rolling dist-upgrade
- check that you dont have a xorg.conf (/etc/X11/xorg.conf) as now the kernel directly deal with X; and an oldish xorg.conf often disturb the system

you can also google a bit around your MB model + linux/ubuntu

---

### Post by offgridguy on 2013-02-12
> **danxaz said:**
> I have had success installing every ubuntu distro until 12.10.  Now when I try to use 12.10, either Ubuntu, Xubuntu, Lubuntu, etc. I have black and red bars running horizontally on the screen.  I can still see the desktop and the everything behind the bars and it seems to be running smoothly.  I even tried running the latest version of Fedora with the same outcome.  It happens whether running the system from a live usb or full install.  I have a Gateway Laptop MX3228, with Intel Celeron M 1.5 GHZ. Display is 1280 x 768.  Please let me know if you need more info.  Thanks!
This sounds more like a hardware issue.

---

### Post by danxaz on 2013-02-12
I suspected a hardware issue also, since it's only started with the latest releases.  As another bit of information, whenever I do a fresh install, I always wipe the hard drive with DBAN first.  I have learned that if I try to install over other distros, I tend to have problems.   Can you clarify, what I need to do in recovery mode?  I'm not sure I understand.  Thanks.

P.S. If it is a hardware issue, what do I do?

---

### Post by offgridguy on 2013-02-12
> **danxaz said:**
> I suspected a hardware issue also, since it's only started with the latest releases.  As another bit of information, whenever I do a fresh install, I always wipe the hard drive with DBAN first.  I have learned that if I try to install over other distros, I tend to have problems.   Can you clarify, what I need to do in recovery mode?  I'm not sure I understand.  Thanks.

P.S. If it is a hardware issue, what do I do?
Recovery mode is something i have no experience with yet, so i can't advise on that.   Since you have the same issue using both
live USB or full install, that likely rules out a hard drive problem.  It sounds more like the monitor is misbehaving.

Here in our part of the world, most tech repair shops will do
an inspection and repair estimate at no charge, so you can
decide from there.

---

### Post by Mark Phelps on 2013-02-13
Your Gateway appears to be using an S3 Unichrome video chip.  That's pretty old and support for it is minimal.  Could very well be that the default drivers don't work with the new X-server version present in Ubuntu 12.10.

---

