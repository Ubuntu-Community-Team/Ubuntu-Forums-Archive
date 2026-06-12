---
title: "Server install doesn't recognize drive, Desktop ubuntu does."
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by BobMarso on 2012-07-21
I am trying to install Ubuntu Server 12.04 on the following system:  Intel DP35DP motherboard, two Seagate 1TB drives (sda and sdb), two  Seagate 1.5TB drives (sdc and sdd), and one 3TB Seagate drive (sde).   Using GPartEd from the Desktop Live CD in the "try without installing"  mode, I have written a new MSDOS partition table to each 1TB drive and  created one primary partition and one extended partition.  In the  extended partition I have place logical partitions for Ubuntu Server.   All partitions on both drives have the raid flag set and the intended  boot logical partition has its boot flag set.

I then restart the computer with the server installation CD.  The  computer starts up, goes through the language, network, and user setups,  I tell it to recognize the RAID function, and then does the "detect  drives" step.  However, only sdb, sdc, sdd, and sde are recognized.  The  installer does not recognize sda.  At this point I can set up a RAID0  with sdc and sdd, but I can't set up a RAID1 for the Ubuntu installation  using sda and sdb since it won't recognize sda.  I then switched the SATA ports sda and sdb were connected to.  The problem followed the drive.  I've formatted the drives identically -  any ideas what is happening?  Why is  the Desktop Live CD version of 12.04 able to recognize all drives but the 12.04  server installer can't see one of them?

Thanks for the help

---

### Post by darkod on 2012-07-21
It seems to me there is a mix up. Setting the raid flag marks it as physical device for software RAID.
If the server installer asked you if you want to activate the raid, that means it detected traces or settings of hardware raid (or fakeraid). Unless you are not talking about the Configure Software RAID in the partitioner.

So, first I would make sure there is no hardware raid arrays configured. You might need to press a combination of buttons during boot to enter the raid adapter BIOS. Or the main motherboard BIOS, depending what raid we are talking about.

After that boot into live mode again and remove meta data from all drives one by one with:
sudo dmraid -E -r /dev/sda

using it from /dev/sda to /dev/sde. That will remove meta data on all disks where it will be detected.

After that you can continue. You don't need to redo the disks again, the dmraid command doesn't influence the raid flags.

The server installer shouldn't ask you to activate the hardware raid, only when you get to the manual partitioning step it will show you the partitions marked with the raid flags, and in that step you can configure software raid.

---

### Post by BobMarso on 2012-07-21
Thank you, Darkod, that was the problem.  Running dmraid on sdb fixed the problem.  My server is now up and running.

---

