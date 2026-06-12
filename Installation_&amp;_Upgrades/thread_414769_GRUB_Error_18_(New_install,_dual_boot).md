---
title: "GRUB Error 18 (New install, dual boot)"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by OriginalGabriel on 2007-04-20
I just installed 7.04 on my Thinkpad and while everything seemed to go okay, once I rebooted I received an "Error 18" during GRUB's load up and am unable to load either Windows XP or Ubuntu.  I pretty much went with the defaults on install (resized my HD to roughly 70% and installed Ubuntu on the freed up space).

My fdisk output is as follows:```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9143    73441116    7  HPFS/NTFS
/dev/sda2   *        9144       12030    23189827+  83  Linux
/dev/sda3           12031       12161     1052257+   5  Extended
/dev/sda5           12031       12161     1052226   82  Linux swap / Solaris
```

Any ideas?  I'd rather not have to format the drive and reinstall XP.

---

### Post by bullgr on 2007-04-20
> **OriginalGabriel said:**
> 
/dev/sda2   *        9144       12030    23189827+  83  Linux

the asterisk means that your active boot partition is the linux partition.
but in ubuntu installation, for default grub installs in winblows partition (MBR).
so, on booting grub can't be found because it's not in linux partition

try to boot from the winblows partition changing the bios boot option and post again the results.

---

### Post by Herman on 2007-04-20
the asterisk means that your active boot partition is the linux partition.

When ubuntu is installed, grub _is_ installed in the _Ubuntu _partition.  :)

A small part of grub, called stage1 is installed in the _hard disk's MBR_. Another part of grub is installed in the next fifteen sectors of the first track of the hard disk, called stage1_5. 
Neither Grub nor Ubuntu touch the Windows partition which does not begin until sector 63 in a typical installation. :)

The MBR is not part of the Windows file system and therefore it is not part of Windows.
I have some computers that have never had Windows in them and they still have a MBR. 
Windows has a boot sector but it does not have a MBR. 
It is not correct to say that Windows has an MBR. :)

Grub error 18 does not always mean what it says, but here's the official Gnu/Grub prognosis for it anyway,
> 18 : Selected cylinder exceeds maximum supported by BIOSThis error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).You might have something wrong with your /boot/grub/menu.lst file or more likely a problem of some kind with the way your hard disk is set up in your BIOS. Make sure have the hard disk detection in your BIOS is set to auto and not on user. Make sure LBA is enabled in your BIOS, and if LBA is already enabled, try switching it to 'normal' mode and see if that helps.

What do your menu.lst entries look like? If you need help would you mind posting the bottom ssection of your /boot/grub/menu.lst file here please? Since you can't boot you'll need to use the Live CD to get this, here's how,                                  [Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")
Regards, Herman :)

---

### Post by OriginalGabriel on 2007-04-20
It doesn't matter which partition I have set to be booted from, I keep getting the same error.  I did a bit of digging and it looks like it might be the fact that Thinkpads have a hidden partition and their own little boot loader (Access IBM)  to be able to access that partition for system restoration.

So, as it stands, I'm still only able to boot off of a LiveCD and, unless anyone has any ideas, it looks like I'll be formatting the drive and starting from scratch this evening.

---

