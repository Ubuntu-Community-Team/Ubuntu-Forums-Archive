---
title: "XP dual boot with vmware linux guest"
date: 2006-05-21
forum: Installation &amp; Upgrades
---

### Post by Eman_Resu on 2006-05-21
I have a Fujitsu T4020 Tablet/Laptop with an internal SATA hard disk.  I have Windows XP on the first primary partition and Windows temp data and page file on the second primary partition.  Then I have a final primary partition for Linux boot and an extended partition with two logical volumes for Linux root and Linux swap.  Grub is installed in the master boot record and I can successfully boot Ubuntu and Windows.

Here begins the problem.  I would like to sometimes boot the Linux installation from within vmware (workstation 5.5) on Windows.  I setup the virtual machine to use the entire raw disc and it begins to boot but hangs when trying to mount the Linux root filesystem.  It is my understanding that SATA drives under Linux receive drive names like SCSI drives (ie /dev/sda) so it seems to me that the vmware virtual SCSI disk device would be seen similarly, but, perhaps I misconceive...

I've searched the forums and have seen examples where Windows is the guest, but, I need the opposite setup.  Is anyone using a dual boot and also running Ubuntu as the guest OS from within vmware on Windows XP?

---

