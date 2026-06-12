---
title: "Grub Dual Boot Issue - Cannot boot Win 7"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by MrVidal on 2010-05-03
I updated from Ubuntu 9.10 to 10.04 via Ubuntu updater. Worked nicely.

Until I had to use Win 7 for a moment, so I went to the Grub boot menu and picked Win 7.

Nothing is happening. Just a black screen with blinking underscore to the top left corner.

I never had this problem with 9.10, so I am confused. I tried looking around and nothing helped.

Be noted that I am an amateur with Ubuntu coding and installing.

I did hear that this is already a common issue now.


Edit: I do not have Win 7 disk.

---

### Post by adm1968 on 2010-05-03
[FONT="Georgia"][SIZE="2"]This is affecting lots of people
[http://ubuntuforums.org/showthread.php?t=1469755](http://ubuntuforums.org/showthread.php?t=1469755)
[/SIZE][/FONT]

---

### Post by MrVidal on 2010-05-03
Apparently there is no solution yet. :/

---

### Post by oldfred on 2010-05-03
Did you look at post #3 in above link by adm1968. That has a sollution that has worked for many.

Did you as part of the upgrade install grub to all the partitions? That it the problem.

---

### Post by MrVidal on 2010-05-03
1) I tried and I can't even get tar.bz2 open. (I am very bad at installing packages manually)

2) I do not know. I used Update Manager to update and it asked me abotu Grub, so I kept it as the way it is (status quo).

---

### Post by MrVidal on 2010-05-03
Managed to work testdisk and followed all of the instructions from the link in post 3 by adm1968.

Didn't work.

Apparently reinstalling 9.10 didn't solve the issue either, even if wiping the Linux partition clean.

---

### Post by oldfred on 2010-05-03
IF testdisk does not work then you can try the windows repairs, you need to run fixboot which is slightly different for XP vs Vista/7. If you run fixMBR you will have to reinstall grub to the MBR, but then you can boot windows to know that it works. 

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

