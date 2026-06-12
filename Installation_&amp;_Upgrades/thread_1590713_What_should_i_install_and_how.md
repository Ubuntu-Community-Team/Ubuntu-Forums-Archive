---
title: "What should i install and how ?"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by Warlok22 on 2010-10-08
i have 2 hdd x 500gb and 1x 250 gb's

a few days ago o decided to merge the 2 partitions i had in 2nd  500gb hdd and to become one... the second partition was filled up with only photos of mi family witch i was gathering since our first digital camer ... so i had somm 110 gb of pictures...

Beeing an windows user... with a good package of knwoledge in using windows programs and bugs.. at that moment i didnt consider necesarly to defrag that partition before merging partitions... so the resoults ware a catastropy . 

i've tryed in windows the following softawares :

```
-patition magic    - recover files   - Active @ patition recovery  
-Disc Internals    - Acronis           - Active @ Partition Recovery Enterprise
```the best result i had was to rescue entire amount of data with folders and files with names but when i try to open a photo there was no preview.

the hdd and the partitions is swhown by the boot script as :

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sda1    *             63   111,298,319   111,298,257   7 HPFS/NTFS /dev/sda3         111,298,383   519,847,334   408,548,952   7 HPFS/NTFS  

```I've made no modifications to the disk MBR or other stuff like, i went to 
an company witch activities are only in the field of data recovery and they
told me that if i pay them 100 $  they will recover mi entire data. 

QUESTION : is there in linux/ ubuntu / etc any way that i  can recover that partition ?

i'm attaching an .JPG to see how's the hdd seen in Partition magic .

Thanks in advance and hope to succed !
[IMG]http://ubuntuforums.org/%3Ca%20href=http://img696.imageshack.us/i/hddbo.jpg/%20target=_blank%3E[IMG]http://img696.imageshack.us/img696/5686/hddbo.jpg[/IMG][IMG]http://img696.imageshack.us/img696/5686/hddbo.jpg[/IMG]

---

### Post by dino99 on 2010-10-08
to recover this unallocated partition, boot on cgsecurity disk:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

then follow the procedure

Before installing ubuntu its better first to defrag your other partitions (windows), then prepare the ubuntu partitions with partedmagic: [http://partedmagic.com/](http://partedmagic.com/)

Boot on it and make 3 partitions, (take note of their names: /dev/sdx, x is a letter from a to z):
- / (root) in ext3 or ext4 format, about 12 gb and make it bootable
- swap about 2 gb
- /home in ext3 or ext4 format, unlimited

then install the alternate iso (i386 for 32 bits, amd64 for 64 bits) on a cd/dvd or usb stick (burn at lowest speed) and select custom installation to use the previous buil partitions

---

### Post by ronnielsen1 on 2010-10-08
The best cd's that I've seen for data recovery are puppy unleashed and hirens bootcd for testdisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
> TestDisk is powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting a Partition Table). Partition table recovery using TestDisk is really easy.

Hirens boot cd:
[http://phpfusion.org/software/system/5638-hirens-bootcd-v106-and-keyboard-patch.html](http://phpfusion.org/software/system/5638-hirens-bootcd-v106-and-keyboard-patch.html)
I can't find a link for puppy unleashed but if you can find it, it is quicker

---

### Post by Warlok22 on 2010-10-08
[QUOTE=dino99;9939254]to recover this unallocated partition, boot on cgsecurity disk:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

QUOTE]

The hdd had 3 partitions C,D,E... i told partrition magic to merge E with D ...remaining only C an D
inside the partition D i got an folder named E witch is inacsesible... that folder was created and ment to take all the inormation inside partition E !

here are the resoults  of the Deepest scan 

[IMG]http://img301.imageshack.us/img301/3303/hdd2.jpg[/IMG]

---

### Post by Warlok22 on 2010-10-08
bump

---

### Post by Warlok22 on 2010-10-08
bump x2!

---

### Post by Warlok22 on 2010-10-08
This is first serious recovery program run'd by me 

now how do i recover safe that partition ?

[IMG]http://img440.imageshack.us/img440/9026/recoveryd.jpg[/IMG]

---

### Post by ronnielsen1 on 2010-10-09
That's a hard question to answer without actually being there and seeing all of the results of testdisk. I don't think I would have merged the partitions. [Here's]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") a good step-by-step for testdisk

---

