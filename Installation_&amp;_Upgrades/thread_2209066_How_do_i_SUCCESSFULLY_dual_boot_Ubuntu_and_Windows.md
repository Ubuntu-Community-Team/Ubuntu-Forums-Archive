---
title: "How do i SUCCESSFULLY dual boot Ubuntu and Windows 7"
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by sonyboyj on 2014-03-03
i make a shrinked volume partition of unallocated space and tryed to install Ubuntu a few times but every time i restart after the installation it always boots into windows i tryed boot repair and don't work. i tryed a older version 12.04 LTS and used install along side and still boots into windows

---

### Post by ubfan1 on 2014-03-03
Assuming this is not a UEFI machine, and the disk partition table is mdsos type, you have a limit of 4 primary partitions.  When you have four, no more primary partitions may be created, no matter how much free space is left on the disk.  To get around this limitition, make the last primary partition an extended partition, then you may make more logical partitions inside the extended partition, and Ubuntu does not care that its partitions are logical and not primary.  The main problem seen is the pc vendor has already used the four primary parititons, so you need to figure out how to convert one to an extended which will include all the free space, then add your logicals.  This can be done manually, but there are tools like partman(? not sure about name), which can make the job easier.  Confirm this is not a UEFI machine, and maybe someone else can suggest a partition tool which does the job easily.  Did the install go all the way through?

---

### Post by oldfred on 2014-03-03
If you have installed:

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

