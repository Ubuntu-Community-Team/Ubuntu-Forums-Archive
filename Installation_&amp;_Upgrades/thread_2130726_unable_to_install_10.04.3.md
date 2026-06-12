---
title: "unable to install 10.04.3"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by milpas on 2013-03-30
I just put a new motherboard into my computer. (Gigabyte GA-Z77-DS3H)


I put my Ubuntu 10.04.3 cd and when it ran I got this message:
(initramfs) Unable to find a medium containing a live file system.


I have put this program from this cd on various computers and have never seen this before.


I was able to install  12.10 with no problems, but I prefer the older version with the disk utility among other differences.


Does anyone have a solution.

---

### Post by dabl on 2013-03-30
There is a problem with the optical drive or the CD -- the drive is not able to read the CD.

It is also possible there is a compatibility problem between the old optical drive and the new motherboard.

---

### Post by Azyx on 2013-03-30
Does the CD read correctly? I have often experiensed problem with the CD/CD-drives. Are the CD dirty and so on...

You can check the CD with [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Anyway are you awared that 10.04LTS don't get supported after 9-may this year? 12:10 are supported to april-2014  but 12.04 are supported untill april-2017?

---

### Post by milpas on 2013-03-30
i got the same result with a usb stick so i suspect that the problem is not cd

---

### Post by grahammechanical on 2013-03-30
> [COLOR=#000000](initramfs) Unable to find a medium containing a live file system.[/COLOR]

I do not think that there is a way around this. I had the same problem a few weeks ago with every ISO of Raring Ringtail that I tried. It was and still is under development. But the problem is now fixed. I never had an issue like that with any ISO image of Ubuntu before.

I recently installed Ubuntu Kylin 13.04 to a USB stick and things were fine until an update got stuck and I powered off. The update included a kernel update and when I booted again I got that same error message. I simply re-installed. Believe what the message says. It cannot find a live file system.

Regards.

---

