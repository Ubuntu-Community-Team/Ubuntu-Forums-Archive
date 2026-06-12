---
title: "Text based installation, how?"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by SpinningAround on 2008-09-16
i tried several times to install ubuntu 8.04 on my stationary computer, since all of them have failed have I started to wonder why and start suspecting a bug. Problem with the installation is that I get a complete lock-up so I need to make a hard reboot, so I'm not able to check the problem after it has occurred. 

Is't possible to make the installation though the console and what commands in that case, if I install it with the console will I be able to see what happen when the installation freezes.

---

### Post by az on 2008-09-16
> **SpinningAround said:**
> i tried several times to install ubuntu 8.04 on my stationary computer, since all of them have failed have I started to wonder why and start suspecting a bug. Problem with the installation is that I get a complete lock-up so I need to make a hard reboot, so I'm not able to check the problem after it has occurred. 

Is't possible to make the installation though the console and what commands in that case, if I install it with the console will I be able to see what happen when the installation freezes.

You can install using the alternate cd.  It's text-only.

But I would suggest you check your computer's hardware.  Faulty hardware can make you think you found a bug:

[http://help.ubuntu.com/community/FaultyHardware](http://help.ubuntu.com/community/FaultyHardware)

---

### Post by Pumalite on 2008-09-16
Make a new CD; download a new iso if necessary. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Do md5sum, burn at 4x or less, do not use CD-RW, check CD integrity before install. If after that you have the same problem; do what az suggested.

---

### Post by SpinningAround on 2008-09-16
> **az said:**
> You can install using the alternate cd.  It's text-only.

But I would suggest you check your computer's hardware.  Faulty hardware can make you think you found a bug:

[http://help.ubuntu.com/community/FaultyHardware](http://help.ubuntu.com/community/FaultyHardware)I think my hardware is working fine since I have XP running on the computer also, but might be worth a try. The thing that confuse me is that I tried installing Ubuntu before I installed Windows and that time was I able to start the installation but it failed to create a ext3 partition. When I tried to install it after I installed XP did the installation stop right after the partitioner get loaded, it doesn't actually show the partition menu it stop before that. I think I give the alt cd a try but I'm a little confused why the normal cd don't work, since I only have installed new harddrives. Before I got new harddrives where I able to install and run ubuntu.

> **Pumalite said:**
> Make a new CD; download a new iso if necessary. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Do md5sum, burn at 4x or less, do not use CD-RW, check CD integrity before install. If after that you have the same problem; do what az suggested.I already burned a new cd but haven't checked md5sum, so maybe.

---

### Post by Pumalite on 2008-09-16
If you can boot a Live CD; post a screenshot of Gparted

---

### Post by SpinningAround on 2008-09-17
Ok uploaded screenshoots of both drives (see **attachment**), /dev/sda/ are my windows drive and /dev/sdb/ are supposed to have my linux partition.



**The installation lock-up right after this load bar is completed.**
[IMG]http://www.psychocats.net/ubuntu/images/installinghardyplus09.png[/IMG]

**it don't actually make it do this part.**
[IMG]http://www.psychocats.net/ubuntu/images/installinghardyplus10.png[/IMG]

pictures from. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Forgot to mention, I have scanned both drives for error but both turned out negative.

---

### Post by Pumalite on 2008-09-17
In the unallocated space is where you can follow my suggestions.

---

### Post by SpinningAround on 2008-09-17
> **Pumalite said:**
> In the unallocated space is where you can follow my suggestions.

try a new cd!

---

### Post by SpinningAround on 2008-09-22
Ok, downloaded a new cd, checked the MD5Sum (it was correct), burned the cd in 8x (slowest). Tried to install it but it failed with something like this (translation from Swedish).

> 
Failed with creating a ext3-filesystem on partition no.1 on SCSI4(0,0,0)(sdb)


Adding a few things, was able to create a partition using gparted and get the installer to start copying files. Then Errno 30 read-only show up, thing is that it say that the harddrive might be damaged but I have checked the harddrive with Samsungs own test program and it wasen't able to find any problems.

---

### Post by Pumalite on 2008-09-22
Try r4escuecd (TestDisk):
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

