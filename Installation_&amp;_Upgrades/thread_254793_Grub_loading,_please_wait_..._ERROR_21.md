---
title: "Grub loading, please wait ... ERROR 21"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by sadalmelik57 on 2006-09-10
I took the plunge and clicked on the "install" button.  I left my C drive alone, where XP is installed.  I partitioned my second (slave) hard drive to have 50 gb NTFS for data already stored there, 98 gb for "/" and 2 gb for swap.  

I continued and got the message "The test of the file system with type FAT16 in part #1 of IDE1 Master (hda) found uncorrected errors."  I chose to continue anyway, since HDA1 is part of the "C" drive which I did not intend to change at all.  As far as I know I made no changes to the primary hard drive.  The installation seemed to go smoothly from there.

Upon reboot I get the message "Loading Grub 1.5" followed by "Grub Loading, please wait ... Error 21."  The boot process ends.  I get no option to choose Windows or Ubuntu.  Can anybody venture a guess about what the problem is, and how to fix it?

---

### Post by NetworkGuy on 2006-09-10
> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

It appears that the error you had on your "C: drive" was for real. 

Grub uses the MBR on your first hard drive.  Your error messages were on that drive.  

I recommend you boot your XP CD, enter the recovery mode, then run FIXMBR to get XP working again.  Reboot into XP, then run chkdsk on your "C: drive" and look for any block errors.

---

