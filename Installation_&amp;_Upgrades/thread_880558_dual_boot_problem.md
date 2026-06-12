---
title: "dual boot problem"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by a-guest-user on 2008-08-05
a desktop pc with 2 hard drives: hard drive 1 has WIN 2000 installed on it, then I installed Ubuntu 8.04 on the second hard drive. Both hard drives are SATA Samsung 160 GB.

The installation worked fine, on restart the Grub boot loader appears, offering to boot into both systems. When I choose Ubuntu, this error is displayed:
```
Error 17: cannot mount selected partition
```
When choosing WIN 2000, it says:
```
Error 13: invalid or unsupported executable format
```

I assume this is a Grub problem, so here is the /boot/grub/menu.lst:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4d6a8dda-8735-421e-9f56-f97a9bda5ee8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4d6a8dda-8735-421e-9f56-f97a9bda5ee8 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
chainloader	+1
```

And the /etc/fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=4d6a8dda-8735-421e-9f56-f97a9bda5ee8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=e1b8bdf1-2041-46a1-99ec-76016ea66235 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I don't have much of a clue as to what I can do, so I'd appreciate any help. thanks.

---

### Post by cdtech on 2008-08-05
Whats the output of "sudo fdisk -l"

---

### Post by cdtech on 2008-08-05
You'll want to make sure your BIOS is set correctly for SATA drives as well.

---

### Post by a-guest-user on 2008-08-05
fdisk -l says:
```
Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xd84739a3

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       16708    93249292+   f  W95 Erw. (LBA)
/dev/sda5            5100       16708    93249261    7  HPFS/NTFS

Platte /dev/sdb: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x0004b6f7

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1       19293   154970991   83  Linux
/dev/sdb2           19294       19457     1317330    5  Erweiterte
/dev/sdb5           19294       19457     1317298+  82  Linux Swap / Solaris
```

When booting with the live cd, it takes quite long (more than 5 minutes), and a message appears saying:
```
ata2.00: revalidation failed (errno=-5)
ata2.00: exception Emask 0x0 SAct [sth else here] frozen
```
The message appears 3 times, then Ubuntu seems to boot normal.

How would I have to set up the Bios for SATA disks?

---

### Post by cdtech on 2008-08-05
I'm not really sure which board you have. Normally it would be in the boot order section I would think..

---

### Post by a-guest-user on 2008-08-05
any hint as to what I should look for? if in BIOS I select the WIN disk to be booted from, it works fine, WIN2000 starts without problems, so I'm not sure it really is a BIOS problem.

the boot loader is on the Linux disk.

any other ideas?

---

### Post by logos34 on 2008-08-05
> **a-guest-user said:**
> if in BIOS I select the WIN disk to be booted from, it works fine, WIN2000 starts without problems, so I'm not sure it really is a BIOS problem.

the boot loader is on the Linux disk.


When the grub menu screen comes up press 'e' to edit the ubuntu kernel. 'e' again on the 'root' line and change to (hd**0**,0).  'enter' and 'b' to boot.

Once inside ubuntu make the change permanent:

gksudo gedit /boot/grub/menu.lst

--change 'root' lines and 'groot' (near the top) to match.

Your windows entry should [look exactly like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

---

### Post by a-guest-user on 2008-08-05
thanks, that has partially helped. I also found this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635)

So I changed the boot line to hd0,0 and added irqpoll all_generic_ide to the kernel line.

It now starts booting, but doesn't get until the actual OS. the error "ata4.00: revalidation failed (errno=-5)" and several other lines are displayed, repeated, and eventually it stops booting, ending with a line (initfams) or similar.

Any ideas? It seems Ubuntu has trouble with the SATA disks.

---

