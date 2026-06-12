---
title: "why disable fast startup for installing dual boot with windows 8?"
date: 2013-11-14
forum: Installation &amp; Upgrades
---

### Post by ATEGEV on 2013-11-14
Sorry if there is already another topic with this. I tried searching with brackets or quotes, but I don't know how to search for exact word groups. I tried "fast startup" or (fast boot), but the results given are with boot or fast.

I read in all the manuals for installing a dual boot system that you have to disable Fast startup in Windows. What is the exact eason for that?

Can it be reenabled after the installation was succesful?

---

### Post by oldfred on 2013-11-14
You should not. Even if you create a shared NTFS data partition the hibernation may maintain the file structure so if you try to save a file from Linux into the NTFS partition it will get lost on Windows reboot as it only remembers the old file structure.

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

---

### Post by ubfan1 on 2013-11-14
Additionally, fast bootup makes it very difficult to use the function keys to select boot devices or entering BIOS/UEFI setup.

---

### Post by ATEGEV on 2013-11-14
> **oldfred said:**
> You should not. Even if you create a shared NTFS data partition the hibernation may maintain the file structure so if you try to save a file from Linux into the NTFS partition it will get lost on Windows reboot as it only remembers the old file structure.


It will get erased? Or will it be just undetectable for Windows (I mean if you afterwards log in to Ubuntu it will stil be there)?


> **ubfan1 said:**
> Additionally, fast bootup makes it very difficult to use the function keys to select boot devices or entering BIOS/UEFI setup.


I don't have this problem. If you know which key it is that you need, you can push it several times, beginning soon enough.

---

### Post by oldfred on 2013-11-14
Windows restores old file structure. While data may still be on drive it is then gone. And Ubuntu will not see it on a new reboot as it will load the new (old) version that Windows then has restored.

---

