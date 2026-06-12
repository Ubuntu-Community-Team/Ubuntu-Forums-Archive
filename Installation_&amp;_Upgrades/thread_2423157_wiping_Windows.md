---
title: "wiping Windows"
date: 2019-07-18
forum: Installation &amp; Upgrades
---

### Post by dwater on 2019-07-18
Hi,

I'm about to wipe Windows from my laptop (Lenovo T480s), however I'm hesitant because I might need to use Windows to update firmware/etc.

I'm inclined to create a Windows restore disk, but I'm not entirely sure that will do what I want (without completely wiping my Ubuntu install in the process).

What's the recommended procedure?

Max.

Windows 10
Ubuntu 19.04 (iirc)

---

### Post by yancek on 2019-07-18
You would probably get better info on making a windows 10 backup/restore disk at the microsoft site or a windows forum.  I have no idea.  Not sure how making a backup of windows 10 would wipe out your Ubuntu install unless you backed up to the wrong disk?

How big is/are your drive/s?  The Ubuntu documentation below explains dual booting with win 10.  It seems from your post you already have this but it isn't clear to me.  Shrink the windows partitions to a minimum amount and use the rest for Ubuntu.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Have you looked into using clonezilla?

---

### Post by dwater on 2019-07-18
> **yancek said:**
> You would probably get better info on making a windows 10 backup/restore disk at the microsoft site or a windows forum.  I have no idea.

Perhaps, though it isn't a common thing for them to want to wipe windows off, replacing it with Ubuntu. I suppose they might have some idea how to boot Windows just to update firmware/bios/etc.

> Not sure how making a backup of windows 10 would wipe out your Ubuntu install unless you backed up to the wrong disk?

Well, that comment was about when/how I *make use of* the restore disk - ie unlike Ubuntu, I can't boot Windows off a USB drive - or can I? I had anticipated it wiping Ubuntu (which I'm about to install).

> 
How big is/are your drive/s?  The Ubuntu documentation below explains dual booting with win 10.  It seems from your post you already have this but it isn't clear to me.


(Drive is 256GB) I used to have this dual boot setup on my older laptop, but Windows often caused problems with the boot loader, so I wiped that off and made good use of the extra disk space it was using. On this new laptop, I am seriously considering completely wiping Windows from the start.

> Shrink the windows partitions to a minimum amount and use the rest for Ubuntu.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Have you looked into using clonezilla?

I've not heard of that...I'll take a look.

Thanks.

---

### Post by crip720 on 2019-07-18
If just want to have windows for bios/firmware, you only need enough space for windows minimum install(plus a little extra).  Can make a new install partition instead of shrinking(make windows install disk).  Not using windows for anything else, so updates not as important/needed.  EFI installs seem like they don't mess up grub as much(only one test) now.  Bios/firmware updates can sometimes be done with ubuntu with a lot work compared to almost one click in windows.

---

### Post by oldfred on 2019-07-18
Many end up wanting Windows back for one application or game that does not run well in Ubuntu. So we suggest backing Windows up.

One user would purchase laptop with HDD, and immediately remove HDD before Booting Windows and add SSD and Ubuntu. Then later when he sells laptop, he has a new Windows install and no issue of any of his data on it.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

The standard Windows ISO, may not include any drivers that your system needs. 
       
 Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by pascua28 on 2019-07-22
Why not just dual boot?

---

