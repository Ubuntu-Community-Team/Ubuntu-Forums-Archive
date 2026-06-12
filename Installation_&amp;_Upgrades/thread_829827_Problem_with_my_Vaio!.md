---
title: "Problem with my Vaio!"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by conoco on 2008-06-15
[B]Hello Everyone!
I want to install Ubuntu 8.0 on my laptop (Sony Vaio VGN-CR21S ) and when i click install and to format all the other partitions on it it gives me an error 

Failed to create a swap space

The creation of a swap space in partition #5 of SCSI1 (0,0,0)(sda) failed.

What is the problem? the OS it had before is Windows Vista home Premium edition and a recovery disk partition i want both deleted-formated and install all disk space Ubuntu (cause its the best!!), if someone can please help me i would really appreciate it thank you for your time.[/B]

---

### Post by Sniffer on 2008-06-15
Hi and welcome to ubuntu forum,

Try using Gparted for doing the partitions in your hard disk, you will need at least:

swap partition - twice of your ram
/ (root partition) - rest of the disk

Then use ubuntu CD, bypass the partition options on ubuntuCD and install the OS.

Hope it helps
Sniff.

---

### Post by conoco on 2008-06-15
Thank you for the warm welcoming im a little new on linux how can i do this?
Ok i went in Gparted but it doesnt show any partition or device it says no device detected.
I did refresh but still the same. Is there a possibility that this means the drive is clean? (no OS on it or anything).
What should i try now ? 
Thank you for your help~!

---

### Post by Sniffer on 2008-07-22
> **conoco said:**
> Thank you for the warm welcoming im a little new on linux how can i do this?
Ok i went in Gparted but it doesnt show any partition or device it says no device detected.
I did refresh but still the same. Is there a possibility that this means the drive is clean? (no OS on it or anything).
What should i try now ? 
Thank you for your help~!

Yep, GPARTED or Ubuntu is NOT recognized your drive, this reveals 2 things:

1 - Your Hard Drive is gone or

2 - Ubuntu and Gparted don't recognize your Hard Drive Controller.

---

