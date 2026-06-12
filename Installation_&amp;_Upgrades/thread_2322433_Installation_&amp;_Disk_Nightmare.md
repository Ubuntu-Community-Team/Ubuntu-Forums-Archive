---
title: "Installation &amp; Disk Nightmare"
date: 2016-04-28
forum: Installation &amp; Upgrades
---

### Post by peter206 on 2016-04-28
I tried to make a fresh install of Ubuntu 16.04 LTE on my hard disk which was part of previous installation with 3 disks (one external WD hd). I removed 2 hard disks (old with bad sectors) from PC and left only a new one and external HD connected. 

I start the installation with USB key and all goes well until the menu where Ubuntu selects the type of installation. I clearly specified to remove old Ubuntu 15.04 and make a fresh installation. The problem is that the installation decided to skip the HD in the PC and starts to format my external HD. 

1. Major Problem:

My WD external disk with all my precious data was probably fast formatted. I stooped the process as soon I saw the program lightning up the external HD (two seconds max). Now the disk is unrecognizable in Windows (no letter) but I can see it in HD tools with one UEFI partition in the beginning of the disk and two empty partitions. Please tell me I can get back my data. 

2. Problem: 

The disk in my PC is not seen by Ubuntu on my USB and nothing can be done to format this disk or fix it.  When I run Ubuntu in safe mode it ends up with

/dev/disk/by-uuid/xxxxx-xxx-xxx does not exist. Dropping to a shell!
(initramfs) 

I tried boot-repair but the program is giving me only a report option or it is trying to fix the USB drive. Do I have to use windows installation to fix this disk or there is a way to do it with Ubuntu on USB?

Please help me solve this. Thank you.

---

### Post by kek3 on 2016-04-28
I'dont know about getting back your data, but you can recover the letter (I think)

On your pc you need to execute admin [https://gyazo.com/dbd71136a2222655d5ef0d6d45a7c5d8](https://gyazo.com/dbd71136a2222655d5ef0d6d45a7c5d8)
Then you can put a letter in disk manager option [https://gyazo.com/93dabce01d74337ff4c168d8fce500a3](https://gyazo.com/93dabce01d74337ff4c168d8fce500a3)

It is in spanish but i think it can be understand

And sorry for my worse english!!

EDIT: I think that format only deletes the index table, so probably you will get your back back!

---

### Post by peter206 on 2016-04-28
Thanks for prompt reply kek3 but in my case all options are grayed out in windows. The WD disk is there, windows can see it with 3 partitions (first is 600 MB UEFI partition ) but no options are available. :-(

---

### Post by westie457 on 2016-04-28
Hello

For the external drive Testdisk is probably the best tool for the job. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It is also available in the repo's.

Was any/all of your drives set up in a raid configuration?

---

### Post by peter206 on 2016-04-29
I am happy to report that the issue is resolved in both cases. TestDisk saved my butt with data recovery and westie457 pointed out to raid configuration. 

Thanks for prompt help guys! :-)

---

