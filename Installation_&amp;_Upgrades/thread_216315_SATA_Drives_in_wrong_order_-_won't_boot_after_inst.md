---
title: "SATA Drives in wrong order - won't boot after install"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by grim1234 on 2006-07-15
Here's the setup :

Asus A8N-SLI Deluxe, raid off.

SATA1 : Seagate 200gb
SATA2 : Seagate 200gb (1 fat32 partition)
SATA3 : Maxtor 300gb (1 ntfs partition)
SATA4 : Maxtor 300gb (1 ntfs partition)

on booting with the i386 install cd ubuntu allocates :

SATA1 : /dev/sdc
SATA2 : /dev/sdd
SATA3 : /dev/sda
SATA4 : /dev/sdb

Why it chooses this order I have no idea. 

I want to install to SATA1, and have partitioned as following :

/dev/sdc1 /root    - 100gb
/dev/sdc2 /swap    - 2gb
/dev/sdc3 /windows - 86gb (windows xp, ntfs, already installed).
(do I need a /boot partition or can it go on root?)

When i install ubuntu, it does not place the bootloader on /dev/hdc (SATA1), but probably on /dev/hda.

How can I set the drives to load in a logical order? 
(ie SATA1 for /dev/hda)

How can I load grub onto /dev/hdc if this is not possible?

Should I submit this a a bug somewhere?

Thanks,

G.

---

### Post by rbalfour on 2006-07-15
Check your grub. the hd(1,0) is most likely wrong.
I had the same issue, changed hd(0,0) and /dev/sdc1

---

