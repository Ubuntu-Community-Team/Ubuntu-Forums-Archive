---
title: "Another Dual Boot Thread"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by impreziv on 2009-12-02
I am having some trouble getting my dual boot system to work properly...

Facts:
1) I have Windows 7 64-bit RC1 installed on a 300GB VelociRaptor drive.
2) I have Ubuntu 9.10 installed on a 74GB VelociRaptor drive.
3) The 300GB hard drive has 2 partitions, the Windows 7 and a System Reserved.
4) The System Reserved partition contains the bootmgr and boot folder.
5) My GRUB bootloader works loading Ubuntu, but doesnt work loading Windows 7.
6) When I try to load Windows 7 it says that BOOTMGR is missing, but I have checked the System Reserved partition and it is there.
7) I can boot into Windows 7 fine if I place my 300GB drive first in the boot order in my BIOS and to the GRUB if I put the 74GB drive first.
**Please ignore the 500GB drives as they are storage only.**

My fdisk -lu
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92824e89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976762879   488380416    7  HPFS/NTFS

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b090b09

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   139363874    69681906   83  Linux
/dev/sdb2       139363875   145211534     2923830    5  Extended
/dev/sdb5       139363938   145211534     2923798+  82  Linux swap / Solaris

Disk /dev/sdc: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf72aa317

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2          206848   586070015   292931584    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92824e89

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   976762879   488380416    7  HPFS/NTFS

```My menu.lst
```

...
## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        ee58f0d7-8a23-418b-a4f1-9d290418c7ce
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=ee58f0d7-8a23-418b-a4f1-9d290418c7ce ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        ee58f0d7-8a23-418b-a4f1-9d290418c7ce
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=ee58f0d7-8a23-418b-a4f1-9d290418c7ce ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        ee58f0d7-8a23-418b-a4f1-9d290418c7ce
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ee58f0d7-8a23-418b-a4f1-9d290418c7ce ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        ee58f0d7-8a23-418b-a4f1-9d290418c7ce
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ee58f0d7-8a23-418b-a4f1-9d290418c7ce ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, memtest86+
uuid        ee58f0d7-8a23-418b-a4f1-9d290418c7ce
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


#Windows 7
title Windows 7
rootnoverify (hd2,0)
savedefault
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

```I have tried everything that I can think of to get this to work. It seems to me that if I can load Windows when I boot off the 300GB drive and then load Ubuntu when I boot off the 74GB drive then there is no reason that it shouldn't load Windows when I try to start it from the GRUB.

---

### Post by oldfred on 2009-12-02
Drive order in Grub, windows and Ubuntu may not be the same as BIOS. The order is see may indicate that your windows is drive 3?

This is an upgrade to 9.10 so you still have old grub correct?

title Windows 7
rootnoverify (hd3,0)
savedefault
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1

---

### Post by impreziv on 2009-12-02
Yes, this is an upgrade to 9.10. Does it not upgrade my grub as well. How can I go about upgrading my grub bootloader if it hasn't been? I am in class so I'm going to have to try your suggestion when I get home. I am almost positive, however, that my Windows 7 drive is drive 2 because I don't think it would tell me that the bootmgr is missing if I was booting the wrong drive. Wouldn't it tell me that there was no operating system instead? I could be wrong, I'm not an expert on grub :P

---

### Post by Megafag on 2009-12-02
> **impreziv said:**
> Yes, this is an upgrade to 9.10. Does it not upgrade my grub as well. How can I go about upgrading my grub bootloader if it hasn't been? I am in class so I'm going to have to try your suggestion when I get home. I am almost positive, however, that my Windows 7 drive is drive 2 because I don't think it would tell me that the bootmgr is missing if I was booting the wrong drive. Wouldn't it tell me that there was no operating system instead? I could be wrong, I'm not an expert on grub :P

dont upgrade. grub2 sucks.

---

### Post by impreziv on 2009-12-02
> dont upgrade. grub2 sucks.

lol good thing I am in class or else I would have done it without hesitation.

---

### Post by presence1960 on 2009-12-02
```
title        Windows 7
rootnoverify (hd[COLOR="Red"]3[/COLOR],0)
savedefault
map          (hd0) (hd[COLOR="Red"]3[/COLOR])
map          (hd[COLOR="Red"]3[/COLOR]) (hd0)
chainloader  +1
```

Note the entries in red. GRUB 0.97 (Legacy) uses (hdx,y) where x = device & y = partition. Numbering for both starts at 0. But the x designation is determined by the order of your disks in BIOS not fdisk. So what you want to do is go into BIOS and see what position in the hard disk boot order your 300.1 GB disk is. If it is second changes those red #s to a 1, if it is fourth change them to a 3. 

If you aren't sure report back the order of your hard disk boot in BIOS and we'll tell you what to edit in menu.lst

---

### Post by impreziv on 2009-12-02
> **presence1960 said:**
> ```
title        Windows 7
rootnoverify (hd[COLOR=Red]3[/COLOR],0)
savedefault
map          (hd0) (hd[COLOR=Red]3[/COLOR])
map          (hd[COLOR=Red]3[/COLOR]) (hd0)
chainloader  +1
```Note the entries in red. GRUB 0.97 (Legacy) uses (hdx,y) where x = device & y = partition. Numbering for both starts at 0. But the x designation is determined by the order of your disks in BIOS not fdisk. So what you want to do is go into BIOS and see what position in the hard disk boot order your 300.1 GB disk is. If it is second changes those red #s to a 1, if it is fourth change them to a 3. 

If you aren't sure report back the order of your hard disk boot in BIOS and we'll tell you what to edit in menu.lst

Awesome. Thank you very much! I checked the boot order in my BIOS, adjusted the code accordingly and it worked!

---

### Post by presence1960 on 2009-12-02
> **impreziv said:**
> Awesome. Thank you very much! I checked the boot order in my BIOS, adjusted the code accordingly and it worked!

Great! Glad you got it working, enjoy ubuntu. Don't forget to thank oldfred too!

---

