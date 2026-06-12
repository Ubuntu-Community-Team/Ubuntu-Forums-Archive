---
title: "Touble with my dual boot!"
date: 2014-06-29
forum: Installation &amp; Upgrades
---

### Post by BGLamb on 2014-06-29
Hello all.

I got a new HD recently and have been having issues getting Ubuntu and Windows working nicely together.

I've done a lot of back and forth, but the current situation is as follows: I have installed Win 8 onto my new HD, and then booted from a Ubuntu CD. I installed Ubuntu, but upon rebooting it just loads straight into Windows. Now, my limited knowledge of these things makes me think that this is because, in order to dual boot, my bootloader must be on the very first partition of my HD (correct me if I am wrong), and I have already installed Windows there. When I boot back off the Linux CD, I can see my Linux partitions, but Windows is telling me that it can't (in fact it believes the whole drive is it's own partition, which seems kinda scary from a data-loss perspective).

Is there a way I can fix this without having to reinstall both Windows and Linux? That would be a big pain as I did a lot of installing programs on Windows, and also when I installed them in the reverse order it wasn't without it's problems either! (I think installing Win after Linux may have overwritten my boot partition or something anyway.)

Any and all help/advice appreciated. I'd love to understand more about what is going on and why. Here is an attached copy of "fdisk" for the disk in question.

> Disk /dev/sdb: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000cf04c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sdb2          718848   437552466   218416809+   7  HPFS/NTFS/exFAT
/dev/sdb3       437553150   500117503    31282177    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sdb5       437553152   491737087    27091968   83  Linux
/dev/sdb6       491739136   500117503     4189184   82  Linux swap / Solaris


---

### Post by oldfred on 2014-06-29
With a BIOS boot you have to have grub in the MBR and can boot Windows from the grub menu.
But with Windows 8 you do have to be careful to turn off fast boot or the always on hibernation. 
Grub really only boots working Windows, so you really need a Windows repair flash drive for those times when Windows breaks.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 

Even if not UEFI better to have Windows 8 flash drive.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Then you can run Boot-Repair to put grub2's boot loader into the MBR of your drive.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

