---
title: "[SOLVED] No Grub on boot"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by Enforcer83 on 2008-02-08
I am currently dual booting my computer.  However, when I start my computer it immediately boots to windows, there is no menu that I can choose what OS I wish to boot to.  What is required to fix this?  The following is my current hard-drive configuration from fdisk -l:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a557382

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS (contains system32 folder)
/dev/sda2            3265        9729    51930112+   7  HPFS/NTFS (misc windows programs)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x261f0283

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            5223       60801   446438286    7  HPFS/NTFS (storage drive 1)
/dev/sdb2   *           1        5002    40178533+  83  Linux
/dev/sdb3            5003        5222     1767150    5  Extended
/dev/sdb5            5003        5222     1767118+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10414032

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         522     4192933+   7  HPFS/NTFS (pagefile drive)
/dev/hda2             523       24792   194948743+   7  HPFS/NTFS (storage drive2)

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c3a1af9

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       11982    96245383+   7  HPFS/NTFS (storage drive 3)
/dev/hdb2           11983       14593    20972857+   c  W95 FAT32 (LBA) (storage drive 4 left over from before 5.10)

```

---

### Post by Rocket2DMn on 2008-02-08
Sounds like you need to reinstall GRUB and have it set as the bootloader, here's how you can do that: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

---

### Post by Enforcer83 on 2008-02-08
I'll give it a try.

---

### Post by zvacet on 2008-02-09
When comp try to boot you see it count time in sec until it boot.Then press ESC key an you should see all options to boot.If Ubuntu is one of them select it and hit Enter.

---

### Post by Enforcer83 on 2008-02-09
@Rocket2DMn
nope didn't work or maybe I am just doing something wrong.  Here is what I get from grub (while in ubuntu)

```

enforcer@REACH:~$ sudo grub
[sudo] password for enforcer:
Probing devices to guess BIOS drives. This may take a long time.
grub> find /boot/grub/stage1 
 (hd3,1)

```

So using that and the following from my menu.lst, what should be the sequence of commands that I input?

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a80be03f-d9c9-4f14-9f40-60e62a3a0f75 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a80be03f-d9c9-4f14-9f40-60e62a3a0f75 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd3,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

---

### Post by sandysandy on 2008-02-09
the boot priority is set to which hard disk.

regards

---

### Post by Enforcer83 on 2008-02-09
In BIOS my computer is setup to boot these drives in sequence

DVD-ROM
DVD-RW
Floppy
SATA 1 (hd2)
SATA 2 (hd3)
IDE 1 (hd0)
IDE 2 (hd1)

EDIT:
but yet when I go

grub> root (hd3,1)
grub> setup (hd2)

and i reboot GRUB gets printed to the screen over and over again

---

### Post by sandysandy on 2008-02-09
it looks that linux is on SATA 2. however sata 1 is set to boot first, which has windows. so windows is booting. 

where did u install grub while doing the installation. did u install it to sata1 or sata 2.

regards

---

### Post by Enforcer83 on 2008-02-09
I really wasn't paying attention so i believe it installed to its default location.

---

### Post by sandysandy on 2008-02-09
have u tried the following:-

- disconnecting all drives other than the Linux one to see if it boots (This will clarify whether grub was installed on the linux HDD MBR or not).
- super Grub disk to reinstall ur grub.(can be downloaded from net and burnt as ISO and then boot from it)

regards

---

### Post by sandysandy on 2008-02-09
u may also consider changing the boot order in BIOS and then boot to see whether it helps (since it is not sure where Grub is installed).

regards

---

### Post by Enforcer83 on 2008-02-09
I tried reinstalling ubuntu real quick and I got an interesting response.  I selected hd2 (my windows install location) for the location to write the location of grub to.  Grub was found but it printed "GRUB" over and over and over again.

---

### Post by Enforcer83 on 2008-02-09
Solved it.  I installed grub to my first IDE drive (hd0) set my bios to boot that drive first and everything works. So thanks all for the help.

---

