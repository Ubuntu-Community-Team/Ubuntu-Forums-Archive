---
title: "New installation, trying dual-boot for the first time"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by johnjust on 2011-09-29
Hello all,

Haven't been here in quite some time, which means I haven't had any issues in quite some time - Ubuntu has been solid the past year or two.

I have a new ThinkPad waiting for me when I get home today, and although Wine has been awesome so far, I'm looking at possibly dual-booting between Windows and Ubuntu for the first time.

Here's the problem: I've never dual-booted before, although I know that it's recommended to install Windows first.  Since my ThinkPad comes pre-installed with Windows 7 (and usually no Windows disc), I'd like to preserve that install if possible, and use GParted to re-partition the Windows drive into both OS/User space, and then create 2 other partitions for Ubuntu root/home space.

A couple quick questions:

1. Do I need to defrag the Windows drive before repartitioning?  This may be a stupid question, but I have very little knowledge of how Windows 7 performs.

2. Is it necessary to have separate user space on both the Windows and Linux installs?  Or, can I get away with a 3 partition drive (Windows, Linux, User space) and have the user space accessible from both OS'es?

3. What are some good sizes to partition the drives?  I was thinking 10-15 for each OS and then the remaining space for user space (split 70/30 if separate Windows/Linux space is needed, as the Windows space will only be used for games).

That's pretty much it - thanks for any assistance!

---

### Post by Bucky Ball on 2011-09-29
Defrag and resize the Windows drive using Windows software, NOT Gparted.

Once you have defragged (several times if possible and Power-defragger is free and more powerful than the generic Win defragger) shrink the Win partition and just leave empty space; you don't need to create any partitions as you can do that in the Ubuntu install process. Just leave free space.

With that free space create an extended partition (when you are installing Ubuntu) and inside that create logical partitions; /, /home, and /swap are a good start. You are limited to four primary partitions on one physical drive; the extended is one of them BUT you can theoretically create as many logical partitions inside that as your machine will handle. Ubuntu ***does not*** need to be on a primary partition. Lives happily on logical inside an extended. ;)

---

### Post by johnjust on 2011-09-29
> **Bucky Ball said:**
> Defrag and resize the Windows drive using Windows software, NOT Gparted.

Once you have defragged (several times if possible and Power-defragger is free and more powerful than the generic Win defragger) shrink the Win partition and just leave empty space; you don't need to create any partitions as you can do that in the Ubuntu install process. Just leave free space.

With that free space create an extended partition (when you are installing Ubuntu) and inside that create logical partitions; /, /home, and /swap are a good start. You are limited to four primary partitions on one physical drive; the extended is one of them BUT you can theoretically create as many logical partitions inside that as your machine will handle. Ubuntu ***does not*** need to be on a primary partition. Lives happily on logical inside an extended. ;)

Thanks for that.  What should I do about a user data partition?  That's my main concern - having non-OS space that won't be touched if I reformat down the road, accessible by both OS'es if possible.

---

### Post by oldfred on 2011-09-29
+1 good advice from Bucky Ball

Windows needs lots of room. NTFS needs 30% free, at 20% free it slows down and at 10% free it just about stops. So leave room. 

Also best to have a shared NTFS partition. Windows does not like a lot of writes into its system partition. You can mount it read only or just mount & hide it. Because the NTFS driver in Linux shows all the Windows hidden files & folders, it is just too easy to accidentally move a vital file or folder.

Make the Vendor recovery DVDs, and after you have housecleaned out the temporary software you do not want & updated system you may want to do a full backup as the vendor recovery is just an image of the drive as purchased.

Vital to have LiveCDs or RepairCDs/USBs for every system installed. You Ubuntu install CD works for repairs, but it pays to have a Windows repair CD.

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by johnjust on 2011-09-29
> **oldfred said:**
> 
Windows needs lots of room. NTFS needs 30% free, at 20% free it slows down and at 10% free it just about stops. So leave room. 


Yikes...  wasn't expecting that, I definitely don't want to dedicate any more than ~10GB-15GB to the Windows partition, that's crazy.

I'll make the backups, thanks for those links, but I'll probably end up with another Ubuntu-only laptop (which is fine, Windows would only be used for a game or two anyway).

Thanks, should be solved from here.

---

### Post by Bucky Ball on 2011-10-01
Good news. What Oldfred says is right, but if you're using XP ... I have that installed on 12Gb partition. ;)

---

