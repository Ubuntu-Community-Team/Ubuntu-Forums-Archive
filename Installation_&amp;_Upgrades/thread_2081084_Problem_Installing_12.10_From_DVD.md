---
title: "Problem Installing 12.10 From DVD"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by brantpadams on 2012-11-05
Hey guys, hope I can get some help.

I burned a copy of 12.10 i386, 32-bit, onto two different dvds and I get stuck on the "saving installed packages" part of the installation every time, on both discs. 

I am trying to do a fresh install from 12.04, mainly because I have been having problems trying to load my update manager. Simply put, it won't open. This is the same story with synaptic. I've tried finding solutions for these problems and after finding nothing I decided to upgrade, but now I'm having this problem. 

I haven't been able to find similar problems to mine so I'm hoping I can get some help. I'm something of a newbie with Linux, but I'm not completely illiterate so I should be able to keep up with any instructions. 

Please let me know if more info is needed and I would be happy to provide. Thanks in advance.

---

### Post by 2F4U on 2012-11-06
Did you verify the checksum of the downloaded iso file? The download may be corrupt, so burning it on disk would do no good.

---

### Post by brantpadams on 2012-11-06
I probably overlooked that step. I'll definitely try that a little later. I've usually always booted from a usb drive in the past, but all I have on hand right now are DVDs. 

Would you say that one or the other is more reliable?

---

### Post by darkod on 2012-11-06
Burn the DVDs at very low speed (same as with CDs). Remember that when burning DVD the 4x is much more faster than 4x with a CD.

I burn CDs for OS install at 8x or 10x max (depending how low the CD can go). For a DVD I wouldn't use more than 4x even better 2x, and most DVDs these days would default to 16x if you don't change it.

It lasts few minutes more but makes much better install media.

Definitely check the ISO mdsum, and if you need to redownload try to do it from torrent since it checks for corruption during download.

---

### Post by brantpadams on 2012-11-06
Thanks for the tip.

Where would you suggest I download a torrent? I couldn't find a link to any off of Ubuntu's main page.

---

### Post by uclugLee on 2012-11-07
I'm having a very similar issue.  I have downloaded the imaged a few times and verified the checksums, and burned them at a slow speed.  I can boot from the live dvd and even install.  However, upon reboot, all I get is a flashing cursor in the upper left of the screen.  I also tried two different hard drives.

---

### Post by darkod on 2012-11-07
If we are talking about the standard desktop live cd, which is now bigger than 700MB so you need to burn it on a DVD, all the links including for torrent are here:
[http://releases.ubuntu.com/quantal/](http://releases.ubuntu.com/quantal/)

As for a real (big) DVD release, not sure if it has option for torrent and I think it's not released for 12.10 yet. Not even sure it will be released.

A flashing cursor up left might mean video issues or also a broken grub2 install. You can try running boot-repair from live mode and see if it helps by reinstalling grub2:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by brantpadams on 2012-11-07
Sorry to report that after a fresh install and a fresh burnt DVD, the install still gets stuck on saving installed packages. 

I have yet to try installing off a usb drive, and hopefully that will work. I'm curious as to why this won't install properly.

---

