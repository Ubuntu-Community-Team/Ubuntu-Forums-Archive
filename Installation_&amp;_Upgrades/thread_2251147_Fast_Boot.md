---
title: "Fast Boot?"
date: 2014-11-02
forum: Installation &amp; Upgrades
---

### Post by tehtotalpwnage on 2014-11-02
So I've read a lot of installation instructions telling me to turn off fast boot if I'm installing Windows 8 and another OS together. But if these systems are on seperate partitions and I never access the Ubuntu drive from Windows and vice versa is it fine to leave fast startup on?

---

### Post by oldfred on 2014-11-02
If Windows never accessed it may be ok.

Because it is hibernated, you cannot then access the data in the Windows NTFS partition from Linux. The Linux NTFS driver has built in protection  that if a file system is hibernated or corrupted and needs chkdsk it will not mount it to prevent damage that chkdsk then could not fix. 
You may be able to mount in read only mode by forcing it.
This may also apply to a separate NTFS shared partition. With Windows I do not believe their is a way to unmount a data partition before shutting down, so the data partition is also hibernated.

       WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

---

### Post by tehtotalpwnage on 2014-11-02
Alright thanks!

---

