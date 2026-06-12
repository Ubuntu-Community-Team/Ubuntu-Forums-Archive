---
title: "USB drive does not boot after update"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by keepertoad on 2007-12-29
Have been running Edubuntu on a usb drive for my granddaughter.  has always booted normally.  After recent update grub could no longer mount th boot partition.  grub menu appears normally.  Interestingly, it will not boot the install of Ubuntu on the internal hard drive either.  Grub is installed on the usb drive.

Tried reinstalling grub with identical results.  have confirmed menu.lst entries are correct including UUID and magic number.

Any thoughts appreciated.  BTW, removing usb drive and booting Ubuntu from internal drive works just fine so it is definitely something that changed on the USB drive during update.

Also, once Ubuntu is booted from internal drive, usb disk can be mounted and read with no issues.

---

### Post by meierfra on 2007-12-29
Do you get any error messages?
Post the output of "sudo fdisk -l" and "sudo blkid".
Also post the relevant parts of "menu.lst" 
Do you have a  menu.lst on the internal and one the external drive?
Do you have a separate boot partition?

---

### Post by keepertoad on 2007-12-29
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f8bf3e4a-e103-490e-bd08-41e134acd55f ro quiet splash noapic
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f8bf3e4a-e103-490e-bd08-41e134acd55f ro single noapic
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

bmcclure@hplaptop:~$ sudo fdisk -l
[sudo] password for bmcclure:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sda2            8925       12954    32370975    5  Extended
/dev/sda3           12955       14462    12113010    c  W95 FAT32 (LBA)
/dev/sda4           14463       14593     1052257+  d7  Unknown
/dev/sda5            8925        8936       96358+  83  Linux
/dev/sda6            8937        9544     4883728+  83  Linux
/dev/sda7            9545        9606      497983+  82  Linux swap / Solaris
/dev/sda8            9607       12954    26892778+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28f12a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

bmcclure@hplaptop:~$ sudo blkid
/dev/sda1: UUID="5C27FDCF2176638D" LABEL="WINXP" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="3EC6-2E70" TYPE="vfat" 
/dev/sda4: UUID="A0B0ED02B0ECE030" TYPE="ntfs" 
/dev/sda5: UUID="e161a8ea-28d6-4ad9-850c-b2e0c9a0b84c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="9fe423ab-48fe-4f1a-b7b2-74b376249653" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="7869bba3-5954-410a-97be-82ea894e90a0" 
/dev/sda8: UUID="f8eec745-c494-492d-8c6e-5f6dbb0f5214" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="f8bf3e4a-e103-490e-bd08-41e134acd55f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="776b0c36-f7a8-48a6-b2cf-21c2029bafe0" 

Yes, grub on both drives and both have /boot partition.  Error 17 which I think is cannot recognize filesystem type.  

Thanks for prompt response.

---

### Post by keepertoad on 2007-12-29
Ooops.  Responding to my own post, the external drive does not appear to have seperate /boot partition.

---

### Post by meierfra on 2007-12-29
Just to make sure:  Then the external drive is plugged in, the computers boots from the external drive. The Grub menu which appears is  from the external drive.  And the  the part of "menu.lst" which you posted is from the external drive.
If that is correct, then:

Change all  "root (hd1,0)" to "root (hd0,0)" in the menu.lst on the external drive
Also change  " #groot (hd1,0)" to "#groot (hd0,0)".

This should let you boot in Edubuntu.

---

### Post by keepertoad on 2007-12-30
Thanks a million, that worked.  When I reinstalled Grub the external drive was mounted as /dev/sdb hence the erroneous reference to (hd1,0).  Still curious what in the last batch of updates changed Grub...but that's another day.

Thanks again.

---

### Post by meierfra on 2007-12-30
> Still curious what in the last batch of updates changed Grub.

It that "#groot (hd1,0)"

The # in front means that Grub ignores it. So often  people edit the "root (hd?,?)"  statements in "menu.lst" but do not change "groot (hd?,?)". Well, Grub ignores groot,  and everything is working fine.

During kernel updates "menu.lst" is rewritten via the command "update-grub". update-grub looks at "#groot" to determine what "root" is supposed to be.  So if groot is wrong all  the  roots are going to be wrong afterwards.

You can easily test this:  Just change "#groot (hd0,0)" to say "#groot(5,7)" in menu,lst, type "sudo update-grub" in the terminal and see that happened to "menu.lst"

---

### Post by keepertoad on 2007-12-30
Aha!  Education is a wonderful thing.  Thanks again for the info.  Now, to solve intermittant USB device mounting.

---

