---
title: "Blank Screen After Menu During Install"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by xBeldin on 2007-08-01
Hi, I am new to Ubuntu and Linux, I've been trying to Install Feisty Fawn on my desktop and am failing.  I get it to boot to the main menu where I choose to install it and it shows some scrolling text then it just goes to a blank screen or a blank screen with a single cursor.  Just like in this thread [here.]("http://ubuntuforums.org/showthread.php?t=419351&highlight=blank+screen+during+install")

My system specs are:
Intel P4 HT 2.4Ghz
1 GB PC3200 RAM
nVidia eGeforce 6200 LE
ASUS P4P800 Motherboard

I have tried the LiveCD and the Alternate Text Based cd, each downloaded through http and bittorrent and burned as an iso file.  So I've tried 4 different discs and still the same.

Any Idea?

Thanks

---

### Post by Pumalite on 2007-08-01
Do you get a command line? Did you try all the posted possible solutions in the thread (link) you provided? What were the results?

---

### Post by xBeldin on 2007-08-01
I do not get a command line and yes I did try all the options in that thread and nothing was different it still acted the same.

---

### Post by Pumalite on 2007-08-01
Then is time to do md5sum on your iso ( compare it). Burn at 4x. Check CD for corruption before install. Download a new iso if necessary. Torrent better than HTTP or FTP. I suspect your graphics card, but the Alternate CD should give you a command line at least.

---

### Post by xBeldin on 2007-08-02
I burned both the LiveCD and the alternate at 4x and I still get the same exact thing.

---

### Post by Pumalite on 2007-08-02
Make sure you burn the 'iso' as an 'Image'

---

### Post by xBeldin on 2007-08-02
Yeah I did that for sure.  I'll try a different burning software today when I get home.

---

### Post by xBeldin on 2007-08-02
I burned it with a different software and checked them all with md5sum and they're all fine but still do the same thing.  I loaded the disks on my work computer and it all works fine.  What can I do?

---

### Post by Pumalite on 2007-08-02
I'm stumped. Your hardware looks ok to me. You should have no problems. Maybe someone with fresh ideas?

---

### Post by xBeldin on 2007-08-02
I have also tried 6.06, 6.10, and Xubuntu.  They all did the same thing except 6.06 LiveCD displayed: "Uncompressing Linux... Ok, booting the kernel." Then it froze with a cursor beneath it flashing.

---

### Post by Pumalite on 2007-08-02
As a last resort you could try Zenwalk: [http://www.zenwalk.org/](http://www.zenwalk.org/) or DamnSmallLinux: [http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)
Just to see what your computer will do with those.

---

### Post by Takster on 2007-11-27
> **xBeldin said:**
> ...I get it to boot to the main menu where I choose to install it and it shows some scrolling text then it just goes to a blank screen or a blank screen with a single cursor...

...My system specs are...

**ASUS P4P800 Motherboard**

I have tried the LiveCD and the Alternate Text Based cd, each downloaded through http and bittorrent and burned as an iso file.  So I've tried 4 different discs and still the same.

Any Idea?

Thanks

Same problem here. The fix? update p4p800 BIOS to the latest version possible. Then it works. ;)

> 
P4P800 Beta BIOS 1021.006
Latest beta BIOS.

---

