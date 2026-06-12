---
title: "Can't boot XP or Kubuntu after new install of 8.04"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Tiger__Style on 2008-05-10
***EDIT: See my 3rd post, now only XP that won't boot, probably because I tried installing Grub til hd1?***

After a new install of 8.04 I can no longer boot into XP and not the newly installed Kubuntu either. When I choose XP in grub, it says: Invalid or unsupported executable format, and Kubuntu: No such partition

**Output of sudo fdisk -l:**

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4d3e54f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401   83  Linux

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc712ecf8

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS**
/dev/sdb2           42314       42562     2000092+  82  Linux swap / Solaris
**/dev/sdb3           42563       48641    48829567+  83  Linux**
/dev/sdb4           12749       42313   237480862+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc712ecf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       48641   390708801   83  Linux

---------------------------------------------------------------

**My XP install is on sdb1 and Kubuntu is on sdb3**

**My /boot/grub/menu.lst:**

## ## End Default Options ##

[B]title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b25c0b74-ae79-422b-be72-57ce26a6fc5b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet[/B]

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b25c0b74-ae79-422b-be72-57ce26a6fc5b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
[B]title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1[/B]

---

### Post by Tiger__Style on 2008-05-10
Figured it out :)

---

### Post by Pumalite on 2008-05-10
Can you share the solution for the benefit of the forum?

---

### Post by Tiger__Style on 2008-05-11
Seems I didn't completely solve the problem after all.

What I did was change the setting for Ubuntu to hd0,2 instead of hd1,2 and for XP to hd 0,0 instead of hd 1,0.

However, before I tried this I probably did a stupid thing :(
I tried reinstalling Kubuntu, and when it came to grub install, I changed that from hd0 to hd1.

Kubuntu loads fine now, but when I select XP; I just get the text "Starting up" in the top left corner like I always do, but nothing more happens. I tried reinstalling Kubuntu again, and selecting hd0 for grub, but that doesn't solve the problem.

Anyone know how I can fix this, preferably without having to reinstall XP and Kubuntu?

---

### Post by housam on 2008-05-11
Try to use the [[COLOR="Red"]_super Grub disk_[/COLOR]]("http://supergrub.forjamari.linex.org/")

---

