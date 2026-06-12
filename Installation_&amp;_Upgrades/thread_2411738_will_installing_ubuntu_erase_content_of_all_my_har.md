---
title: "will installing ubuntu erase content of all my harddrives?"
date: 2019-02-03
forum: Installation &amp; Upgrades
---

### Post by blumarmalade on 2019-02-03
Hi, I'm running windows 10 and i'm looking into installing ubuntu instead.
The only reason I use windows is because of Visual Studio, but now I want to install ubuntu for testing my webapps as they run on an ubuntu server.

I could dual boot. But I would rather go all in.

So what is left for me to go on and do it properly is that i have 3 haddrives with alot of content I want to keep. These are normal windows ntfs disks.

By installing Ubuntu i'm fine with completely overwriting the main windows install, but will I be able to keep and access the content on my other disks?

---

### Post by TheFu on 2019-02-03
Yes, but it would be best to physically disconnect the other disks during the installation for someone unsure of their skills to 100% prevent human error from wiping the wrong storage or having the boot code put on the wrong disk.

Also, leaving any NTFS connected post-install is inefficient and can cause permissions problems.  The NTFS driver is slow, it runs in user-space, not kernel-space.  But if you must keep NTFS, there are some mount options which can help, but those can only be added via the fstab options, no GUI mounting will do it.  This might over your head, so maybe save this and come back to it in 6 months. It will make more sense after dealing with NTFS for a few months. ;)

---

### Post by Impavidus on 2019-02-03
Will Ubuntu erase all hard drives? No, not necessarily. With multiple hard drives it's best to use manual partitioning and the installer will only wipe the partitions you select to format. But you wouldn't be the first to select the wrong partitions, so it's best to disconnect the drives you want to keep unaffected first. Also, a drive is the physical thing plugged into your computer. A partition is a logical segment of a drive. Windows confuses the terms. Just in case you were not aware of that.

There's another problem with keeping your data on ntfs filesystems after wiping Windows. Linux isn't very good at fixing ntfs. So if filesystem damage happens, the Linux tools may be unable to fix it and you need either Windows tools or your backups.

---

### Post by Rick St. George on 2019-02-04
> **blumarmalade said:**
> 
By installing Ubuntu i'm fine with completely overwriting the main windows install, but will I be able to keep and access the content on my other disks?

Short Answer: YES, ubuntu will access those files on any of those disks.

But I would recommend a Dual Boot system, that way you can still use WinX to create Visual Studio files, programs etc. You may need to install Ubuntu Server to properly display your resulting work.
See my Post #4 on this Thread [https://ubuntuforums.org/showthread.php?t=2411731](https://ubuntuforums.org/showthread.php?t=2411731)

You could also install Ubuntu (and Server files) on Disk 2 or 3 ... IF you have at least 2 partitions and 1 large enough to install Ubuntu or (Xubuntu [https://xubuntu.org/download/](https://xubuntu.org/download/)) onto. This would not be a Dual Boot system. In that event, you may also install a "Switch". I use [URL="http://www.kingwin.com/hard-drive-power-switch-hdd-ps6/"]http://www.kingwin.com/hard-drive-power-switch-hdd-ps6

[/URL]

---

