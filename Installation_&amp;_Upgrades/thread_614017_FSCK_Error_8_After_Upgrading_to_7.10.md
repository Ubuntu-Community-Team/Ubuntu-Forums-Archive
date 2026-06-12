---
title: "FSCK Error 8 After Upgrading to 7.10"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by DeadSteve on 2007-11-15
Hi all,
I was running a pretty clean install of Ubuntu 7.04 for about 8 months with only the following system changes:

1) Installed an old Geforce 4200 video card
2) Installed a secondary 40gb hard drive and moved my /home directory to it so my information would be safe when performing future OS upgrades.  

The system has been running solid until today.  Today I decided to do the 7.10 upgrade.  After running the upgrade from the update manager (yes, I installed all the hot fixes for 7.04 before doing the upgrade) everything looked as if it was going well.  The system rebooted and that's when it happened.  I got the following error and couldn't log into the system.

fsck 1.40.2 (12-JUL-2007)
fsck.ext3: No such file or directory while trying to open /dev/hdb1
fsck died with exit status 8

The error goes on stating that the superblock couldn't be read and to try e2fsck - b 8193 <device>.

I did try it and it didn't work.  Although I believe it is an ext3.   I know both hard drives work fine as I used them all day prior to the upgrade.

It then opens a maintenance shell, but I'm not well versed in it, so that doesn't help me very much.  So I do the control-D to continue to boot.  Once to the login screen, I can't login because my /home is on the secondary drive. :(

Any help would be greatly appreciated.

Thanks,
DeadSteve

---

### Post by hamid.nyc on 2007-12-17
Exactly same issue here, any solutions out there?

---

