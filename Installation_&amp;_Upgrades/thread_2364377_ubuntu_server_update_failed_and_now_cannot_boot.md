---
title: "ubuntu server update failed and now cannot boot"
date: 2017-06-22
forum: Installation &amp; Upgrades
---

### Post by dvbarragan@gmail.com on 2017-06-22
System notified me that updates where available (like it does almost every other day....) including a update to ubuntu base.

I notice that it was saying a package had failed  (it looked like grub2??? and it was failing with kernel image 4.4.0-81 not being able to write to my disk....)
I allowed the report process to run ... then the report process failed indicating this update had already failed and been reported.

System rebooted and now get this on my screen (attached failure.jpg)
[ATTACH=CONFIG]275730[/ATTACH]

Any help on how to revert?  I can't seem to get grub to come up.

Thanks in advance (really in need of help!)




Dave-

---

### Post by TheFu on 2017-06-22
Out of space on /boot?  If so, that needs to be cleaned up first.  Use any liveboot method running the same OS on the machine, choose "rescue mode" - let it setup the chroot with / and /boot mounted using the correct partitions.  Now you can use apt or aptitude or dpkg or ... whatever APT method you like to clean up the /boot partition.  
**Do not just delete files.** 
Then run **update-grub** - if it looks like it worked, excellent. 
If it looks like it failed, come back with a copy/paste version of the output.

---

