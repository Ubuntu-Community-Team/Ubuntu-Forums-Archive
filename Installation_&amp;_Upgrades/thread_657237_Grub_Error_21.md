---
title: "Grub Error 21"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by squid636 on 2008-01-03
I screwed up my grub loader and I need some help.  I was trying to install mythubuntu onto my flash drive to test it out.  I thought that the installation was complete since the screen went black after it said it was at 1oo% complete.  It seems that it was still writing to the grub menu.  I tried to restart and when it booted it went to the flash drive fine.  When I took the flash drive out and tried to boot into Windows XP or Ubuntu 7.10 the computer stops and gives me the error 21 code.  Can someone tell me what I need to do to repair my grub file.  Right now I am on the Ubuntu live cd.  Thanks.  [SIZE="3"]Here is the output from menu.lst[/SIZE]

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=30e6bfab-1629-4bec-9f69-0c59e50c24ee ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=30e6bfab-1629-4bec-9f69-0c59e50c24ee ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
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
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

[SIZE="3"]Here is the output of sudo fdisk -l[/SIZE]

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b7d2eab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9121    73264401    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006c57a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris

---

### Post by mikewhatever on 2008-01-03
You have to [reinstall GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") using a live CD or [super grub]("http://supergrub.forjamari.linex.org/") while your flash drive is unplugged.

Here, read some similar threads from the past. They should explain the problem in more details.
[http://ubuntuforums.org/showthread.php?t=448208&highlight=grub+external](http://ubuntuforums.org/showthread.php?t=448208&highlight=grub+external)
[http://ubuntuforums.org/showthread.php?t=439702&highlight=grub+external](http://ubuntuforums.org/showthread.php?t=439702&highlight=grub+external)
[http://ubuntuforums.org/showthread.php?t=382920&highlight=grub+external](http://ubuntuforums.org/showthread.php?t=382920&highlight=grub+external)

---

