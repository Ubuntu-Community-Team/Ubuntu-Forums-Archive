---
title: "[SOLVED] Grub can't find partition..."
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Tosa on 2007-10-27
So, I finally managed to finish Gutsy install. Grub lists Linux kernel and Windows XP.
But if I select Linux I get
**No such partition**
If i select Windows I get
[B]NTLDR is missing
[/B]
Both Linux and Windows are installed on 120 GB ATA drive. I use 160 GB SATA drive for storage. ATA drive is set as a boot drive in bios.

This is menu.lst:

```
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=a9529e2e-fe08-43b5-8ce9-2d6a8b0b424a ro quiet splash nosplash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=a9529e2e-fe08-43b5-8ce9-2d6a8b0b424a ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd1,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```

And this is output of fdisk:

```
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b212a8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   117226304    58613121    c  W95 FAT32 (LBA)
/dev/sdb2       117226305   178257239    30515467+   f  W95 Ext'd (LBA)
/dev/sdb3       178257240   234436544    28089652+  83  Linux
/dev/sdb5       117226368   175815359    29294496    b  W95 FAT32
/dev/sdb6       175815423   178257239     1220908+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5488a53a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312577775   156288856+   7  HPFS/NTFS
```

This is the output of the of the last boot. Before that one the 120 GB ATA drive was listed as sda!
I'm completely confused and cant figure out what to do...

---

### Post by Pumalite on 2007-10-27
Reinstall Grub:[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by logos34 on 2007-10-27
Select the ubuntu kernel on the grub menu screen and hit 'e' to edit.  Hit 'e' again on 'root' line and change to (hd**0**,2).  Hit enter to save and 'b' to boot.  If that gets ubuntu to boot, make the change permanent:

gksudo gedit /boot/grib/menu.lst

-change 'groot' and root lines accordingly.

As far as windows goes, you might want tp try switching the drives in **/boot/grub/device.map**.  

Not sure about the musical drive designations on reboot...i've seen it happen with two sata controllers being recognized differently at each boo, but not ide and sata

---

### Post by Tosa on 2007-10-27
Thanks for your help, and my apologies for your trouble.
I was stupid enough not to see this thread [http://ubuntuforums.org/showthread.php?t=594088](http://ubuntuforums.org/showthread.php?t=594088)

I just need to figure out how to mark this one as solved...

---

### Post by Pumalite on 2007-10-27
Use the 'Thread Tools'

---

### Post by Tosa on 2007-10-28
Thanks, it was obvious...

By the way, ubuntu part of your suggestion in the thread I've mentioned worked for me (again obviously).
I've changed the windows part, but still get the message about missing ntloader. When I change original line hd1,0 to hd0,0 I get the grub prompt!? I haven't reinstalled grub (yet).

---

