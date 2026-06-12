---
title: "Need help installing Ubuntu only once."
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by Masterj15 on 2007-03-12
In Need help installing Ubuntu only one time. The reason why I say that is beacuse every time I install ubuntu on a nonlive disk the first time it has a grub error. The error code is 18 which is the code that:

Error 18
Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time. 

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel. 

The kernel it self does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem. 
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot. 

I have no clue of what that means.
Please help me.:confused: :confused:

---

### Post by Kateikyoushi on 2007-03-12
Do you have partitions on the disk ? If no then can create a /boot at the beginning of the drive and it is solved.

What is wrong with the live discs, why do you install from the alternate CD ?

---

### Post by Masterj15 on 2007-03-12
Beacuse I have only 128mb I will try what You said. Thanks

---

### Post by Kateikyoushi on 2007-03-12
Then I understand, if you need help about partitioning just ask.

What you have to do is make a small (256MB will do) /boot partition and set the mount point as /boot, then do the rest of the installation as you did before.

---

### Post by Masterj15 on 2007-03-12
Thanks alot! that really helped. 
If you can ( I will understand if you don't want to) can you help me with another problem. It is in the. Install forum. I need help uninstalling something.:)

---

