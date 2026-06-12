---
title: "Ricoh xD Card Reader on a Dell E1405"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Haluci on 2008-02-20
The relavent bits of lspci:

```
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

Tried the stuff in [this post]("http://ubuntuforums.org/showthread.php?t=436364") and it didn't work.  Is there anything else I can try?

---

### Post by corevette on 2008-02-20
[http://ubuntuforums.org/showthread.php?t=453893](http://ubuntuforums.org/showthread.php?t=453893)
saw this...don't know if it'll help :-D

---

### Post by Haluci on 2008-02-20
hm, that didn't work.  It's interesting what the op's solution was:

> **.adma said:**
> just saw your reply, sorry about that!  I was without internet all weekend...oddly enough, the way I fixed the issue was to comment out the line in the FSTAB file that set up permissions for the MMC card.  Odd huh?

I don't have anything of the sort in my fstab file.  Do I need to add something?

Here's my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d632fe08-ac2b-4648-94c8-03db48a8f9cb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2b988f35-c760-4d6d-8346-8ef5f8c75cac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by Haluci on 2008-02-22
Bumping after 1 day of inactivity.

I'm beginning to think that all I need to do is mount the memory card (perhaps with pmount, and then add the mount point to fstab), but how do I mount something that ubuntu doesn't even recognize?

---

### Post by Haluci on 2008-02-24
bumping again after 2 days of inactivity.

Maybe I'll just try again next month.

---

### Post by doublearon on 2008-05-12
I'm not sure if the reader works for any others, but the reader hasn't ever read XD cards for me on my e1405. It pisses me off because I gave away my kodak camera with an SD Card. 

I guess XD is just too "proprietary" for anyone to bother making a driver for it.

---

