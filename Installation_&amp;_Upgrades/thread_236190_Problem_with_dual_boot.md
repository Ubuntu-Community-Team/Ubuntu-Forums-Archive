---
title: "Problem with dual boot"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by howardepgco on 2006-08-14
My computer has two hard drives.One has Ubuntu and the other has XP. When I first loaded Ubuntu all went fine. I could get out of Ubuntu,reboot and I had a choice of Linux or XP.Now that seems to have gone.If I specify in my bios during bootup the hardrive with linux it will load it,however,if I specify the hard drive with the XP it will show the drives during boot up but when it tries to load XP it shows the word GRUB_ and the underscore is blinking. Any ideas on how to fix it?

---

### Post by confused57 on 2006-08-14
Boot up into Ubuntu, then open a terminal(Applications---Accessories---Terminal), enter:

```
sudo fdisk -l
```
The -l is a small "L".

This will show your partition tables and will make it much easier for someone to help resolve your problem.

Since you have 2 hard drives, you might also want to read this thread:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

If you have the Windows Installation CD(not a recovery CD), you "may" need to repair the Windows mbr, I don't really understand why it was working, then you got the error later:


[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

