---
title: "Failed to create swap space..??"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by Giulia_newby on 2008-09-30
Hi everyone!

I'm a fresh new ubuntu user, well at least I would be if I could get it installed! I'm trying to install ubuntu on a laptop that wasn't running well with windows xp anymore. It was crashed and needed recovery cds. Which I obviously didn't have, so I decided to try and put ubuntu on. I downloaded the cd image and all went perfectly fine until the installation began. After some time, an error message appeared saying:

Failed to create a swap space
The creation of swap space in partition #5 of SCSI1(0,0,0)(sda) failed.

Anything I can do about it or should I just trash the notebook? 
:(

Thanks for your help!

---

### Post by Partyboi2 on 2008-09-30
Try wiping the drive with [[COLOR=Blue]dban[/COLOR]]("http://www.dban.org/") and try installing again.

---

### Post by Giulia_newby on 2008-10-01
Thanks for your help! But the problem now is the following: I did as you suggested and ran dban. It worked but said there were some non fatal errors. I couldn't save the log file 'cos the laptop has no floppy. 
So then I tried running ubuntu again, and this time the error message is:
Failed to create a file system
the ext3 file system creation in partition #1 of SCSI1 (0,0,0)(sda) failed.

Anything else I can do?
Thanks again, all suggestions are welcome!

---

### Post by Partyboi2 on 2008-10-01
Try making the partitions with gparted before starting the install process. You can access gparted by going to System>Admin>Partition Editor.

---

### Post by cariboo on 2008-10-01
It almost sounds like your hard drive is failing, I would suggest going to your hard drives manufacturers web site and download and use the diagnostic tools on your hard drive. This will give you a positive answer about the condition of the hard drive.

Jim

---

### Post by smithers102 on 2008-12-08
I have the same problem. The strange thing is during the part of the installation where you configure partitions my harddrive is detected, but when i boot gparted via live CD it doesn't detect my HDD.

Any ideas?

---

### Post by jccjoanne on 2010-03-17
Sorry for bringing old post back to live...
I am completely new to Linux, I am trying to install Ubuntu 9.10... however, I keep getting the same error. I tried to install 8.04 as well, still it doesnt work. I have the same problem as post #6 - gparted cannot find my HDD... and even worst... my computer wont boot from my hdd now... What should I do??? (I am planning to wipe off my window vista completely and let ubuntu takes 100% control...)

---

