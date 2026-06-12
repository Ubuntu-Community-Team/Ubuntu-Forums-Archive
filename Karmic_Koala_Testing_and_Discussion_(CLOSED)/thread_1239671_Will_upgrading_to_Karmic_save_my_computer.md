---
title: "Will upgrading to Karmic save my computer?"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by stevejesus on 2009-08-13
Over 2 months ago my computer stopped booting.  It failed when trying to mount my swap partition.  I fixed the swap from the Jaunty live CD and now it won't load network modules.  This happened after an update.

When I bought the laptop, Gutsy was new.  Since, I have upgraded to Hardy, Intrepid, and now Jaunty.  

From grub I have tried booting from the three most recent kernels in the list, .11, .12, .13.

Save me!  I cannot go another day using my wife's laptop.

Will an early upgrade to Karmic make my laptop boot?  How will I upgrade?

---

### Post by Psicolonia on 2009-08-13
I would recomend a full install of jaunty. A new install.

Backup all your files and start from a newly fresh instalation.

Are you sure it's a software issue and not a HardDrive problem?

---

### Post by raymondh on 2009-08-13
as for me, I'll re-install 8.04 LTS because it previously worked ;)

---

### Post by stevejesus on 2009-08-13
I ran Spin-rite on the hard disk and passed all the tests.  This is the only hard-drive I have these days.  I cannot backup.  Must save my installation:(

---

### Post by Mark Phelps on 2009-08-14
> **stevejesus said:**
> Over 2 months ago my computer stopped booting.  It failed when trying to mount my swap partition.  I fixed the swap from the Jaunty live CD and now it won't load network modules.  This happened after an update.

Sounds suspiciously like a failing hard drive.
> 
When I bought the laptop, Guty was new.
Sounds like an "old" drive, and laptop drives wear out a lot sooner than desktop drives.  Again, sounds like a failing drive.
> 
From grub I have tried booting from the three most recent kernels in the list, .11, .12, .13.
Have you tried booting into recovery mode?
> 
Will an early upgrade to Karmic make my laptop boot?
No reason why it would, especially if it's failing hardware.  And, there's no good reason to "upgrade" to an alpha version of a release when the current version is stable.

---

### Post by stlsaint on 2009-08-14
so to answer your question...NO and upgrade to KARMIC will not fix your problem! try and older version from another livecd...if an older version doesnt work and a newer version doesnt work than that will prove that its not the software but the hardware/hdd!!

---

### Post by stevejesus on 2009-08-14
Oh dear...

My hard disk seems to be fine however.  I trust spin-rite.  I can boot into recovery mode, but once I am there I have no idea what I should be doing...

---

### Post by stlsaint on 2009-08-14
so once you get into safe mode can you install from there?

---

### Post by presence1960 on 2009-08-14
boot from the Ubuntu live CD, choose "try Ubuntu without any changes". When the desktop loads download the Boot Info Script 0.32 from the link on my signature line to your desktop. Then open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will produce a file RESULTS.txt on the desktop. Paste the entire contents of that file back here. This will give us a lot of info about your setup & boot process.

---

