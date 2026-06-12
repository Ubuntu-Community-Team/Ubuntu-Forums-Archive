---
title: "Install on Samsung Netbook NC110"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by Packwood1 on 2012-01-27
[FONT=Verdana][SIZE=2]I am ready to install Ubuntu 11.10 on a Samsung NC110 netbook, but reading other posts leaves me with a few concerns.

Here is my current Partition table.

Partition   File System   Label   Size   Flags
/dev/sda1   NTFS   SYSTEM   100MB   boot
/dev/sda2   NTFS   WIN7 (C)   67GB
unallocated      5MB
/dev/sda4  extended   147GB   lba
  /dev/sda5   NTFS   Data
  /dev/sda6   linux-swap   4GB
  /dev/sda7   ext4   13.68GB
/dev/sda3   NTFS   SAMSUNG_REC   diag
unallocated   5MB

I have created sad5, sda6 and sda7.  All the other partitions were as supplied although I shrunk sda by 20GB to create space for Ubuntu.  I want to install Ubuntu to sda7.  However I do not want to disturb sda3 the Samsung recovery partition.  This is accessed on Boot via the f4 key.

Reading various posts there seems to have been issues with the installation corrupting the MBR.  How can I avoid this?

I started the installation and stopped at the step where it asks for the "Device for bootloader installation".  What should I select here?

Has anyone succesfully installed Ubuntu on this netbook?

Thanks.
[/SIZE][/FONT]

---

### Post by zvacet on 2012-01-30
Install Ubuntu on sda7 as you planed and I think right answer for device is sda.That way grub will become your bootlader.You will be able to boot both OS.

---

### Post by Packwood1 on 2012-01-31
That was my initial thought.  

However my concern is that making Grub the bootloader on sda will overwrite the MBR and then make sda3 (the Win7 Recovery partition, accessed through the F4 function) inaccessible at start up.

Thnaks.

---

### Post by zvacet on 2012-01-31
Grub should be able to see all partitions,but you can also try Easy BCD [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

---

### Post by Packwood1 on 2012-02-02
Thanks, the EasyBCD solution worked fine.  I put 11.10 on sda7 and Grub in the same partition.  Just needed to create an entry with EacyBCD to provide the start menu for Ubuntu.

---

