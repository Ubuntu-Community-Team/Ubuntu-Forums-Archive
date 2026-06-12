---
title: "GRUB,dual boot,drive setup?"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by bradc28 on 2007-08-12
I have been messing with a dual-boot install that has been driving me crazy. I am guessing I am partitioning the Linux partitions wrong.

I have two drives, hd0 & hd1... I want Ubuntu on a second partition on hd1 as hd0 has all windows crap on it and the first partition on hd1 is multimedia stuff.

No matter what I have done I have had GRUB stage 1_5 errors. I cleaned up the 'error 5' after redoing the partitions and an error (16 or 17) of unsupported partition continues to hang my GRUB loader. How should I segment this second drive so I can get past GRUB into both OSes?

I would like to delete the two linux partitions on hdb and rebuild with a 512mb swap & remainder Ubuntu. ext3 is the right format from what I recall and I manually set the boot flag in fdisk just to see if it made a difference.

I have tried the BIOS on LBA and Auto for both drives.


I currently have fdisk looking as follows:
ubuntu@ubuntu:/media/disk/boot/grub$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9080    72935068+   c  W95 FAT32 (LBA)
/dev/hda2            9081        9733     5245222+   f  W95 Ext'd (LBA)
/dev/hda5            9081        9733     5245191    b  W95 FAT32

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
86 heads, 15 sectors/track, 302885 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1      208090   134217723+   b  W95 FAT32
/dev/hdb2          208091      208866      500520   82  Linux swap / Solaris
/dev/hdb3   *      208867      302885    60642255   83  Linux

grub menu.lst as follows:
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=82056845-53f5-47c1-9eb7-6fc36f94ec2e ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=82056845-53f5-47c1-9eb7-6fc36f94ec2e ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title          Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

and here is the output from grub console:

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1) /boot/grub/stage2 p /boot/grub/menu.l
st "... succeeded
Done.

grub>

---

### Post by logos34 on 2007-08-12
follow the suggestions here:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#16](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#16)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

---

### Post by MQMike on 2007-08-12
You said:

grub> setup (hd1)

It should be (hd0)
And just before that line, it should be:

grub> root (hd1,2)


So, it should read:

grub> root (hd1,2)   #This is your Ubuntu root files (and GRUB files I’m assuming)
grub> setup (hd0)
grub> quit
$ exit


Your menu.lst looks ok, but I’ll have another look at it, too.

---

