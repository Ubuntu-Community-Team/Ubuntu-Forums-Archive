---
title: "Hard Drives not seen - P5Q"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by pigeonjim on 2008-09-11
I have been trying to install hardy on my new system but the install does not see my Sata hard drive. When I boot from the live cd the file manager can not see my hard drive either.
I can not change to ahci in the bios because i already have xp installed (which i use for games) and I didnt do the F6 thing because I dont have a floppy drive. I have tried and failed to use many methods to change my xp to ahci without reinstalling and I have been unsuccessful.
Is there any other way to get Ubuntu to recognise my hard drive so I can install?

---

### Post by dstew on 2008-09-11
Try the Alternate Install CD. It uses a text-based interface, and has a different installation program. Maybe the system on it will recognize the drive.

---

### Post by pigeonjim on 2008-09-11
> **dstew said:**
> Try the Alternate Install CD. It uses a text-based interface, and has a different installation program. Maybe the system on it will recognize the drive.

Thank You

My linux skills are basic. Is this easy to use?

---

### Post by pigeonjim on 2008-09-11
Anyone else got any ideas? I prefer to use Ubuntu as my main OS like I did before I built this system but at the moment im using xp :(

---

### Post by Horizon on 2008-09-20
Hi, Did you find your answer?

Since this is the first google result I got, I thought I'd update it.

To fix this problem you need to go into your bios and go into "storage configuration" and change IDE to AHCI.

---

### Post by pigeonjim on 2008-09-20
> **Horizon said:**
> Hi, Did you find your answer?
To fix this problem you need to go into your bios and go into "storage configuration" and change IDE to ACHI.

In my original post I state that I am unable to do this. I need another way. A good OS should be able to use my sata drive without me changing this setting anyway.

---

### Post by Horizon on 2008-09-20
> **pigeonjim said:**
> In my original post I state that I am unable to do this. I need another way. A good OS should be able to use my sata drive without me changing this setting anyway.
Woops, sorry, missed that.

I just did a repair install of windows.
Decided this wasn't worth the hassle for just leaving it to reinstall some files for half an hour and downloading a few windows updates.

Your games should be fine.

---

### Post by blackpaw on 2008-11-24
Installed Ubuntu 8.10 on my P5Q-E's SATA drive without a single problem.

However, I did switch SATA config from IDE to EHCI in BIOS.

Useful post that helpded me is here: 
[http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html]("http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html")


Regards


Andreas

---

