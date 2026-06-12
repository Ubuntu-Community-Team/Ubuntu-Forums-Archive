---
title: "Grub Error 15"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by anortrup on 2007-07-31
I've just installed Ubuntu and I'm receiving an "Error 15" from grub.

I think that the error is caused by Ubuntu and Grub detecting drive orders differently.

I have three drives.  They are listed here in no particular order because no two pieces of software agree which one goes first

Drive 1: SATA 
Set first in the boot order in BIOS.

This disk has 2 partitions.  The first partition contains my home directories.  The second is supposed to be the boot partition.

Detected as (hd0) by Grub Boot CD
Detected as /dev/sdc by Ubuntu
Detected as (hd2) when I run 'sudo grub' inside Ubuntu

Drive 2: SATA 

Three partitions.  Root, Swap, and an ext3 partition for backups of the home directory.

Detected as (hd1) by Grub Boot CD
Detected as /dev/sdb by Ubuntu
Detected as (hd1) when I run 'sudo grub' inside Ubuntu

Drive 3: IDE (Channel 0 Master)
Has a single NTFS partition for my Windows XP installation.

Detected as (hd2) by Grub Boot CD
Detected as /dev/sda by Ubuntu
Detected as (hd0) when I run 'sudo grub' inside Ubuntu


Using the Grub Live CD I can get the OS running with these Commands:
```

root (hd0,1)
kernel /vmlinuz-2.6.20-16-generic root=/dev/sdb1
initrd /initrd.img-2.6.20-16-generic
boot

```

My /boot/grub/devices.map file looks like this:
```

(hd0)   /dev/sdc
(hd1)   /dev/sdb
(hd2)   /dev/sda

```

And my /boot/grub/menu.lst file looks like this: (useless comments omitted)

```


## ## End Default Options ##
default		0
timeout        10


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=ffa6418a-8fdc-4c0b-90db-e6bb33ba518e ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=ffa6418a-8fdc-4c0b-90db-e6bb33ba518e ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=ffa6418a-8fdc-4c0b-90db-e6bb33ba518e ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,1)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=ffa6418a-8fdc-4c0b-90db-e6bb33ba518e ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I'm generally very competent but this one has me stumped.  Any help is greatly appreciated.

-Andy

---

### Post by Pumalite on 2007-07-31
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15)

Use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by anortrup on 2007-07-31
I have to say that that worked wonderfully.  I unfortunately did not take the notes that I wish I had in order to document the solution correctly.

I do know that I did restore grub on the the boot sector.  I'm guessing that I most likely made a mistake on the partition configuration section of installation.

Props to the developers of Super Grub for a great product.

---

