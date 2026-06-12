---
title: "Installation error"
date: 2006-04-05
forum: Installation &amp; Upgrades
---

### Post by tsharpe62 on 2006-04-05
I just installed a new HD and trying to unstall ubuntu but I'm getting an error that says:
!!Partition disks
no root file system
Please correct this from the partitioning menu

But when I try to select "guided partitioning" the only selection that appears is manual partitioning and when I select it - it throws me back to the partitioning menu. Help!

---

### Post by tsharpe62 on 2006-04-05
additional info:
When I remove the installation CD and let it boot on it's own under Linux the boot up stops with the following:
VFS: cannot open root device "301" or 03:01
Please appent a correct "root=" boot option
Kernel panic: VFS: Unable to mount root fs on 03:01

---

### Post by Phlosten on 2006-04-05
Have you checked that the hard disk drive is in fact installed correctly.
Make sure the bios is detecting the drive correctly or manually set the specs in the bios itself. Also make sure that you have set the jumper pin on the drive correctly.

---

### Post by tsharpe62 on 2006-04-05
Yes the bios recognizes the new drive. I can't boot to a dos diskette and switch to the c: drive and event copy files from the a: drive to the c: I've tried every jumper setting (strap up and down) that there is available.

---

### Post by tsharpe62 on 2006-04-05
oops...
Yes the bios recognizes the new drive. I can boot to a dos diskette and switch to the c: drive and event copy files from the a: drive to the c: I've tried every jumper setting (strap up and down) that there is available.

---

### Post by tsharpe62 on 2006-04-05
Here is where I'm at:
When using the install disk it stops at this point:
Checked bios and it recognizes the drive.
Boot from a dos disk in a: and I can switch to c: and copy files from a: to c:
If I boot from the Ubuntu install cd it stops with the following on the screen:
!!Partitioner disks
      ??? ???
and it is stuck there - you can't continue and you can't go back.

(I realize that this might be irrevalant since I'm not completing the install)
If I boot without the install CD or the Dos diskette I'm getting this error:
Warning: Unable to open an initial console
Kernel panic: no init found. Try passing init=option to kernal

---

### Post by Phlosten on 2006-04-06
Ok, another question for you. What was on the hard disk before you installed it? I am thinking maybe you may have a corrupted file system on the disk or one that the Ubuntu install is not recognising, and being tripped up by.

One suggestion would be to download and run DBAN ( [http://dban.sourceforge.net/](http://dban.sourceforge.net/) ). You create a bootable CD from the downloadable ISO, then run that in the computer with the hard disk you are having trouble with and it will complete wipe the hard disk on it. (Be careful with this CD, you don't to wipe things you dont need to.)

Failing the hard disk being the problem, maybe you could look at the quality of the Ubuntu install CD. People have had problems before running Ubuntu CD's that have been burnt too quickly and the integrity of the CD has been lost. Maybe try to burn the CD at the slowest speed you can to ensure there are no problems.

---

### Post by tsharpe62 on 2006-04-06
You re the man!  Dban did the trick. I think that the compact loader created some funky partition that the ubuntu did know how to handle. After wiping the disk with Dban the install ran smoothly. 

Thanks for you help!

---

### Post by Phlosten on 2006-04-06
Glad to see that it worked.
The DBAN tool is quite handy, great if you want a nice clean install, as you know everything will be completely gone.

A glorious welcome to another Ubuntu install!

---

