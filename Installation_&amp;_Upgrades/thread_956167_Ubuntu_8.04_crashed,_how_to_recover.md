---
title: "Ubuntu 8.04 crashed, how to recover"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by svkndv on 2008-10-22
My 8.04 ubuntu installation is almost 3 months old. I have installed it on a vista machine as dual booting. I have installed Ubuntu on my second disk. Unfortunatly i abandoned using vista since last 3 months. My productive work and snaps of my kids/family all were stored on Ubuntu partition. two days back Ubuntu crashed it is not responding after 2-3% of booting progress bar.If i wait for longer i could see an error "segmentation fault" abnormal exit.

I tried  to reinstall and tried searching different tricks adviced by various forums. My vista partition is working fine. can anyone tell me how i can recover the data from my ubuntu disk. I lost the hope of recovering my operating system. if anyone can help i can try that as well(recovering OS).

System - Dual core Pentium
       - 512 MB Nvidia GPU
       - Hard Disk 320 GB
       - RAM 2 GB

---

### Post by chrisamiller on 2008-10-22
What kind of partition is your Ubuntu installed on?  EXT3?  If that's the case, then you can use IFS to mount that partition as a drive in Windows and access your files.  [http://www.fs-driver.org/](http://www.fs-driver.org/)

Without further information, it's pretty hard to diagnose your problem, so my suggestion would be to copy your data to the windows partition, then reformat and reinstall ubuntu from scratch.  Wait a few days and you can even go straight to Ubuntu 8.10.

---

### Post by sparvik on 2008-10-22
If the HDD passes a self test in the BIOS then you could simply use a live CD like Knoppix or you Ubuntu Live-CD to get into an OS that recognizes your Ubuntu file system format. Then transfer the files over to you Vista drive and do the reinstall like the post above me says.

---

### Post by svkndv on 2008-10-23
I have installed it on a seperate hard disk not sure whether it is ext3.self test is passed, vista manager show the disk as healthy but unable to browse the disk from vista.
What is mean by segmentation fault, why ubuntu is waiting so long ("15 min) to display an error message while booting?

---

### Post by sparvik on 2008-10-23
This won't solve your problem but it will define the **segmentation fault** thing.  

[http://en.wikipedia.org/wiki/Segmentation_fault]("http://en.wikipedia.org/wiki/Segmentation_fault")

Perhaps if you where to explain what changes were done before the crash. Installs, updates, Swap partition changes or maybe even a read/write change issue.  I don't know why though it would take 15mins for it to figure out that it can not access what it needs to, unless it is just froze and finally gets that error when it tries to hibernate.

---

### Post by svkndv on 2008-10-23
One more thing i observed just now. Memtest option shown on the ubuntu boot menu. Error is "selected item cannot fit into memory"
I dont think 2 GB RAM is not sufficiant for this operation

---

### Post by Bucky Ball on 2008-10-23
Try booting into Vista and doing a clean shutdown. Then boot into Ubuntu and let us know.

---

### Post by svkndv on 2008-10-23
Clean shutdown done from vista. Started the computer and tried to boot from ubuntu... Same situation.

---

### Post by svkndv on 2008-10-25
can anyone help me to recover the data? i think it is better to return to windows rather than wasting lot of time and effort.

---

### Post by Bucky Ball on 2008-10-25
Damn. What is the issue? Maybe you're right, it's windoze for now, though I hate to say it. I will re-read the thread and see if I come up with any bright ideas ... :-k

Had a thought ... noticed you installed on a separate disk, not partition. Are these disks by any chance IDE and SATA?

ps: the memtest should be testing that 2Gb of RAM, not giving an error. The ram is fine? Windoze is booting fine?

Try this, see if it gives you a clue cos quite frankly, hate to see anyone going back to the Doze!

[http://ubuntuforums.org/showthread.php?t=773787](http://ubuntuforums.org/showthread.php?t=773787)

---

### Post by svkndv on 2008-11-03
Thanks to all of you for your support.Updating this post after a gap of 1 year. 
real issue was with my hard disk. It was quite surprising that this hard disk was running well with xp. Seagate service team informed me that 1 xyz stuff was found miissing from the board.

---

