---
title: "problem with ubuntu 32bit dualboot from win 7 64bit"
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by nauzthiraf on 2012-10-03
Desktop specs--> Acer X3990 , intel i3, 500gb hdd, ddr3 2gb

I have win 7 64bit. i dualbooted ubuntu 11.04 on it.
I have a partition created long ago which i didnt use and want to install it with ubuntu.

I successfully installed ubuntu 11.04 32bit on it, but NOW i can't boot into my windows 7.
Maybe i messed with the swap area and win 7 boot loader, which i kinda forgot during the installation. Or i just did "formatted" my windows 7 partition with ubuntu. 
I just can't boot into my windows 7 from grub, the error is something like "insert CD blabla" . maybe the bootloader is wrong or whatever.

Here is the "sudo fdisk -l"  [http://paste.ubuntu.com/1259301/](http://paste.ubuntu.com/1259301/)

I dont know what is that, 
and this fdisk just show me the 250gb hdd from 500gb , i believe my windows 7 partition is something like 220-250gb. 

I DO HOPE I DIDNT FORMATTED my windows 7 with ubuntu :( :( :(

any help? pleaseeeeeeee...

---

### Post by oldfred on 2012-10-04
Your partitions are showing as SFS or dynamic partitioning. I thought Ubuntu did not even attempt to install to that. In Windows you tried to create more than the 4 primary partitions. Windows then converts to dynamic not the extended partition with logical partitions.

Windows recommends backing up everything, erasing drive & then reformating to get back to MBR(msdos) or basic in Windows type partitioning.

The tools that used to be free are getting converted to pay. Not sure now if conversion from dynamic is still in free versions or not.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by nauzthiraf on 2012-10-04
Thanks, but first of all, i wanna know, does my windows 7 is still there? or its been formatted with ubuntu ?

---

### Post by oldfred on 2012-10-04
The SFS partitions probably contain your Windows, difficult to tell as again it has been converted to a proprietary partitioning scheme that Linux cannot parse.

You can try Windows repair tools, some work, but we have also seen users not be able to repair some systems with dynamic partitions.

If sda4 was your Main Windows or c: then it is now showing as Linux. Not sure if just reformated or fully installed?

The sda3 looks like a typical size for the Windows 7 boot partition and normally the main c: drive is just after that. The unknown partition may have been your vendor recovery?

Testdisk is in the repository, so you can download it into the Ubuntu liveCD or USB and is one many Linux RepairCDs. It may show old partitions and let you recover some data. But if Linux files overwrote your main Windows install then it will not be fully recoverable.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

