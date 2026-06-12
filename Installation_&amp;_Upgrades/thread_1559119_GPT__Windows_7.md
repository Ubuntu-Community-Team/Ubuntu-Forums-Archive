---
title: "GPT  Windows 7"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by Emperor_penguin on 2010-08-23
Hello, i like linix but at this moment, tux is getting me headaches .:twisted:

I have install ubunto 10.04 in a 1tb drive, and i have left 280gb of free space, which i was thinking to install windows 7 for just been able to use itunes and steam games:p

Just 5 minutes ago, i have discover i cannot install windows in any of the paritions of the drive, because windows said: cannot be installed in this disk, the selected is a gpt partition style.

Using the disk utility i have discover also that all the partitions in the 1tb hd is using "Linux basic partition style":-x, since im very new using ubuntu, i did not know anything about this.

Is there anything i can do to install w7 without messing with the installation o Ubuntu?

I have 2 others drives, which are using ntfs(formated under windows prior ubuntu), the w7 installation said that i can install it there, but i rather not, because one is just backup and the other one is not as fast as the 1tb drive:-|

Please, help.. getting tired of ubuntu dislike for MBR paritions![-X

Thank you.

---

### Post by zvacet on 2010-08-23
> and i have left 280gb of free space

> i have discover i cannot install windows in any of the paritions of the drive

Why are you trying to instal on partition when you have free space.Did you tried to install on free space (not empty but formated partition)?If yo uhave empty but formated partition,download Gparted live CD from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) and with it first make free space and then you can format it as NTFS and then istall Windows,or you can do the same without formating (just leave unallocated space).Of cource after that you will have to reinstall grub following this.[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Emperor_penguin on 2010-08-23
> **zvacet said:**
> Why are you trying to instal on partition when you have free space.Did you tried to install on free space (not empty but formated partition)?If yo uhave empty but formated partition,download Gparted live CD from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) and with it first make free space and then you can format it as NTFS and then istall Windows,or you can do the same without formating (just leave unallocated space).Of cource after that you will have to reinstall grub following this.[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)


Hi, thanks for replying, i was about to wipe out ubuntu and then re-install windows...

Yes, you are right, i was trying to say, i have unallocated space in the same hd where ubuntu is running, which i was thinking to use it for the windows 7.

So, once i use the Gparted, i formated the unallocated(free space where w7 might be running)  using NTFS? 

I can not install windows 7 because i install ubuntu fist, and in the same drive where the space free is, the partitions are been use a as DINAMIC DRIVE, hence GPT.

there and image below.[IMG]http://yfrog.com/mwscreenshot10tbharddiskap[/IMG]
[IMG]http://yfrog.com/mwscreenshot10tbharddiskap[/IMG][IMG]http://img824.imageshack.us/img824/7830/screenshot10tbharddiska.png[/IMG]
thanks.

---

### Post by srs5694 on 2010-08-23
Windows refuses to install to or boot from a GUID Partition Table (GPT) disk when the computer uses a BIOS. Windows is fine on GPT disks if the computer uses an EFI or UEFI for its firmware, though. Creating a Windows partition and putting NTFS on it will *not* solve this problem. If your system is BIOS-based, you *must* have a Master Boot Record (MBR) partition table.

The easiest solution is to create a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) putting the Windows partition(s) and any shared data partition(s) on the MBR side. Hybrid MBRs are, however, ugly and dangerous, particularly if you don't know what you're doing. The safest solution is therefore to convert the disk from GPT to MBR form. You can do this destructively (wiping out existing partitions) using GNU Parted, GParted, and various other tools; however, be sure to use something that's GPT-aware, or it will leave behind GPT data structures that will almost certainly come back to haunt you. If you want to convert from GPT to MBR without damaging your existing partition(s), AFAIK the only Linux-based solution is my [GPT fdisk.](http://www.rodsbooks.com/gdisk/) See the [Converting to or from GPT](http://www.rodsbooks.com/gdisk/mbr2gpt.html) page of the documentation for details. Be aware that GPT fdisk is intended for intermediate and expert users, not novices. If you attempt this change, you'll need to re-install your boot loader, as well. Also, depending on how many partitions you've got and how they're laid out, it might not be possible to convert all of the partitions.

Another option is to use a second hard disk. Buy a new one and set it up with MBR, keeping GPT on your existing disk. Linux will then boot from the GPT disk and Windows will boot from the MBR disk. Both OSes will be able to access both disks once booted, assuming they've got appropriate filesystem drivers. (In practice, Windows can't read Linux filesystems without special drivers.) I gather there are some GRUB 2 bugs on systems with two disks that use different partition table types, but I don't have a URL handy for the exact workarounds.

---

