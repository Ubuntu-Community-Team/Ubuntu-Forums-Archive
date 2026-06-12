---
title: "What DCDRW brand/model works under HARDY"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by gwoodruff on 2008-05-09
I am convinced that my DVDRW problem :

[http://ubuntuforums.org/showthread.php?t=777805](http://ubuntuforums.org/showthread.php?t=777805)

is a hardware compatibility issue. 

If you have a working DVDRW drive under HARDY please post your brand / model.

---

### Post by Therion on 2008-05-09
I've confirmed that Hardy HATES my Plextor 716A (PATA) DVD-RW.

**Sony DRU190A = Joy.**  

Failed with the 40 connector/40 pin cable, works like a champ with the 80 connector/40 pin cable.

Cheap too... Set me back ~$30.

---

### Post by arch stanton on 2008-05-09
**gwoodruff ** 

I appreciate the effort you are putting into this, as i am more or less in the same boat.


My HP 420n will play DVD's , will burn audio cd's, but will not blank or burn DVD's

besides being maybe permissions related, I have no idea where to begin with this problem

Anyway here's the output of **lshw** 

P.S. Zappa rules!


 description: DVD writer
             product: DVD Writer 420n
             vendor: HP
             physical id: 0.1.0
             bus info: scsi@4:0.1.0
             logical name: /dev/cdrom1
             logical name: /dev/dvd1
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.33
             serial: [HP      DVD Writer 420n 1.3304110101  MY41T1R1
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1

---

### Post by Pumalite on 2008-05-09
This one works too:
 *-cdrom
                   description: DVD-RAM writer
                   product: DVD-RAM GSA-H55N
                   vendor: HL-DT-ST
                   physical id: 0.0.0
                   bus info: scsi@0:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/dvd
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: 1.01
                   serial: [HL-DT-STDVD-RAM GSA-H55N1.0107/05/30 7U02
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 status=open

---

### Post by Pumalite on 2008-05-09
Another one:
Pioneer D-112

---

### Post by Pumalite on 2008-05-09
Another one:
DVD LG GSA-H44N

---

### Post by bml137 on 2008-05-09
> **Therion said:**
> I've confirmed that Hardy HATES my Plextor 716A (PATA) DVD-RW.

**Sony DRU190A = Joy.**  

Failed with the 40 connector/40 pin cable, works like a champ with the 80 connector/40 pin cable.

Cheap too... Set me back ~$30.

I have a **Sony DRU800A = Bad**

It works perfectly fine for about 10/15 minutes, then when I burn or am in the middle of a burn (growisofs), the UBU sits at 100% and it never gets anywhere.  When I make the system turn over some memory (run a memory intensive app), the burning continues, but stops again once the app stops sucking up memory.  It is quite odd.

After about an hour (whether I burn something or don't use it at all), the CD drive cannot be ejected by any means and becomes unusable until a system reboot is in order.

---

### Post by trebor7_1 on 2008-05-09
Hi here are details from lshw in 8.04

cdrom
                description: DVD writer
                product: DVD RW AD-5170A
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom2
                logical name: /dev/dvd2
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.11
                serial: [Optiarc DVD RW AD-5170A 1.11 Jul19,2006
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open

This drive was 100% under 7.10 but failed to write after upgrading to 8.04.

Good news is I just noticed that the drive was connected with an old 40 way ribbon. So changed to an 80 way ribbon and...
IT WORKS

Hope that helps some others.

Regards

Trebor

---

### Post by tazd on 2008-05-09
Using a Samsung  SH-S202N.

Works a treat under Hardy for me.

Hope you get your problem fixed..

---

### Post by cub on 2008-05-10
I have a HP nx9010 laptop with DVDrom that works if booted with cd/dvd in it, otherwise it doesn't work.

lshw:
 *-cdrom
                   description: DVD reader
                   product: SAMSUNG CDRW/DVD SN-324F
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: U201
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: status=nodisc

---

### Post by gwoodruff on 2008-05-11
Thanks to those that have posted. To those that have some functionality of their drive but experience some kind of error, you may want to confirm you have a 80 conductor IDE cable. please see this post for details [http://ubuntuforums.org/showthread.php?t=785417](http://ubuntuforums.org/showthread.php?t=785417) (thanks to Therion for that info). 
      To the rest confirm you do not see any valid optical drive. If you still have gutsy as a bootable choice in the Grub menu choose it and see if you have the drive. If you don't it may be another problem. If you do see it you know your hardware is good. Boot back into Hardy and use the terminal and type the command " lshw -C disk ". If you post an output it may just be a broken or missing symlink. If you see nothing investigate fstab and the device listing for the optical drive (hdc vs scd0 etc).

thanks, Gary

---

