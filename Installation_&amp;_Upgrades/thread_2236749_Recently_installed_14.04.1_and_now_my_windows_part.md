---
title: "Recently installed 14.04.1 and now my windows partition is no longer recognized."
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by bgq13 on 2014-07-28
First, I would like to say that I'm not a normal ubuntu user. I needed to do something that requires a linux OS so I decided to use ubuntu dualbooted with my windows computer.
I used a USB drive to install ubuntu. When I started the installation I was not given the option to install along side windows so I made the separate partition myself (this may have been where I messed up). Here is a photo of gparted: 

[ATTACH=CONFIG]255128[/ATTACH]

I tried running boot-repair and got grub installed but after restarting I still cant see my windows partition.
Edit: Forgot to add my boot-repair link: [http://paste.ubuntu.com/7888429/](http://paste.ubuntu.com/7888429/)

I'm pretty stumped, any help would be greatly appreciated.

---

### Post by mikewhatever on 2014-07-28
Gparted shows /dev/sda1 and /dev/sda6 are with unknown file system. You may need to use testdisk to recover as others have:
[http://www.absolutelytech.com/2010/09/23/solved-unknown-filesystem-in-gparted-in-ubuntu/](http://www.absolutelytech.com/2010/09/23/solved-unknown-filesystem-in-gparted-in-ubuntu/)
[http://superuser.com/questions/328803/how-can-i-restore-my-unknown-partition-type-back-to-ntfs](http://superuser.com/questions/328803/how-can-i-restore-my-unknown-partition-type-back-to-ntfs)

PS: BootRepair is used for different sort of problems.

---

### Post by oldfred on 2014-07-28
That swap is unknown is normal if you encrypted /home. As then swap is also encrypted and no tools can see encrypted partitions (as they should not).

But that you cannot see sda1 is an issue. Partition table says it is NTFS, so you should not need testdisk to recover it as it exists. But it cannot mount it. Or was it also encrypted?

Main reasons are that you resized and it has not yet run chkdsk or you left it hibernated. And if Windows 8 fast boot means always hibernated and that has to be turned off if dual booting. 

 Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

You may need to run chkdsk from your Windows repairCD or flash drive or boot into Windows and turn off fast boot. You may have to temporarily reinstall the Windows boot loader from your Windows repairCD so you can boot and maybe use f8 to get into Windows repair console as it may not boot.

Boot-Repair can reinstall a Windows type boot loader and reinstall grub after you have fixed Windows.
Grub2 only boots working Windows.
And to get grub to find a working Windows after reinstalling grub and rebooting into your install, run this.
sudo update-grub

---

### Post by bgq13 on 2014-07-28
Thanks for the response, I checked out testdisk and my windows partition seems to be damaged. My only option is to rebuild to boot sector, but I'm not sure what that means for my windows partition and what the consequences may be.
After reading more threads, my guess is that my windows partition is encrypted.

Also, im running windows 7 so I don't think that fast boot is an issue.
```
sudo fdisk -lu /dev/sda

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe5b7660f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   397248511   198623232    7  HPFS/NTFS/exFAT
/dev/sda2       397250558   500117503    51433473    5  Extended
/dev/sda5       397250560   426545151    14647296   83  Linux
/dev/sda6       426547200   442169343     7811072   82  Linux swap / Solaris
/dev/sda7       442171392   500117503    28973056   83  Linux
```

Before installing ubuntu I did resize my partition using the windows disk manager. Do you think this is why I'm having this problem? And if so, what would be the safest approach.

---

### Post by oldfred on 2014-07-28
I doubt that it is encrypted, as then you would have to have a separate Boot partition for Windows.

If it says Boot sector is damaged, testdisk can restore the backup if that is not damaged.  If both are damaged then you have to run chkdsk or use Windows repairCD to fix the Windows boot sector.

 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by bgq13 on 2014-07-29
That sounds like a good fix. Unfortunately I don't have a Windows 7 install disk or repair CD now, is there any way of booting into the Windows Recovery Environment without one? I tried to use a free windows 7 iso and mount it on a usb drive like I did to install ubuntu but have failed to find a program on ubuntu that will do this.

---

### Post by oldfred on 2014-07-29
You would have to boot ISO from BIOS not from Ubuntu.

You should always have a repairCD or flash drive for the current version of every install.

Boot-Repair can install a Windows boot loader and you can see if f8 gets you into repair console. From grub it is just about impossible as you have to hit f8 almost the same time as you press enter on grub menu for Windows.

Some third party Windows tools may do some repairs.
       EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

---

