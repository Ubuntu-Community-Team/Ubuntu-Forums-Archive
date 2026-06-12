---
title: "[ubuntu] Windows 7 Dual boot installation 12.04 LTS"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by dtgee on 2013-06-24
Hi, so I've been trying to install a dual boot of Windows 7/Ubuntu for a while now. I've ran into so many problems that I've just become sick and tired.

The problem I'm currently having is that when I try to install Ubuntu, my Windows 7 operating system isn't detected. I read up on this and looked around. It turns out I needed to run something like

> sudo apt-get install gdisk
sudo fixparts /dev/sda

I tried installing the FixParts package when I ran Ubuntu from a LiveCD, but it gave me an error message saying "E: unable to locate package gdisk" even though I've already installed FixParts.

I'm completely a noobie with Linux, and I feel like even if I fix this problem, I'm going to run into another problem (mainly the black screen problem that I read about since I have a switchable graphics card, but maybe it's already fixed somehow). I read that you can just install Ubuntu using Wubi. Should I just install Wubi instead and try to install Ubuntu from there? I feel like:

1. I won't run into as many problems using Wubi
2. It will fix the problem I current have above
3. LiveCD also takes quite a bit to time to reboot each time (I reboot into Windows to look for some help)

Also, I already shrunk my NTFS drive. If I install Wubi would I need to expand my volume again and shrink from the Wubi installer?

Thanks for any help. It is greatly appreciated.

---

### Post by oldfred on 2013-06-24
Is your system UEFI? Then you should not run fixparts.
Only if you had a gpt partitioned drive from Ubuntu and then installed Windows in MBR mode would you need fixparts.

Wubi does not work on gpt partitioned drives or any UEFI system as that has to have gpt partitioning.

Most Windows 7 systems were installed with BIOS & MBR (msdos) partitioning. But they usually are configured to use all 4 primary partitions so you have to delete one to get Ubuntu to install.

Post this from liveCD terminal:
       sudo parted /dev/sda unit s print

---

### Post by dtgee on 2013-06-24
It tells me:
> Error: can't have a partition outside the disk

---

### Post by baletka on 2013-06-24
If you type bcdedit in windows 7 administrative cmd, it shows some records. If path ends in .efi it's run as efi and if it ends with .exe it's in legacy mode. Should help others solve your problem.

EDIT: IIRC when I installed ubuntu after windows 7 that booted with uefi, it didn't detect windows either. You just have to make sure you don't install it on the same partition.

---

### Post by dtgee on 2013-06-24
> **baletka said:**
> If you type bcdedit in windows 7 administrative cmd, it shows some records. If path ends in .efi it's run as efi and if it ends with .exe it's in legacy mode. Should help others solve your problem.

EDIT: IIRC when I installed ubuntu after windows 7 that booted with uefi, it didn't detect windows either. You just have to make sure you don't install it on the same partition.

The path ends in .exe. Does legacy mode mean nothing unusual is going on?

---

### Post by oldfred on 2013-06-24
Then you should be booting with BIOS and have MBR partitioning. 

Where are you getting this error? If from liveCD that is standard.
 Error: can't have a partition outside the disk 

But if from hard drive we need to make repairs. Then we may be back to fixparts but not gdisk. Or perhaps testdisk.

Post these as we need it to see what you should do.
sudo parted /dev/sda unit s print
sudo fdisk -lu

---

### Post by dtgee on 2013-06-25
> ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Error: Can't have a partition outside the disk!                          
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbf410cf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600  1194852351   597221376    7  HPFS/NTFS/exFAT
/dev/sda3      1430855680  1464951284    17047802+   7  HPFS/NTFS/exFAT
/dev/sda4      1464936448  1465160129      111841    c  W95 FAT32 (LBA)



These are the results wrapped in code tags.

---

### Post by oldfred on 2013-06-25
255 heads, 63 sectors/track, 91201 cylinders, total 14651[COLOR=#ff0000]49168[/COLOR] sectors
/dev/sda4 1464936448 14651[COLOR=#ff0000]60129 [/COLOR]111841 c W95 FAT32 (LBA)

What is sda4. If you have no data in it, just delete it.
Otherwise fixparts is the correct tool to resolve it as it will make the last sector in sda4 be the same as the last sector on the drive.

First backup partition table and save to another device
sudo sfdisk -d /dev/sda > parts_sda.txt

      
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by dtgee on 2013-06-25
Sorry, I'm still pretty new to all this, so I need more detailed instructions.

1. I'm not exactly sure what sda4 is myself, I just know that I have partitions for my:
     -C: drive which is around 400~500GB, 
     -Recovery drive [D:], (16GB) 
     -System drive? (200MB)
     -112GB of unallocated space

How can I check which sda corresponds to which drive?

2. How do you back up a partition table and save it to another device?

3. I just learned how to use FixParts (kind of), but I don't know which drive number to input.
My approach is to just open command line in Windows 7 with administrative power, change to the directory fixparts.exe is in, and then type in fixparts #, where # is the drive number.

---

### Post by oldfred on 2013-06-25
I do not know how to run fixparts from Windows, only from Ubuntu.

Normally with Windows sda1 is the hidden 100MB partition, then comes the main install so c: is often sda2. But some systems put recovery first. 

Instructions seem to say in Windows it is just 0:

> 
[LIST]
[*]**Windows**&#8212;Windows disk device references     officially take the form \\.\physicaldrive*#*, where     *#* is a number, as in \\.\physicaldrive0.     Since this is awkward, FixParts supports a simpler specification of     *#*:, as in 0: to refer to the first disk. 
[/LIST]


---

### Post by dtgee on 2013-06-26
These are the results of when I try to use FixParts. Its says it is deleting the partition (sda4 which you were talking about). However, I don't want to make these changes yet because I haven't backed up anything. How do you back up the partition table to another device?

> C:\Users\...\Desktop>fixparts 0:
FixParts 0.8.4


Loading MBR data from 0:


Problem: MBR partitions 3 and 4 overlap!
Warning: Deleting oversized partition #4! Start = 1464936448, length = 223682


MBR command (? for help): ?
a       toggle the active/boot flag
c       recompute all CHS values
l       set partition as logical
o       omit partition
p       print the MBR partition table
q       quit without saving changes
r       set partition as primary
s       sort MBR partitions
t       change partition type code
w       write the MBR partition table to disk and exit

---

### Post by oldfred on 2013-06-26
Did you press w to write the changes.

It says it is deleting that partition, did you back up the partition table. The instructions I posted were from Linux. Also if you had data in that partition did you back that up first also?

---

### Post by dtgee on 2013-06-26
Thank you! I have successfully installed Ubuntu alongside Windows 7. Windows 7 seems to be working fine, but I need to boot Ubuntu and make sure everything is working there correctly.

---

