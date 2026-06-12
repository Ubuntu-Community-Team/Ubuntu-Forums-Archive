---
title: "Installer doesn't recognize Windows 10"
date: 2015-12-15
forum: Installation &amp; Upgrades
---

### Post by thunderbirdje on 2015-12-15
Hello all,

I would love to dual boot my PC windows 10 / ubuntu-12.04.5-desktop-amd64

I am trying this on my Dell latitude e7440.

Sadly, the installer doesn't recognize the Windows 10 installation, thereby only provides the "erase all" or "something else" option.

I've tried:

- turn off fastboot
- EUFI boot USB
- Legacy boot USB
- shrink windows 10 partition and leave the rest as "unallocated"

None of this helped in detecting Windows 10, the last doesn't show up in neither Gparted nor the Ubuntu installer while my SSD disc (256GB) is detected as one unallocated "free" space in Ubuntu (see [http://www.tiikoni.com/tis/view/?id=7c60225]("http://www.tiikoni.com/tis/view/?id=7c60225")) while it is actually shrunk and have half of it as unallocated (Niet-toegewezen) space as seen from the Windows Partition Manager  (see [http://www.tiikoni.com/tis/view/?id=9f8cc5b]("http://www.tiikoni.com/tis/view/?id=9f8cc5b"))

---

### Post by yancek on 2015-12-15
A windows 10 default install will be UEFI so you will then need to install Ubuntu UEFI.  That's the first thing to determine, UEFI and MBR do not mix.
Also, some computers have multiple options for hibernation and fastboot and have different names for it.  Turn off anything to do with hibernation or fastboot before booting the Ubuntu installation medium.  I would not use the "Install Alongside" option as to many possibilities for problems.  You should use Something Else.

---

### Post by deepakdeshp on 2015-12-15
Now Ubuntu LTS 14.04 is available for download and install. Please use 14.04 unless you have some special reasons

[http://askubuntu.com/questions/577481/dual-boot-ubuntu-14-04-with-windows-10](http://askubuntu.com/questions/577481/dual-boot-ubuntu-14-04-with-windows-10)

Some more information with a lot of useful links in the thread

[http://ubuntuforums.org/showthread.php?t=2297428ona](http://ubuntuforums.org/showthread.php?t=2297428ona)

---

### Post by LostFarmer on 2015-12-15
Your display from Disk Management (win10), indicates your install is on a MBR partitioned hdd. There are at least 2 reasons for a partitioned hdd to be seen as having no partitions.  If Win10 was installed on a GPT disk there would be a small fat32 efi partition.

1) if the hdd was changed from GPT to MBR with MS Windows, it does not clear the backup GPT data.  MS windows does not care but linux does.
 in a linux terminal run and post output of (sudo parted -l)  Note: -l is a small L   If it displays a warning about the hdd having left over GPt data, this is the problem.

2) the hdd had a raid setup,  do not know how to tell or what to do.

I do agree you should install the latest LTS version.

---

### Post by thunderbirdje on 2015-12-16
Thank you all so far!

1) Downloading the latest LTS as we speak...
2) @LostFarmer:

> **LostFarmer said:**
> 1) if the hdd was changed from GPT to MBR with MS Windows, it does not clear the backup GPT data.  MS windows does not care but linux does.
 in a linux terminal run and post output of (sudo parted -l)  Note: -l is a small L   If it displays a warning about the hdd having left over GPt data, this is the problem.

Output: [I]ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?   [/I]

Is this the warning saying that a GPT data has been left over? If so, how can it be fixed?

---

### Post by thunderbirdje on 2015-12-16
I have tried 14.04 LTS without success in the sense that the windows 10 partition isn't being detected (see [http://www.tiikoni.com/tis/view/?id=00bc6ea]("http://www.tiikoni.com/tis/view/?id=00bc6ea")).

So back to the output of the *sudo parted -l*... Anyone advice on that?

---

### Post by thunderbirdje on 2015-12-16
I have tried **repair-boot** (see [http://paste.ubuntu.com/14048196/]("http://paste.ubuntu.com/14048196/")), windows 10 is still not detected by Ubuntu :(

---

### Post by westie457 on 2015-12-16
In regard to the leftover GPT data and how to remove it, this is your first place to look. 

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by thunderbirdje on 2015-12-16
Thank you Westie, is it safe to remove the leftover GPT data? (I don't know much about partitioning schemes...)

---

### Post by LostFarmer on 2015-12-16
use fixparts, the left over data must be removed for linux .  It is left over junk that is causing problems.

---

### Post by saaadatgmail.com on 2016-06-23
Hi thunderbirdje

I am in the same situation you are, have you deleted the GPT data with fixedparts? Has it worked?

---

### Post by oldfred on 2016-06-23
If you delete gpt data on a UEFI system you destroy it.
Windows only boots in UEFI mode from a gpt partitioned drive. And only BIOS from MBR.

Only if you have converted system to MBR(msdos) and then are booting in BIOS boot mode, do you need to remove left over gpt data.
Windows 7 default install is BIOS and that converts a drive from newer gpt to the 35 year old MBR. But Windows does not do it correctly and leaves the backup gpt partition table. Windows 7 can be installed in UEFI mode, but must be copied to flash drive and files moved around.

Issues with not seeing Windows 8 or 10 is usually related to Windows fast start up or always on hibernation. Linux NTFS driver will not mount NTFS that is hibernated nor if it needs chkdsk. And after any resize it needs chkdsk.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

