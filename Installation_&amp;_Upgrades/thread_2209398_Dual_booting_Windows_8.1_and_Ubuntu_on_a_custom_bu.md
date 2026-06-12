---
title: "Dual booting Windows 8.1 and Ubuntu on a custom build?"
date: 2014-03-05
forum: Installation &amp; Upgrades
---

### Post by pyrogoggles on 2014-03-05
Hey. I wanted to know if I could dual boot Windows 8.1 and Ubuntu 13.10 on my custom built PC. I've done this previously on the same PC with Windows 7, and all I had to do was shrink the Windows partition, and then I put the Ubuntu partitions in the empty space. Would I still be able to do the same thing with Windows 8.1, or has Windows 8.1 permanently screwed me? Thanks for the reply, if anyone does reply.


Also, specs.

My motherboard is an ASUS P8Z77-V LX with the Asus UEFI BIOS. Had no problems installing Ubuntu before with the BIOS.

My HDD is a WD 500GB.

Thanks!!!

---

### Post by oldfred on 2014-03-05
If you installed Windows 7 in your system in BIOS boot mode, hard drive is MBR(msdos).
Both Ubuntu and Windows only boot from MBR with BIOS, so do not boot any installers with UEFI as that is how it will try to install. 
Windows 7 had to be converted to a flash drive from DVD and some updates to make it UEFI compatible.
How you boot installer is how it install and Ubuntu now offers both UEFI & BIOS from the live installer. I think Windows does now also, but have not installed Windows 8.

You will need to keep fast boot off.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by pyrogoggles on 2014-03-05
You may not know if there is, but would you happen to know if there is a way I can revert to Windows 7? I only won Windows 8.1 in a giveaway, I just want to revert.


I do have a Windows 7 Home Premium disc, though. Could that work to downgrade?

---

### Post by pyrogoggles on 2014-03-05
[http://learnedstuffs.wordpress.com/2013/12/13/dual-boot-windows-8-1-and-ubuntu-13-10-for-computers-with-uefi/](http://learnedstuffs.wordpress.com/2013/12/13/dual-boot-windows-8-1-and-ubuntu-13-10-for-computers-with-uefi/)

Would this work? This is what I wanted to do, but no one seems to understand that there has to be a simpler way.


Also, I wanted to install [SIZE=3][FONT=arial black]**Ubuntu 13.10.**[/FONT][/SIZE]

---

### Post by oldfred on 2014-03-05
Do you want BIOS boot or UEFI boot, major differences between the two.
If you do want UEFI and Windows 7, you have to convert DVD to flash drive and make changes to be UEFI capable.

But UEFI has to have gpt partitioning. With MBR you can only boot with BIOS.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by pyrogoggles on 2014-03-05
I want UEFI boot, like I did when I had Windows 7.


Could I install Ubuntu 13.10 with UEFI while keeping Windows 8.1?

Also, I don't care at all about GPT or MBR.

---

### Post by oldfred on 2014-03-05
You have to care about gpt or MBR.
With UEFI boot you must have gpt partitioning.
With MBR partitioning you can only boot in BIOS mode.

I do not know a lot about Windows but it has very specific partition requirements. I would back up all data, erase drive and install Windows in UEFI mode.
Then I would turn off fast boot, and use Windows to shrink the NTFS partition & reboot so it can run its chkdsk.

Then install ubuntu into the unallocated space you have created.

Lots more details in link in my signature.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

