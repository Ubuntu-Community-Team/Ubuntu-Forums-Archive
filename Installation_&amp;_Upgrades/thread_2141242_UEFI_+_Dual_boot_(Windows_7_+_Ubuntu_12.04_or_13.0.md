---
title: "UEFI + Dual boot (Windows 7 + Ubuntu 12.04 or 13.04)"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by Ippo 2001 on 2013-05-02
Hi there, I'm trying to install ubuntu in dual boot with windows 7 on a Lenovo Ideapad Z500. This notebook use UEFI BIOS, but can be settled as legacy support.
I tried different configuration:

1- Bios Set-up: Legacy support, I can install windows 7 ultimate, but when I try to install ubuntu 12.04 or 13.04 I can't put it alongside to windows 7. if I choose other possibility, the program doesn't recognise the NTFS partition and so windows installation. I can only make a new installation of ubuntu deleting windows 7.
2- Bios Set-up: UEFI, I can install ubuntu but not windows 7 that stop during the first step.

The notebook has only one hard drive (1TB), The original O.S. is windows 8. In the Bios boot choice windows there is note that suggest to use UEFI only for windows 8 and for other O.S. Legacy support.

What can I do?

---

### Post by oldfred on 2013-05-02
I believe several users have installed Windows 7 in place of Windows 8 in UEFI mode. But you have to decide if you want UEFI or BIOS to boot.
Both Windows & Ubuntu have to be installed in the same mode, either both UEFI or both BIOS/CSM.
You do have to have secure boot off in UEFI. Then either UEFI mode or CSM/BIOS on. Different systems do it somewhat differently on how you specify that.

If drive was gpt and you install Windows 7 in MBR(msdos), you probably have to run fixparts as Windows only overwrites the primary gpt partition table, not the backup. Then Linux tools see both MBR and gpt and gets confused.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Windows only boots from gpt partitioned drives with UEFI, or from MBR drives with BIOS. 
Ubuntu will boot from gpt drives with either UEFI or BIOS, or from MBR drives with BIOS. But if Windows is UEFI and Ubuntu BIOS you cannot easily dual boot.

Post this:
      
 sudo parted /dev/sda unit s print

---

### Post by Ippo 2001 on 2013-05-02
Thank for your reply, here is the report:

andrea@ubuntu:~$ sudo parted/dev/sda unit s print
[sudo] password for andrea: 
sudo: parted/dev/sda: command not found
andrea@ubuntu:~$

---

### Post by Ippo 2001 on 2013-05-02
Ok I runned fixparts as in the link you posted me. and this is the results.

andrea@ubuntu:~$ sudo fixparts /dev/sda
[sudo] password for andrea: 
FixParts 0.8.4

Loading MBR data from /dev/sda

NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N): y
Erasing GPT data!

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 1953525168 sectors (931.5 GiB)
MBR disk identifier: 0x685C012D
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048       206847   primary              Y      0x07
   2                206848    629352447   primary              Y      0x07
   3             629352448   1258498047   primary              Y      0x07
   5            1258500096   1953521663   logical     Y        Y      0x07

MBR command (? for help):

---

### Post by oldfred on 2013-05-02
It looks like fixparts fixed parts.

I think you left out a space.
sudo parted /dev/sda unit s print

You can copy commands into terminal and paste into terminal.

You are showing 4 NTFS (type 07) partitions. Ubuntu uses Linux partitions. You may have to shrink one partition and expand the extended partition to make room for more partitions.

Use Windows Disk tools to shrink Windows partitions and then reboot. But use gparted or the installer to create partitions for LInux. If you just want / & swap, just make unallocated space and use auto install.

---

### Post by Ippo 2001 on 2013-05-02
hi, before run fixparts I installed ubuntu from windows in the 300GB second partition (30GB of space requested), and then I ran fix parts with the results I posted above. After that i rebooted and everything went well dual boot with windows seven and ubuntu.
Now I want to make a clean installation of both the OS. 
My problem is now if I boot from the DVD with Windows 7 DVD I get a blue screen during the loading files screen.
What's wrong?

---

### Post by oldfred on 2013-05-02
I do not know Windows issues, other than dual booting. 
Do you get error messages?
If DVD is good I do not know.

Have you done a full power down and  cold boot after power was off for a bit. If a laptop remove battery and hold power switch to dissipate energy. Then use one time boot key (f12 on my system) to choose to boot DVD.

---

### Post by Ippo 2001 on 2013-05-03
Hi, the DVD is new, I used it to install windows 7 before fixing the mbr. The system is fresh I started now after one night of sleep :D, the error I get is related to the cache_manager, but looking to the technical information the error code relate to the RAM or hard drive.
what can I do? here is the BSOD image (sorry, it's taken with my cellular)

---

### Post by oldfred on 2013-05-03
Do you have a small SSD with Intel SRT running as cache or was Windows hibernated when you shut it down.

       But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Ippo 2001 on 2013-05-03
Ok I fixed my problem, with fixparts I solved the partition table problem, I deleted GPT and left only MBR. The BSOD during Windows 7 installation was due to some file corrupted in the Filesystem on my hard drive, don't ask me why this influence the installation from the beginning. 
To fix this problem, I run Ubuntu from the live cd, deleted all the partition on the hard drive and then reinstalled windows 7 and ubuntu and now I could choice to install ubuntu alongside windows 7 ...
Thanks to everybody for the support !!!

---

