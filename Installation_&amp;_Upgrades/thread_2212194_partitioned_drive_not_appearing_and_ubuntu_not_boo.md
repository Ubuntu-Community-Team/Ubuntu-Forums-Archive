---
title: "partitioned drive not appearing and ubuntu not booting"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by michael127 on 2014-03-19
Hi all, this is in relation to my post [http://ubuntuforums.org/showthread.php?t=2212101](http://ubuntuforums.org/showthread.php?t=2212101), after the initial install which now worked I am having a couple issues

So I have installed Ubuntu 13.10 on one of my drives, but when I restart my PC, and I select boot menu (F11) and choose the drive which Ubuntu is installed on, Windows 8.1 still is booting as a priority and I don't know how I can get into Ubuntu.

Also, the disk that I partially partitioned is now not showing (or is showing as Unallocated in Disk Management) while showing the 20gb which I allocated for the Boot section (and other relevant Ubuntu installations), the Swap drive I created, and the remaining 1.8 tb of the drive is saying Unallocated. This has important files on it which I still need, but in "This PC" (Win 8 version of My Computer) it is not showing that drive at all, only when I go to the Disk Management section of Computer Management? Also shortcuts to files on this drive (which was the s:) no longer work.

Any help would be greatly appreciated.

Thanks

---

### Post by Kris_Spencer on 2014-03-21
Windows can't read Linux filesytems. Aslong as the partitions themselves are showing, even if each one says unallocated, they should be fine.

---

### Post by michael127 on 2014-03-21
Yes, but when I go through the boot menu through BIOS and select the drive which it is installed on to boot from, it still launches windows 8.1. I can't actually get Ubuntu to boot (or at least don't know how to).

So part of one of my drives is partitioned for Ubuntu, but the remaining part of the drive now is accessible. After the partition occurred at installation, windows does not have access to any part of that drive, and the part that was not partitioned says unallocated. I can make the part of the partition active, but it says that I have to format the drive, which will cause me to lose ~400gb of files (most of which are potentially recoverable but some will be lost permanently). I figured that as it is a 2tb drive that it wouldn't be an issue reserving some space for Ubuntu, I didn't expect it to make all data on that drive invisible

---

### Post by Mark Phelps on 2014-03-21
I can confirm that Win7 Disk Management WILL show Linux filesystem partitions, just not the contents (as it can not actually read the filesystems).  

If it is showing the space as "unallocated", that is a more serious problem.

Also, you can't make "part" of a partition active. IF whatever tool you are using is allowing you to do that, it has misinterpreted the filesystem information and is, most likely, corrupting it in the process.

So, what is it you really want to do at this point -- recover the data from the former Windows partitions on the drive?

---

### Post by michael127 on 2014-03-23
OK so the update is, I have got ubuntu working (required a "boot-repair"). The files on the 2tb drive (the remaining amount which was not partitioned) I have been able to update to active as it was "unallocated". I am going to attempt data recovery soon, but I have a new "bigger" issue.

The Boot Repair seems to have somehow affected my Windows 8.1 boot, and win 8 no longer will boot...

When I let my computer do a standard boot (where I don't select the Ubuntu boot drive), it comes up with this error

err: disk 'ldm/a3943930-0014-11e3-be69-d43d7ed8930e/Volume1' not found
Entering rescue mode...
grub rescue>

at which point I can enter commands (although not sure what commands to  use, as ls lists the 3 hdd [hd0], [hd1], [hd2] connected to my pc, but  my understanding of terminal is very limited)
This same error occurs if I select my ssd drive from the boot menu.

Here is also the URL for the boot repair [http://paste.ubuntu.com/7141195/](http://paste.ubuntu.com/7141195/)

---

### Post by michael127 on 2014-03-23
I have been attempting for the past week to establish a dual boot PC with Win 8 on my SSD and Ubuntu on my HDD. After Installing Ubuntu and it not working (win 8 working fine still), I ran Boot-Repair to fix the Grub. However since then I have not been able to boot windows (either letting it run through the standard boot process, or even selecting my ssd in the Boot menu). Ubuntu is working fine, but I need Windows far more for software already installed than I need Ubuntu.

When I let my computer do a standard boot or drive specific boot (where I don't select the Ubuntu boot drive and select the Windows Drive), it comes up with this error

err: disk 'ldm/a3943930-0014-11e3-be69-d43d7ed8930e/Volume1' not found
Entering rescue mode...
grub rescue>

at which point I can enter commands (although not sure what commands to  use, as ls lists the 3 hdd [hd0], [hd1], [hd2] connected to my pc, but  my understanding of terminal is very limited)
This same error occurs if I select my ssd drive from the boot menu.

Here is also the URL for the boot repair [http://paste.ubuntu.com/7141195/](http://paste.ubuntu.com/7141195/)

Needless to say I have been freaking out for the last hour trying to find a fix for this, any help would be GREATLY appreciated.

---

### Post by oldfred on 2014-03-23
Boot-Repair does go overboard and install grub to every MBR. You really want to keep your Windows boot loader on sda.
Either use Boot-Repair to install a Windows boot loader to sda. Use advanced options and choose system and then choose drive to install boot loader into.
Or use your Windows repair cd or flash drive to fix your Windows with fixMBR command.

You still with Windows 8 have to have fast boot or the always on hibernation off or you will have issues.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

I see a ldm mention in your error.

 ldm bug grub2 2.00
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

ldm is the Windows dynamic partitions for gpt partitioned drives. But you are not showing the newer gpt drives?

Ubuntu will boot from gpt  partitions. Was drive gpt and Windows dynamic before? Just could be the left over data.  Some Windows third party tools may remove that.

---

### Post by oldfred on 2014-03-23
Duplicate threads merged. Please do not create duplicate threads on the same topic as that dilutes the effort of all the volunteers here in the forum.

---

