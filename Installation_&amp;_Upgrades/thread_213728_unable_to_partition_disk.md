---
title: "unable to partition disk"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by devillion on 2006-07-11
I downloaded the 64bit Desktop CD of ubuntu to install on my HP DV5140 Pavilion notebook (literally brand new) which has a AMDTurion64 processor, and i cannot install ubuntu6. I ran memtest86 for two passes, and got no errors. I checked the ubuntu CD using the tool provided, and got no errors. My hard drive works fine in the pre-installed OS (Microsoft Windows XP SP2 MCE)

I can use the CD live just fine. Sound drivers and everything else load perfectly. However, when i go into "Places > Computer", my hard drive is listed (as HDA 110gb parition), but it can not be mounted. When i double click its icon, it says "failed to mount /dev/hda using qmount".

When i run the installer, i get this same problem. I do not want to wipe my entire hard-disk, so i attempt to use the GNOME partition tool provided to partition manually. I can make changes, but when i go to apply them, i get a fantastically unhelpful error "failed to write/change /dev/hda".

Any idea what is going on? Or where i can get a more verbose error log so i know what is breaking? The only thing that i can think may be causing this is the fact that this computer shipped with two paritions. A 1gb partition called "HPRECOVERY" and a 119gb parition with NTFS that is everything else. Maybe this is why?

I read stickies but saw no discussion that helped me. Sorry if i missed something.

---

### Post by BaKsHi on 2006-07-12
I have the same exact problem as you. I also have an HP Pavilion notebook, and its a zv6000 model. I get the same stuff as described to you. I thought I'd get Ubuntu installed tonight, but I guess not.

---

### Post by defrex on 2006-07-12
I also have this problem on an HP (non-laptop). It's frustratingly nondescript.

---

### Post by orb9220 on 2006-07-12
When I had problems was my hd's were fragmented and stopped the gpart in it's
tracks.

booted to xp and ran defrag a couple of times and walla worked fine after that.

Wasn't sure if you were installing as a second OS with xp or not.

---

### Post by defrex on 2006-07-14
Well, I solved my problem; maybe what I did will help others, too.

I tried defraging twice, but it was still no good. Then I tried using [Partition Magic]("http://www.powerquest.com/home_homeoffice/products/system_performance/pm80/index.html"). While this was still no good at making the new partition, it gave me a better error message for the purposes of googling.

What I found was [this](http://forums.winforums.org/showthread.php?t=1705): that I need to run "chkdsk /f" in a windows command prompt. 

Honestly, I have no idea what function this was supposed to serve, but it worked. I loaded up the live CD and installed Ubuntu without any more problems.

---

### Post by J-Rod on 2006-07-15
It likely flagged faulty sectors, and replaced them with spare good ones that exist on anothter platter within the disk.

---

