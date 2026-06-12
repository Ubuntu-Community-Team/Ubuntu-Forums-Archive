---
title: "Trying to install Ubuntu as dual boot on Windows 8.1 desktop"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by stephenesherman on 2014-04-19
I can run Ubuntu 14.04 from a DVD I burned (AMD 64bit), but when I try to install from there, I do not see "Install Alongside ..." only the "Something Else" option.

This is an HP 500-214 Pavilion desktop, with a 64-bit AMD chip, running the latest **Windows 8.1 Update** version. It has a 2TB hard drive, set up with 4 partitions; as these are GPT/GUID, there should be no issue with the old 4 partition limit. I disabled "Fast Startup" from PC Settings, which seems to be the same as disabling "Fast Boot" from the BIOS. AMD has no equivalent to Intel's SRT, so that's not an issue. Secure Boot is also disabled, but I did not intentionally do that. In short - both Fast Boot/Startup and Secure Boot are presently disabled.

Using Windows Control Panel, I shrank the C: drive to 1TB, leaving (approximately) 1TB Unallocated for the Ubuntu Install. 

I would prefer to proceed carefully, let Ubuntu's Installer work for me. **At this point, should the Installer be able to do an "Install Alongside ..."  or must I do  "Something Else,"  specifying 3 Linux partitions: sdb, mount points, ext4, etc.??**

Another question ... The HP chat support guy said that, even if installed on a separate partition, Ubuntu might "corrupt" the Windows MBR. I suspect he means there might be some work to do with the Boot Order, or possibly use the Boot Repair tool. I'm not overly concerned, but would like any thoughts on his warning.

I have been using this page as my main guide:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
So far, I have not yet completed step 4. (Install Ubuntu), and recognize that there may be subsequent boot issues (per step 5.)

Thanks!


_SYSTEM SPECS, PER HP's SUPPORT ASSISTANT TAB_
OS: Windows 8.1 64-bit 
Chip: AMD A8-6500 APU with Radeon(tm) HD Graphics  
Memory: 8GB  Kingston 1600MHz
Graphics device: AMD Radeon HD 8570D 
System board: 2AE0 1.0
BIOS: 80.46
Hard drive: ST2000DM 001-1CH164 SATA Disk Device
 - Drive C: 931.7 GB (701.08 GB free)
 - Recovery Drive D: 15.29 GB (1.9 GB free)
 - Unallocated not shown, about 1TB

---

### Post by Luke M on 2014-04-19
Since your Windows is an EFI install (must be since it's a GPT drive), there is no Windows MBR to corrupt (well, there's an MBR but it's a "dummy" not used for anything).

Be sure that you're booting the ubuntu DVD in EFI mode, not in BIOS mode. Since the DVD supports both, you could be getting either depending on your BIOS settings and what you select from the BIOS boot menu (if you're using a BIOS boot menu).

I don't know why "install alongside" isn't showing up. I always do a "something else" install.

---

### Post by stephenesherman on 2014-04-20
[ATTACH=CONFIG]252277[/ATTACH]

Luke, Thanks for your help.

I get this screen, so that should mean that I am booting the DVD in EFI mode. Is that correct?

I'd like to use "Install Alongside ..." Any suggestions as to what the problem might be?

If I do a "Something Else ..." how much swap? Twice RAM would be 16GB. Some ppl say "up to a maximum of 8GB" for swap. I'm not worried about space; just want best performance. So .. 8GB, or 9GB, or 16GB??

---

### Post by fantab on 2014-04-20
Can you post the output of the commands below from Live Ubuntu?

```
sudo parted -l
sudo fdisk -l
```

After 'shrinking/resizing' windows partition have run '[chkdsk]("http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html")'? Sometimes a filesystem error in C: can hide Windows from Ubuntu installer.

---

### Post by bradsturtevant on 2014-04-20
I have discovered recently that clicking on 'Try Ubuntu' then clicking on the 'Install Ubuntu' icon in the invoked Ubuntu desktop is a much better way to install in general. Skip that big 'Install Ubuntu' all together. Starting from 'Try Ubuntu' will allow to cancel install, explore and tweek drives, partitions ect. before starting install.

From inside the desktop (before you install) you COULD open up a terminal, install gdisk (the Linux GPT tool) and examine the partitions that Ubuntu/Linux is aware. Before you can 'sudo apt-get install gdisk' you must enable the 'universal' apt-get repository (try google search on that)

---

### Post by oldfred on 2014-04-20
If you get grub menu or black screen that is UEFI boot. If the purple screen with tiny accessiblity icons at bottom of screen for a few seconds that is a BIOS boot.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

You only need larger swap equal to RAM in GiB not GB, if you want to hibernate. And if dual booting best not to hibernate. Then with 8GB of RAM you may never use swap, but having a little is a good idea or maybe 2GB.
      
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Be sure to backup Windows main partition and the efi partition. And make a Windows repair flash drive.
      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by stephenesherman on 2014-04-20
Thanks fantab & brad,

I have gotten this far .... From the Live DVD ---> Try Ubuntu ---> Install Ubuntu ---> Something Else mode ---> (specified partitions as shown below) ---> "Executing grub-install/dev/sda failed."
[B]
Output of sudo parted -l [/B][INDENT]ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  1074MB  1073MB  ntfs            Basic data partition          hidden, diag
 2      1074MB  1451MB  377MB   fat32           EFI system partition          boot
 3      1451MB  1585MB  134MB                   Microsoft reserved partition  msftres
 4      1585MB  1002GB  1000GB  ntfs            Basic data partition          msftdata
 6      1002GB  1043GB  41.0GB  ext4
 7      1043GB  1052GB  9216MB  linux-swap(v1)
 8      1052GB  1984GB  932GB   ext4
 5      1984GB  2000GB  16.4GB  ntfs            Basic data partition          hidden, msftdata


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
[/INDENT]

**output of sudo fdisk -l**[INDENT]ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0b3d4451

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.
[/INDENT]

I also had to change the Boot Order in the BIOS, to put the DVD ahead of Windows MBR. I presume I just move Windows MBR back to the top once things are working.

When the install failed at GRUB, there was a message saying I'd be permitted to file a bug report (presumably with diagnostic info). But I could not close the screen and had to manually shut down. Not sure how to find that diagnostic info.

(Tried to use GParted. It was either stuck or verrrrrrrry slow on Searching Partitions. SO I stopped it.)

I looked in the root partition, and it seems to have all the Ubuntu folders in there. I'm hopeful the system is installed, and just needs some tweaking of GRUB.

---

### Post by oldfred on 2014-04-20
fdisk does not work on gpt partitioned drives. You may want to download gdisk.
sudo apt-get install gdisk

If your EFI partition has ubuntu folder with grub you can try this.
 Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

There are work arounds to get Boot-Repair to work in trusty.
      
  ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)

---

### Post by stephenesherman on 2014-04-20
Thanks all. I finally got dual boot to work. 

There were many false starts and false restarts. But, eventually, here was the process that worked for me: Burn Ubuntu 14.04 DVD. Run that Live. Install from there, using "Something Else .." specifying the 3 partitions in the dialog. The install failed at "grub-install/dev/sda." After trying w/o success to use a Boot Repair CD, then USB, I ran it from within Live Ubuntu (note that there are changes to the terminal commands, for 14.04 version of something in there).  Ultimately Secure Boot had to be disabled.

Running Boot Repair fixed the problem. I have booted up both Ubuntu, am typing this now from Windows. Just in case, the Boot-Info URL is [http://paste2.org/0mtpnmhW](http://paste2.org/0mtpnmhW)

Only advice I can give is "Go slowly, one step at a time. There are many alternative ways to do many of the steps. Try them. Try any one of them 2 or 3 times. Do your best to make sure that the step you're doing is not likely to blow anything up. Also, try to understand as much as possible of the process." (When my Install failed, and it looked like there was NOTHING there, based on research, I had some confidence that Ubuntu system was there, merely couldn't boot.

I wish I could give more disciplined, step-by-step path, but it was too messy, too many false starts.

My thanks to forum members for responding; my thanks to Ubuntu community for maintaining the many useful documentation pages.

I'll mark this issue solved.

---

### Post by prantik007 on 2014-09-10
> **stephenesherman said:**
> Thanks all. I finally got dual boot to work. 

There were many false starts and false restarts. But, eventually, here was the process that worked for me: Burn Ubuntu 14.04 DVD. Run that Live. Install from there, using "Something Else .." specifying the 3 partitions in the dialog. The install failed at "grub-install/dev/sda." After trying w/o success to use a Boot Repair CD, then USB, I ran it from within Live Ubuntu (note that there are changes to the terminal commands, for 14.04 version of something in there).  Ultimately Secure Boot had to be disabled.

Running Boot Repair fixed the problem. I have booted up both Ubuntu, am typing this now from Windows. Just in case, the Boot-Info URL is [http://paste2.org/0mtpnmhW](http://paste2.org/0mtpnmhW)

Only advice I can give is "Go slowly, one step at a time. There are many alternative ways to do many of the steps. Try them. Try any one of them 2 or 3 times. Do your best to make sure that the step you're doing is not likely to blow anything up. Also, try to understand as much as possible of the process." (When my Install failed, and it looked like there was NOTHING there, based on research, I had some confidence that Ubuntu system was there, merely couldn't boot.

I wish I could give more disciplined, step-by-step path, but it was too messy, too many false starts.

My thanks to forum members for responding; my thanks to Ubuntu community for maintaining the many useful documentation pages.

I'll mark this issue solved.

Hey I have the exact same case. Can you please tell me exactly how you fixed it?

---

### Post by WinEunuchs2Unix on 2014-09-11
> **prantik007 said:**
> Hey I have the exact same case. Can you please tell me exactly how you fixed it?

Because he didn't answer you I'll point out that in his post he explicitly regrets he CAN NOT say the exact steps to solve the problem.  I look forward to experiencing the same problems tonight, tomorrow night or this weekend depending on how long research takes.

---

