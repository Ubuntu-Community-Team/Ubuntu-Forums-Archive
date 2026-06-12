---
title: "cannot  dual boot Ubuntu and Windows"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by alexathk on 2007-06-21
Actually, my problem is similar to [this one]("http://ubuntuforums.org/showthread.php?t=478698&highlight=grub+windows").
It came up like this.
When I wanted to resize the windows partition by Ubuntu live CD, I accidentally delete the label of the partition, so the whole disk is like formated(in Gparted). However, I can still access my files in those partitions(seemed those label information is stored in RAM), so I used a external drive copied the whole system. After I installed the Ubuntu 7.04, and copied the files back to the primary  partition. I cannot find the winXP in the GRUB. Desperately, I reinstalled Ubuntu again. This time, the grub loader found windows. However, after choosing this option, the process would hang there. 

Then today, I used the recovery partition in the drive(it appears in grub and works right).In the beginning of  the recovery process, the gurb worked fine. I can boot into Ubuntu and windows. But as the IBM setup the applications in Windows, after one of the automatic restart, Grub was lost. and the screen showed 'Hard Disk Error'. and at the same time, the computer went dead. It wouldn't restart after I  pressed Ctrl+Alt+Del, But when I press Power off, It would shut down immediately. However, the computer will start by itself after a few seconds. I really got lost. 

could anyone help me to fix this problem?

Thank you very much

---

### Post by ajgreeny on 2007-06-21
You really seem to have borked something but try restoring the windows MBR in the first place with the windows CD (boot into it and hit "r" for the recovery console and then type fixmbr) and see if that allows you to start windows again.

If it does you can now reinstall grub and hopefully all will be OK.  If not then you may like to try fixboot from the windows recovery console this time instead of fixmbr which you tried the first time.  Now try rebooting windows again and if OK reinstall grub.

If none of this works, then I'm afraid the problem is way beyond me and it may be that the reformat has knocked the system out and a reinstall is all that you can do.

Good luck.  I hope the last option I mentioned is not where you end up!

EDIT- I've just noticed you have already used the recovery partition (to reinstall windows, I presume) so am now even more baffled about what you may have done to your system.

---

### Post by alexathk on 2007-06-24
Thanks for your prompt reply. 
Right now I have fixed the problem. However, I still don't know where it went wrong. But I think it's not GRUB in menu.lst. Because it didn't change. Maybe MBR was the problem.
Let me tell you how I fixed it. I just mentioned when I ran recovery. The Grub boot well during the process. So, before the recovery finished, I replaced everything in C: with the backup. Of course, I first reinstalled Ubuntu, so that I can have a grub and ran recovery.
Now, it's a dual boot. though still a little problem about my newly 'installed' Windows.

I backed up the MBR during I reinstall Ubuntu. Before I reinstall it, nothing boot.  I think Ubuntu installer fixed the MBR. I cannot read what's inside. I just attached them, so that some experts can find out what's the problem.

P.S. the attached MBR for IBM.tar.gz is what IBM provided to fix the problem of booting if I cannot find the recovery partition. However, with Ubuntu installed. This floppy can only crash my grub and MBR. Again, I don't know the reason.

---

