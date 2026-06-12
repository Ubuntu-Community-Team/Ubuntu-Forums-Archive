---
title: "Partitioning Hard Drive in Windows 8"
date: 2013-09-19
forum: Installation &amp; Upgrades
---

### Post by twisted willow on 2013-09-19
Hoping someone can help me with this.I have Window 8 (upgraded Windows 7) and am struggling to free up space to install Ubuntu as a dual boot. What I have  tried so far:

Used Windows Partition Manager to free up 20GB then used the Simple Volume Wizard to set this as a FAT32 volume. When I fired up UBUNTU it picked up this space but it was flagged as unuseable.

I then went back into the Partition Manager and deleted the volume so I just had unallocated space. Fired up Ubuntu and launched GParted. This didn't pick up the free space. I tried shrinking my main volume to free up space by GParted threw up and error and wouldn't do it.

Not quite sure what yo try now. Any ideas?

---

### Post by Mark Phelps on 2013-09-19
Ubuntu doesn't install in FAT32 filesystems; instead, it needs Linux filesystems.  Do NOT mess around with GParted trying to shrink the Win8 OS partition -- doing so risks corrupting the Windows filesystem and rendering Win8 unbootable.

---

### Post by oldfred on 2013-09-19
Did you turn off fast boot in Windows as that creates all sorts of issues. Gparted (and the installer?) will not be able to mount NTFS partition that is hibernated with fast boot on.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

See link in my signature for a lot more info on UEFI installs. Some settings, creating repairCD & backups are really required as any issue then can be recovered from.

---

