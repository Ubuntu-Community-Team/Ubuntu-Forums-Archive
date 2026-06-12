---
title: "Booting my new ubuntu install = &quot;GRUB GRUB GRUB GRUB GRUB&quot; etc."
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by will0957 on 2007-01-13
I've got 4 hard drives. 2x 160gb SATA drives, 2x 300gb ATA drives. All 4 drives were formatted, and I installed ubuntu on one of the 300 gig drives (the IDE master, drive 0 as the installer recognized).

When i boot up after the install, i just get "GRUB" looping over and over. 

I've reinstalled honestly a dozen times a least (trying different configurations with these drives), with no luck. I've followed instructions on this board to reinstall grub to the MBR, which didn't change anything.

menu.lst
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

```

device.map (my install is on /dev/hda)
```

(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda
(hd3)   /dev/sdb

```

/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=56ef1b08-6e5b-4a1d-9741-c7000e107eba /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=dcd8634b-85d6-4425-a013-85b5f96877a0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

What am I doing wrong? This is starting to become very frustrating.

edit: I did some google searching and found that a possible cause for this may be having the BIOS auto-detect hard drives, and the solution is to turn that feature off and specify what they are so it doesn't need to detect them. My bios (my mobo is DFI ultra infinity) either allows auto detect to be on, or no drive to be specified. So, basically, if I have auto detect off I have no hard drives. 

Anyone have any ideas?

---

### Post by logos34 on 2007-01-13
I wish I had some brilliant insight into your problem seeing as you've knocked yourself out trying to get ubuntu installed (only a dozen times?)...But is there any possibility your iso download is corrupt or you got a bad cd burn?  Maybe you verified the md5sums and burned it slowly (4x or less) and did the cd integrity test, in which case I don't know what to suggest (try Supergrub restore?).  But if you didn't, well, the smallest errors can cause all kinds of strange problems.

---

### Post by will0957 on 2007-01-13
Well, I figured out the problem... figured I'd post it in case someone else comes across the same problem. 

Auto detect in my BIOS didn't need to be off. I turned that back ON. In the same section (right below "auto detect") in my bios was a field called "Access Mode". It was set at the default "CHS" for both drives. I changed both of them to auto. Problem solved.

---

