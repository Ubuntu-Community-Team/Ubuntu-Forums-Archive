---
title: "Cannot boot ubuntu after installing xp on another partition."
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by krusty29 on 2007-08-10
I have recently had a dual boot setup between vista and ubuntu which worked fine, but when i decided to switch back to XP and reinstalled it on the partition where vista was my computer began booting straight into xp and the ubuntu grub loader would not show, how i do i get this working again?

---

### Post by forestpixie on 2007-08-10
Have a look at these - there are many threads on this :)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://ubuntuforums.org/showthread.php?t=515217](http://ubuntuforums.org/showthread.php?t=515217)
[http://ubuntuforums.org/showthread.php?t=519350](http://ubuntuforums.org/showthread.php?t=519350)

---

### Post by Mark Phelps on 2007-08-10
OK - standard rule of thumb: Whichever new OS you install will, by default, install its own boot loader -- usually overwriting whatever MBR is already in place.  In the case of Ubuntu, it's smart enough to detect Windows and add an entry to menu.lst to allow you to boot into Windows.  In the case of Windows, it doesn't care about other OSs -- even its own.  

So, if you decide later to reinstall Vista to replace XP, you will then discover that you won't be able to boot Ubuntu anymore -- and then, you'll have to consult the referenced threads about how to fix that.

---

