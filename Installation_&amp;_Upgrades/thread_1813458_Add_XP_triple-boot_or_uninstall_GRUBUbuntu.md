---
title: "Add XP triple-boot or uninstall GRUB/Ubuntu?"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by x96 Eminem on 2011-07-27
Hi, I want to either triple-boot with Windows 7, Ubuntu 10.04, and Windows XP (7 installed first) or uninstall Ubuntu and GRUB completely so I can install XP beside 7... but not sure how, and cannot find a tut for the life of me. Yeah yeah I know GIYF but today it's not. :(

Compaq Presario CQ60 Windows 7 Home Premium 64-bit
2 GB RAM 900 @ 2.20 2.19 GHz Processor

lemme know if u need more info :) TYIA!!

---

### Post by inertself on 2011-07-27
If you're starting from scratch, I would partition your drive(s) manually with the ubuntu live cd (gparted).  Make one NFTS for your xp, and another NFTS for your windows 7.  Be sure to make one of those big enough to accommodate your ubuntu install later (it's easier to let ubuntu add the partitions for you then to manually set them up, in my opinion).  Then install xp on one first, as I think windows 7 would recognize the xp install better than the other way around.  Install windows 7 next, then make sure that they both boot up properly, etc.  Then go ahead and add your ubuntu install to one of the windows partitions, it will do everything automatically and put in grub, you know the drill.  

Let me know how it goes.

--- I would keep ubuntu, it comes in handy when something goes wrong with windows, and it's good for most every day computing.  You know you always have one safe OS.  not to mention transmission is built in :)


Oh and make your windows 7 partition a minimum of 60GB, I ran out of space on my 40GB SSD in no time.

---

### Post by x96 Eminem on 2011-07-27
> **inertself said:**
> If you're starting from scratch, I would partition your drive(s) manually with the ubuntu live cd (gparted).  Make one NFTS for your xp, and another NFTS for your windows 7.  Be sure to make one of those big enough to accommodate your ubuntu install later (it's easier to let ubuntu add the partitions for you then to manually set them up, in my opinion).  Then install xp on one first, as I think windows 7 would recognize the xp install better than the other way around.  Install windows 7 next, then make sure that they both boot up properly, etc.  Then go ahead and add your ubuntu install to one of the windows partitions, it will do everything automatically and put in grub, you know the drill.  

Let me know how it goes.

--- I would keep ubuntu, it comes in handy when something goes wrong with windows, and it's good for most every day computing.  You know you always have one safe OS.  not to mention transmission is built in :)


Oh and make your windows 7 partition a minimum of 60GB, I ran out of space on my 40GB SSD in no time.

I would do that if I could. I'm not even close to starting from scratch although I want to... Not sure tho. Need to find my 7 install disk that came with my laptop. then back everything up to my 500GB WD HDD... Thanks so much tho! So install Xp, then 7 then Ubuntu/GRUB and GRUB will detect 7 and XP?

---

### Post by oldfred on 2011-07-28
Windows does not make it quite that easy. Windows can only boot from one (active or boot flag) partition and literally moves the boot files from second installs to the first install.  Grub then only boots the one windows and windows gives you a choice of which windows to use.

To get each MS to have its own boot loader make a  second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

