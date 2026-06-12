---
title: "&quot;install alongside windows&quot; deleted, possibly erased windows partition"
date: 2013-12-17
forum: Installation &amp; Upgrades
---

### Post by willthingy on 2013-12-17
After previous installation failures(described further below), I finally had the option to install ubuntu alongside windows. I proceeded with that, and upon boot, there were no partitions found. Using a livedisk, i ran boot-repair, and now grub shows up, giving me the option to boot into ubuntu.

Previously, my 1TB hard drive had this layout:
partition 1: 100mb system reserved
p2: 850gb NTFS, windows partition
p3: 8.5 gb free space
p4: 140gb linux filesystem, with an older installation of ubuntu

It booted straight into windows 7. no grub, even though ubuntu was installed to part4.


After the latest ubuntu install, my 1TB hard drive has this layout:
p1: system reserved(pretty sure grub is here)
p2: 850GB Ext4, **with ubuntu installed, and all the ubuntu files in root, no windows files**
p3: 8.5gb free space
p4:140gb linux filesystem, with an older installation of ubuntu

grub now shows "Ubuntu"(partition 4), and "Ubuntu 13.10"(partition 2), and i'm running off of partition 4.
Not only that, but now my windows recovery cd says "this disk isn't compatible with your version of windows" and shuts down.
Looking in the "files" program in ubuntu, there is no "program files", no "windows", or anything indicative of my files still being there.


What i would like to do, in order of importance(but not necessarily which should be done first):
1. Recover my files.
2. Fix windows OS and be able to boot it.
3. Be able to dual boot windows/ubuntu.



[B]Previous installation failures before all of the above, possibly irrelevant:
[/B]started out with win7. partitions were 100mb system reserved, 850GB windows with NTFS, 30GB truecrypt partition, the rest free space.
"install alongside windows" was not an option. when clicking "something else", the installation only detected 1TB of unallocated space.
I installed ubuntu in the last 140GB, and grub in the first 100MB.
It booted, but would not detect or boot windows.
I tried a number of tools, ntfsfix, testdisk, the one that ended up working was a windows recovery disk from another PC.
the disk detected windows, fixed the MBR and whatnot, booted windows, and then I tried again to install ubuntu, leading to the beginning of my post.



And, here is sudo fdisk -l output:

> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4ecc625d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.




---

### Post by oldfred on 2013-12-17
I am not sure exactly where you are at as the gpt partitioning now confuses it. Windows only boots from gpt partitioned drives with UEFI. Ubuntu can boot from gpt with either UEFI or BIOS.
And both Windows and Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.

Your original partition structure of 100MB boot partition seems like Windows with MBR. With gpt & UEFI the first partition (or near first) must be an efi partition with the boot flag with gpt partitioning.

What does truecrypt have to do with this? Systems will not see that correctly and cause issues. 

Best to see lots of detail.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by willthingy on 2013-12-17
Here you go:
[http://paste.ubuntu.com/6591789/](http://paste.ubuntu.com/6591789/)

iirc, the 100MB partition contained the recovery tools included with my laptop(toshiba satellite p850).

truecrypt was just there before any installations ever happened. again, that last paragraph isn't necessarily relevant to the problem, figured i'd post it just in case.

What other details may i provide?

---

### Post by oldfred on 2013-12-17
The drive has been converted from BIOS/MBR partitioning to BIOS with gpt partitioning. With gpt Ubuntu will boot from BIOS if a small bios_grub partition is added which you now have.
A boot flag was added to the main Ubuntu partition which with gpt makes it an efi partition. An efi partition is only for UEFI boot and should only have the efi boot files in it.
There is no evidence of Windows.
If you have data not backed up, STOP using system. Some recovery tools may get some of your data back, but it is a long slow process. You have to have another large drive with enough space for all the recovered data. Tools like photorec only recover file extensions, so you have to determine correct file names. I had saved some text files many times and photorec found all the deleted copies, but I could not easily tell which was which. Had to do a lot of file compares to last backup and got most of my files back.

I might start with testdisk. It may find old partition table, but now that you have gpt and the old one was MBR (I think) that may confuse it. Not sure which choice you use with testdisk as one of the first questions is if MBR, gpt or some others. If testdisk finds partitions deep search (also slow) may find files with names which you can then copy.
If testdisk does not work then file scan software like photorec may find some data. Some suggest for NTFS Windows tools may work better. You can download and run, but must pay to restore your data if found.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

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

      
 For NTFS 
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - Getdataback often recommended
[http://www.runtime.org/data-recovery-products.htm](http://www.runtime.org/data-recovery-products.htm)

   Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)

IF you did not have a full backup of Windows and/or recovery partition, then you may be able to get a recovery DVD set from your vendor for a nominal charge. Or purchase a full new copy of Windows.

---

