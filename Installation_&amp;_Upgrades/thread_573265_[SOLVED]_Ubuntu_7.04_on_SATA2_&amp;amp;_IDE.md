---
title: "[SOLVED] Ubuntu 7.04 on SATA2 &amp;amp; IDE"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by CrustyDOD on 2007-10-11
Hey

I have a problem, i just installed latest 7.04 in my SATA drive but when i reboot it goes to windows. So since i have IDE drive also i'm guessing it installed GRUB on IDE instead of SATA. Ide drive contains nothing really, just some backup files. Windows is installed on 1 partition on SATA drive and i just put Ubuntu on another partition on SATA.

Now, can i fix this in some simple way or do i have to reinstall everything? If i have to reinstall ubuntu, where on earth do i select where the grub should be installed? I did not see any option when i was installing it!! Maybe i missed it..

Grub should be on the same partition as windows correct?

Hope someone can help me.

Thanks.

---

### Post by be4truth on 2007-10-11
Try this:

Start your Ubuntu Live CD. In the frist menu you choose 'Boot form first hard drive'
I assume your sata drive will boot.
In case it does boot into Ubuntu. 
The open a terminal.

```
sudo grubinstall /dev/sda
```

That will install your grub boot loader on your sata drive.
Make sure the sate drive is plugged into the first sata port.

---

### Post by CrustyDOD on 2007-10-11
Hey

First part worked! 

I'm in ubuntu now but when i type:
```
sudo grubinstall /dev/sda
```
i get: 
> sudo: grubinstall: command not found

Now what?

---

### Post by be4truth on 2007-10-11
sorry, there was a typing mistake.
Use this one:

```
sudo grub-install /dev/sda
```

---

### Post by CrustyDOD on 2007-10-22
Hello!

Finally had a chance to do this and it doesn't really work!

The command itself works and when i reboot GRUB does show up. The problem is when i want to load ubuntu or windows, it says it cannot find partition. Can't load ubuntu without CD and cannot load windows at all.

In installer (partition maker) i had hda and sda. sda7 is where ext3 partition is.

**/boot/grub/device.map**
> (hd0)   /dev/hda
(hd1)   /dev/sda


> sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09470946

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7297    58613121    7  HPFS/NTFS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb67bb67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       60800   467893125    f  W95 Ext'd (LBA)
/dev/sda5            2551       15298   102398278+   7  HPFS/NTFS
/dev/sda6           15299       30496   122077903+   7  HPFS/NTFS
/dev/sda7           30497       40308    78814858+  83  Linux
/dev/sda8           40309       40794     3903763+  82  Linux swap / Solaris
/dev/sda9           40795       60800   160698163+   7  HPFS/NTFS


**/boot/grub/menu.lst**
> ## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=79439698-ed09-48fb-a676-bfcebd2ca442 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=79439698-ed09-48fb-a676-bfcebd2ca442 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


I'm guessing that * (boot) is at the wrong place?

Any ideas how to fix this?

---

### Post by logos34 on 2007-10-22
**gksudo gedit /boot/grub/menu.lst**

>change 'groot' and 'root' lines to **(hd[COLOR="Red"]0[/COLOR],6)**

>change windows entry to:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd**[COLOR="Red"]0[/COLOR]**,0)
savedefault
makeactive
chainloader +1


>Reverse device.map:

> (hd0) /dev/sda
(hd1) /dev/hda

---

### Post by logos34 on 2007-10-22
And the boot flag (*) is fine, it should be on windows partition.

---

### Post by CrustyDOD on 2007-10-23
Works! Thanks a lot!

---

### Post by logos34 on 2007-10-23
ok, super.  Mark as 'SOLVED' (-->click on Thread Tools>mark as solved)

---

