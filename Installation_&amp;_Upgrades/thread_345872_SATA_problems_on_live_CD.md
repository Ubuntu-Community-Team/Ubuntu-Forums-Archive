---
title: "SATA problems on live CD"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by psychiccyberfreak on 2007-01-24
Ok, appearently I'm having some SATA problems on edgy. [ See the original forum post here for more info.]("http://www.ubuntuforums.org/showthread.php?t=325840")

I'm using an intel iCH8 controller on an intel board, with a seagate drive and a core 2 duo.

relevant bug comment:

[https://launchpad.net/ubuntu/+source...02/comments/99](https://launchpad.net/ubuntu/+source...02/comments/99)

> 
ICH8 SATA controller doesn't work. This is a known situation. This is

another bug and is totally unrelated to this bug.
Also found this:

> 
Q. Why Linux is not detecting or recognize my attached hard disk? How do I install Linux on SATA hard disks?

A. Go to your BIOS setup

Press F1/F2 or Del key to enter into BIOS setup

Now turn the ICH8 controller in AHCI mode

Save settings reboot system

Now Linux installer should see disk. Read this previous FAQ for more information.

[http://www.cyberciti.biz/faq/linux-s...not-recognize/](http://www.cyberciti.biz/faq/linux-s...not-recognize/)

Should I do this? I am dual booting windows here, I don't want to screw that up either.

---

### Post by psychiccyberfreak on 2007-01-25
Ok, feisty works on my PC, but it's still unstable, and I don't have a drive big enough to back up 50 gigs worth of files, so I'm going to have to wait for it to be released.

---

