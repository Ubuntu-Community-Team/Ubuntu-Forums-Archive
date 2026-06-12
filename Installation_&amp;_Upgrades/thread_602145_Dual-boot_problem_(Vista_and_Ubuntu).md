---
title: "Dual-boot problem (Vista and Ubuntu)"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by spicyfooty on 2007-11-03
Hi all,
Done searching, but still have problem..really BIG one.

Before installing Ubuntu, I have 2 harddisks in this way:

C: (XP OS) , D: (Vista OS), E: (data files only)

C and D are actually partitioned from 80G SATA HDD.

So, I run Ubuntu Live CD and delete C partition and make new partition (39G) to make way for Ubuntu OS and 1G for swap files.

Now, I cannot boot Vista at all!! So, I looked around forum for help.
Here's my device.map

(hd0)	/dev/sda
(hd1)	/dev/sdb

And edited the menu.lst as follows:

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=00e9626e-98f3-4d9d-a390-6fc7d50ce341 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=00e9626e-98f3-4d9d-a390-6fc7d50ce341 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Vista
root		(hd0,2)
makeactive
chainloader	+1

title		Vista
root		(hd0,3)
makeactive
chainloader	+1

title		Vista
root		(hd0,4)
makeactive
chainloader	+1

title		Vista
root		(hd1,0)
makeactive
chainloader	+1

title		Vista
root		(hd1,1)
makeactive
chainloader	+1

title		Vista
root		(hd1,2)
makeactive
chainloader	+1
 
### END DEBIAN AUTOMAGIC KERNELS LIST

My Ubuntu desktop shows 2 drives. Sda5 and Sdb1. 

Sda5 with all my vista files inside.    -----> looks like D drive 
Sdb1 with all my data files inside.    ------> looks like E drive

I tried every combination possible but I still cant get Vista to boot! 
Please help....

---

### Post by dcstar on 2007-11-04
> **spicyfooty said:**
> Hi all,
Done searching, but still have problem..really BIG one.

Before installing Ubuntu, I have 2 harddisks in this way:

C: (XP OS) , D: (Vista OS), E: (data files only)

C and D are actually partitioned from 80G SATA HDD.

So, I run Ubuntu Live CD and delete C partition and make new partition (39G) to make way for Ubuntu OS and 1G for swap files.

Now, I cannot boot Vista at all!! So, I looked around forum for help.
.........
Sda5 with all my vista files inside.    -----> looks like D drive 
Sdb1 with all my data files inside.    ------> looks like E drive

I tried every combination possible but I still cant get Vista to boot! 
Please help....

Try:

```
title		Microsoft Windows Vista
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```

---

