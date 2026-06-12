---
title: "how to uninstall ubuntu for a windows repair"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by 3rdsun on 2006-08-17
how do I uninstall ubuntu. i need to install SP2 on my windows xp partition but I get a message "the core system file is not windows". Is it  gonna be a clean uninstall removing all traces of the grub loader?

---

### Post by Sef on 2006-08-17
Is XP on your first partition.   If it is not, that would be the problem.   Windows needs to be on the first partition.

---

### Post by bobleny on 2006-08-17
Why!? What makes Windows so special that it has to be first!? I hate Windows. I wish there was a linux version for everything!

---

### Post by hopstah on 2006-08-17
> I wish there was a linux version for everything!

there is.  just search for it if you don't know the name

---

### Post by metaltailz on 2006-08-17
So do I, but MicroSoft is so sure that they are the only operating system out there that they set their operating system too assume that it is the only OS on that PC.

---

### Post by bobleny on 2006-08-17
Right, last I checked microsoft doesnt have a linux based version of Stronghold Crusaders...

Not that I ment to change the subject of this post.

---

### Post by 3rdsun on 2006-08-19
yes windows is on the first partition on my first drive, Ubuntu is on the second partition of my second drive. another windows install is also on the first partition of the second drive (no problem there). So how do I do a temp removal of Ubuntu to update my windows xp install. Do i use the CD? Is it gonna remove the bootloader and have windows as the default OS until i do a reinstall?

---

### Post by confused57 on 2006-08-19
You may not need to uninstall Ubuntu, just repair your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
In this link, just note how to boot up with the Windows Install CD(not a recovery CD), press "r" for recovery mode, then enter** fixmbr** to repair the Windows mbr and remove grub.

After you've installed SP2, you can restore grub to the mbr with the Live CD:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

These suggestions may or may not work with your disk(s) and partitioning setup, but could save reinstalling either OS.  Just some options for you to consider...

---

