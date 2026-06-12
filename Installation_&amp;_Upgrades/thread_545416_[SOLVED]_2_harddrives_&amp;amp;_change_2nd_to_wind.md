---
title: "[SOLVED] 2 harddrives &amp;amp; change 2nd to windows"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2007-09-07
When I installed Feisty ver. 7.04, I had two hard drives in the box. Both are linux the 2nd (primary slave) is Dapper, ver. 6.10. 

Grub found both drives during install. So it knows it is "on the cable" so to speak, and even though I can't boot to it, I can by read and write to it. (adding a 2nd drive in /mnt and changing fstab)

Now I want to remove this 2nd drive and put in a Windows 98 drive and I want to know whether by merely booting the OS, if Grub will find the windows 98 disk? That is will it list it in the start up menu, which as of now presents a long list of new and old kernels it sees installed?

---

### Post by merlinus on 2007-09-07
Don't think so.  You will probably have to manually change a few files, most likely /etc/fstab and /boot/grub/menu.lst.

-merlin

---

