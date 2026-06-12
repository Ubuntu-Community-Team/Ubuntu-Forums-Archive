---
title: "Installation alongside Win8"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by gennoz on 2012-10-05
I have burnt an installation CD for Ubuntu 12.10 and started the installation process, My PC, Sony Vaio S series on i7, has windows 8 CP installed since March, So all my data, etc... are really being used, not just a testing win8 for me.

I am looking forward to install ubuntu 12.10 besides win8 (I have another PC and it has windows XP and Ubuntu 12.10 working flawlessly together)

The options on my PC with win8 while installing is different than what i have seen with XP, I only have replace windows8 with Ubuntu.

How can I dual boot??! is there any solution for this? (I ve tried my best searching before posting this here).

---

### Post by Sylos on 2012-10-05
Hello there.

I havent tried to do what you are proposing but a quick google search seems to suggest that the installer doesnt recognise the win 8 partition properly so it cant re-size it and allow you to install besides. See:

[http://www.forumswindows8.com/tutorials/how-dual-boot-windows-8-ubuntu-6177.htm](http://www.forumswindows8.com/tutorials/how-dual-boot-windows-8-ubuntu-6177.htm)

I suspect you need to use windows tools to resize itself and make a new partition. Then you should be able to install to that from the Ubuntu CD. You might also want to watch out for boot loader issues (i've read that newer windows versions can be very picky).

MOST OF ALL - BACK UP EVERYTHING BEFORE YOU MESS WITH PARTITIONS.
And make yourself a repair disk using the windows utilities so that if things go wrong you can get back you system.

Cheers

---

### Post by Wim Sturkenboom on 2012-10-05
In windows, check how many partitions you currently have and how they are organised. You can use disk management for it (if that still exists in Win8 :D)

---

### Post by Mark Phelps on 2012-10-05
> **gennoz said:**
> I have burnt an installation CD for Ubuntu 12.10 and started the installation process, My PC, Sony Vaio S series on i7, has windows 8 CP installed since March, So all my data, etc... are really being used, not just a testing win8 for me.\
Consumer Preview is a really OLD version. If you're really serious about using Win8, you should be running the Release Preview, or even better, the RTM version.

> How can I dual boot??! is there any solution for this? (I ve tried my best searching before posting this here).
One important thing is NOT to use the Ubuntu installer to shrink down the Win8 partition to make room.  Like with Vista and Win7, that risks corrupting the Win8 filesystem and rendering it unbootable.  Instead, use the Win8 Disk Management utility.

Also, you should be reading a Windows 8 forum for advice -- if you're serious about using it.  Suggest eightforums.com.

---

### Post by oldfred on 2012-10-05
Is system configured as BIOS/MBR or UEFI/gpt? The Ubuntu 64 bit installer will work with either, but must be installed in the same mode.

If BIOS you may have the 4 partition limit issue with MBR partitioning.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by gennoz on 2012-10-05
Thanks all for replying back, i appreciate it a lot!

I had one partition that can be seen by windows, so i used win 8 disk utility as requested, created a virtual 50GB hard disk.

I  attached a print screen of what i have on win8 PC now.
Please let me know your opinion, should i go on and reload the CD and try installation or what i have done is nonsense?

---

### Post by oldfred on 2012-10-05
You use Windows to shrink the NTFS partition, but you should use gparted to create Linux partitions if partitioning in advance. Linux does not work in NTFS partitions (except wubi) and needs Linux formated partitions to support ownership & permissions.

Do not understand the virtual drive that Windows has created. 

Post screeen shot from gparted with Ubuntu liveCD.

---

