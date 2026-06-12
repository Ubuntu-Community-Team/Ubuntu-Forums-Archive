---
title: "Dual boot problems (Ubunto-Xp)"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by polvere on 2010-10-04
Hi everybody,

I a new user of Ubuntu, and I need to keep using also Windows Xp. That why I installed win first and then ubuntu. I know it's more a question about Win, but I'm sure lots of linux users keep win too, so probably someone has the solution.
Everything worked fine and I was happy until I did an update (recommended by ubuntu) and now I'm getting 2 linux core versions at the grub menu (which make the same linux start), and winxp that doesn't start anymore.
The error I got was:
-"Windows could not start because the following file is missing or corrupt:
  <Windows root>\system32\hal.dll.
  Please re-install a copy of the above file."

I googled for a while, and tried to restore the corrupted dll, which, of course, didn't work out. Then I found out that probably the problem is in boot.ini. so I found out that the boot.ini was referring to partition 4, while win is installed on hd0,4, so it seems that boot.ini has to refer to partition 5. Is that correct?

In any case, if I set partition 5 I got a new error, which is:
"Windows could not start because of a computer disk hardware configuration problem.
Could not read from the selected boot disk. Check boot path and disk hardware.
Please check the windows documentation about hardware disk configuration and your hardware reference manuals for additional information."

while I got the usual hal.dll error with all the other partitions.

Do you have any suggestion?
I don't want to do a fixmbr from win restore consolle, since I'm not sure I'm able to restore grub after that...

Also...chkdks is telling me that the win partition doesn't end at the end of the cylinder...

Thank you for you support!
Ciao
Davide

---

### Post by andrewthomas on 2010-10-04
> **polvere said:**
> 

Do you have any suggestion?
I don't want to do a fixmbr from win restore consolle, since I'm not sure I'm able to restore grub after that...

You should be good as long as you have not installed ubuntu using wubi (within windows.)

You can run fixmbr then reinstall grub2 from the LiveCD

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by oldfred on 2010-10-04
Missing hal is usually not a missing hal.dll but boot.ini issues:

Fix WinXP hal.dll Post #8
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
From Recovery Console run bootcfg /rebuild (fixes boot.ini which often causes hal.dll errors) and CHKDSK /r (which checks the drive for errors and fixes any).

With LBA cylinders, heads are obsolete and a partition not ending on cylinder is not an issue.

---

