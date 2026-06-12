---
title: "Installed 10.10 along side vista, now I can't boot into vista"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by mikemamoss on 2011-04-06
Need some help, I installed Ubuntu 10.10 on my PC running Vista Home Basic. I installed to run as a dual boot but now I can only boot into Ubuntu. Please any assistance would be appreciated as I have tried to run the recovery disk for Vista and it errors out also..thanks..Mike

---

### Post by wilee-nilee on 2011-04-06
First in the ubuntu terminal run
sudo update-grub
If vista shows reboot to see if your in.

If vista doesn't show then in the terminal run
sudo fdisk -lu
and post the results.

If this is a wubi install then don't bother with the first command and just identify this by running the second the fdisk.

---

### Post by mikemamoss on 2011-04-06
I ran both the commands, below are the results..

mike@mike-Aspire-T180:~$ sudo update-grub
[sudo] password for mike: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
mike@mike-Aspire-T180:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00087d9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   306440191   153219072   83  Linux
/dev/sda2       306442238   312580095     3068929    5  Extended
/dev/sda5       306442240   312580095     3068928   82  Linux swap / Solaris
mike@mike-Aspire-T180:~$

---

### Post by wilee-nilee on 2011-04-06
If Vista was on sda it has been over-written it looks like, if you only have the one HD.

---

### Post by mikemamoss on 2011-04-06
great..i was afraid of that, i only have the one hard drive. I attempted to use my recovery disk but get an error when attempting to boot from it. any advice?

---

### Post by wilee-nilee on 2011-04-06
> **mikemamoss said:**
> great..i was afraid of that, i only have the one hard drive. I attempted to use my recovery disk but get an error when attempting to boot from it. any advice?

People use testdisk and photorec to recover and do a number of things like finding deleted partitions. I'm not familiar with it though so I have no real advice on using it. Read up on it before using.
[http://www.cgsecurity.org/](http://www.cgsecurity.org/) 

You can get the oem set from acer cheap, and clone the install so in this same situation, or a broken vista, you could just slip the clone back in.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by dazman19 on 2011-04-06
sorry mate, you might get lucky and be able to get some data back but i cant heap with data recovery.
but after looking at the sectors:
/dev/sda1 * 2048 306440191 153219072 83 Linux
it looks like your intaller probably ran a format on the windows drive. 

I hope you backed up some of the data to a USB drive or CD rom, or even to a network location or somewhere on the internet. 

If you just have a fresh install of ubuntu, the easiest way to dual boot is to re-install windows first, allocate only say 50% of the drive, and then install ubuntu afterwards on the other 50%, that way grub should set up the boot file for both of them automatically.

---

