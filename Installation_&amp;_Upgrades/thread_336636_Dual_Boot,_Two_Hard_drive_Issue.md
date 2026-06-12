---
title: "Dual Boot, Two Hard drive Issue"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by strange_cathect on 2007-01-11
Re: Dualboot Two Hard Drives
A little help?

I followed these directions for dualbooting Ubuntu and XP on two separate Hard Drives found at the following link: [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)


1. I disconnected the HD with XP on it and hooked up the new drive using the cables from the original drive. Ubuntu installed perfectly. I updated and was able to boot into Ubuntu without problems.

2. I then proceeded to edit the menu.lst file as directed in the above post. 

3. On reboot, I initially got an error message that the "drive doesn't exist."

4. Now my machine boots to windows every time after briefly flashing Grub on startup. I am unable to boot into Ubuntu.  After many, many tries I am still unable to catch the Grub menu.  

Any ideas?

---

### Post by Paerez on 2007-01-11
the best thing to do to "catch" the grub menu is to repeatedly (maybe once or twice per second) tap the down arrow. Reboot, and after giving the computer a couple seconds, just start hitting down. Eventually the grub menu will pop up.

Pressing down stops the timout counter, giving you more time to act.

---

