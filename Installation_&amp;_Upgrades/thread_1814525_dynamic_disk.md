---
title: "dynamic disk?"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by Matrix01 on 2011-07-29
what is dynamic disk?

someone said; if you create dynamic disk with window disk management,
gparted will not recognize.

---

### Post by Quackers on 2011-07-29
If Windows Disk Management screen shows your Windows partitions as dynamic disks it usually happens because a 5th primary partition has been created. (4 is the maximum).
It does mean that any other operating system (afaik) won't recognise those partitions properly and will not install.

---

### Post by doas777 on 2011-07-29
MS has two types of partitions: "Basic", and "Dynamic".
Dynamic disks can be resized, whereas basic partitions cannot. 

here is some more info on them:
[http://support.microsoft.com/kb/314343](http://support.microsoft.com/kb/314343)


you are correct, gparted cannot see volumes within dynamic disks, and will report the space as either unpartitioned or as being of an unknwon partition type.

unless you specifically converted your disks to dynamic after windows install, you most likely only have basic partitions.

---

### Post by Matrix01 on 2011-07-29
so..
what should i do?
i like to dual boot win7 and ubuntu.
I heard that some win7 user were not able to boot into os after resizing.

[ATTACH]198826[/ATTACH]

---

### Post by oldfred on 2011-07-29
You have to delete one partition so you can make one new one that is an extended partition. Extended partitions will hold many logical partitions and Ubuntu/Linux boots just fine from logical partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Back up first:
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Herman on 2011-07-30
> what is dynamic disk?There are two kinds of dynamic disk, the original 'dynamic disk' was some part of Samsung's 'On Track Disk Manager' software, used for enabling larger hard disks to be addressed than the BIOS in older computers would otherwise be able to cater for, 
see:
[Dynamic Drive Overlay]("http://en.wikipedia.org/wiki/Dynamic_drive_overlay") - Wikipedia, [Resolving BIOS and Drive Size Barriers]("http://www.dewassoc.com/kbase/hard_drives/resolving_drive_barriers.htm") - Dewey, and Associates, and [On Track Disk Manager]("http://www.rainbowpcm.com/on_track_disk_manager.html") - Solve the Hard Disk Crunch.

Some marketing people must have thought the words 'dynamic drive' or 'dynamic disk' had a catchy ring to them, and somehow it came to be re-applied it to what seems to me to be Microsoft's version of what we call LVM and software RAID.
see:
[What is the Difference Between A Basic and Dynamic Disk?]("http://www.dynamic-disk.com/difference-between-basic-and-dynamic-disk.html") - Dynamic-Disk.com, [Basic and Dynamic Disks]("http://msdn.microsoft.com/en-us/library/aa363785%28v=vs.85%29.aspx") - Microsoft Library, and [What is a Dynamic Disk?]("http://www.dynamic-disk.com/what-is-dynamic-disk.html") - Dynamic-Disk.com

So if you have a 'basic disk', as applies to almost all standard Windows PCs, it relies on the partition table in the MBR, and you can use third party software such as GParted for resizing your partition and file system.

If you have a 'dynamic disk', which has a special MBR which contains code to warn outside party partition editors not to touch it, and which relies on a hidden database to keep track of disk information, (read the links), then you cannot use GParted for resizing it.
> so..
what should i do?
i like to dual boot win7 and ubuntu.
I heard that some win7 user were not able to boot into os after resizing.My advice would be to just leave well enough alone and don't attempt to resize from within Windows and then install Ubuntu in  the same disk(s). I don't think it would be a good idea and anyway the  Ubuntu installer probably won't let you.
Install Ubuntu in a USB external drive instead or have an additional hard drive fitted in your PC for Ubuntu or build/buy yourself a different computer for Ubuntu. 
Also make sure you install GRUB to MBR in the same hard disk as you install Ubuntu in. 

Actually, thanks for brining the matter up, I have a work computer with two same-sized hard disks and I only use one for the operating system. It was bought with Vista and' down-graded' (or upgraded depending on what you think of vista), to XP and I think it would have originally needed dynamic disk overlay across both disks to run Vista. I'll bet I can get it to work twice as fast if I can get dynamic disk overlay striping across both disks in RAID0. 
Maybe  I can get Windows XP working half as fast as in two internal SATA drives as Ubuntu does from a single USB2 drive, LOL.  :)

---

### Post by Matrix01 on 2011-07-31
i boot ubuntu from unetbootin in USB.

i change settings, and download web browsers or softwares.

when i turne off computer. everything gets wiped off.

how do u install ubuntu in usb or ex. hard drive, and save your wokrs?


> **Herman said:**
> There are two kinds of dynamic disk, the original 'dynamic disk' was some part of Samsung's 'On Track Disk Manager' software, used for enabling larger hard disks to be addressed than the BIOS in older computers would otherwise be able to cater for, 
see:
[Dynamic Drive Overlay]("http://en.wikipedia.org/wiki/Dynamic_drive_overlay") - Wikipedia, [Resolving BIOS and Drive Size Barriers]("http://www.dewassoc.com/kbase/hard_drives/resolving_drive_barriers.htm") - Dewey, and Associates, and [On Track Disk Manager]("http://www.rainbowpcm.com/on_track_disk_manager.html") - Solve the Hard Disk Crunch.

Some marketing people must have thought the words 'dynamic drive' or 'dynamic disk' had a catchy ring to them, and somehow it came to be re-applied it to what seems to me to be Microsoft's version of what we call LVM and software RAID.
see:
[What is the Difference Between A Basic and Dynamic Disk?]("http://www.dynamic-disk.com/difference-between-basic-and-dynamic-disk.html") - Dynamic-Disk.com, [Basic and Dynamic Disks]("http://msdn.microsoft.com/en-us/library/aa363785%28v=vs.85%29.aspx") - Microsoft Library, and [What is a Dynamic Disk?]("http://www.dynamic-disk.com/what-is-dynamic-disk.html") - Dynamic-Disk.com

So if you have a 'basic disk', as applies to almost all standard Windows PCs, it relies on the partition table in the MBR, and you can use third party software such as GParted for resizing your partition and file system.

If you have a 'dynamic disk', which has a special MBR which contains code to warn outside party partition editors not to touch it, and which relies on a hidden database to keep track of disk information, (read the links), then you cannot use GParted for resizing it.
My advice would be to just leave well enough alone and don't attempt to resize from within Windows and then install Ubuntu in  the same disk(s). I don't think it would be a good idea and anyway the  Ubuntu installer probably won't let you.
Install Ubuntu in a USB external drive instead or have an additional hard drive fitted in your PC for Ubuntu or build/buy yourself a different computer for Ubuntu. 
Also make sure you install GRUB to MBR in the same hard disk as you install Ubuntu in. 

Actually, thanks for brining the matter up, I have a work computer with two same-sized hard disks and I only use one for the operating system. It was bought with Vista and' down-graded' (or upgraded depending on what you think of vista), to XP and I think it would have originally needed dynamic disk overlay across both disks to run Vista. I'll bet I can get it to work twice as fast if I can get dynamic disk overlay striping across both disks in RAID0. 
Maybe  I can get Windows XP working half as fast as in two internal SATA drives as Ubuntu does from a single USB2 drive, LOL.  :)

---

### Post by oldfred on 2011-07-31
How big is your flash drive? If 8GB or larger you can do a full install to it. If not you an add persistence to save some info.

If an external hard drive just do a full install to that drive.

I regularly link to Herman's pages with lots of detail on how to install to a second drive.

Hard drive install:
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)


Flash drive installs:

With grub2 persistent C.S.Cameron post#5 10.10:
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)
With grub2 persistent 10.04 C.S.Cameron post#15:
[http://ubuntuforums.org/showthread.php?t=1593656](http://ubuntuforums.org/showthread.php?t=1593656)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

---

### Post by Herman on 2011-08-01
Dynamic Disk in Windows XP Professional is appears to be as useless as an ashtray on a motorbike.
Can you tell me what is the advantage of converting to dynamic disks?
So far it looks like something they started working on but never managed to quite figure out.
I can't install into it, I can only make a striped data partition. Big deal, who cares about having only their *data* striped? No amount of googling seems to lead to any information about how to get the operating system running in dynamic disk striped RAID, but there is plenty of information out there to say it can't be done. I'm lucky I only tried it out in a test computer first.

In Ubuntu we can use install the operating system across two, three, four or any number of hard disks and either make it run faster or more reliable (redundancy), or a combination in between.

---

