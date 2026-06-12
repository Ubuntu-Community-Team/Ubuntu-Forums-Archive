---
title: "Running windows/ubuntu doesn't work"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by BennX on 2012-01-26
Good evening,
I am running a 64bit windows 7 system and just tried to install ubuntu 11.10 via the "run it with windows" thing. It wasnt a problem to install it but acctually i cant boot ubuntu and tells me that "gave up waiting for the root device". I tried to reset the grub but didnt get it working than.

So i thought i just install it the normal way and make an extra partition for it. But this actually just crashed way more. I installed it and even didnt get the chance to decide between ubuntu or windows. Right after the raid system started up it just restarted the computer.

Now i just made windows new and hope you guys can tell me how to get it work under windows because i would love to use it for programming and stuff like that for the Study.

By the way i am new to Linux so i hope i get an easy introduction.

system informations:
core i7 920
gigabyte Ud4P X58
2x 1tb HDD in an raid 0 system (maybe this is the problem?)
500gb backup HDD
Gainward 295 GTX
6gb DDR3 1600mhz

Best Regards,
BennX

---

### Post by Mark Phelps on 2012-01-27
RAID is likely to be the problem.  Try doing the install using the Alternate CD.  It uses a text-base installer, instead of graphics, but it understands RAID systems.

Since you're running Win7, do NOT use the Installer (slider) to shrink the Win7 OS partitions, instead, use ONLY the Win7 Disk Management utility to do that.  Then, boot into Win7 a couple of times to let the filesystem make any needed adjustments.

Also, after you do that, and BEFORE you attempt the Ubuntu installation, use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will prove vital later should you need to repair the Win7 booting from problems during the dual-boot setup.

---

### Post by BennX on 2012-01-27
Thanks a lot for you answer,
I' try to do that. I just made an extra Partition for it right now. It is in the Raid0 system. 

//Should i use the guide Software_RAID_mit_LVM ? or can i just install it with the alternate CD?!
 Sorry its not a software raid i got so ....
Best regards

---

### Post by BennX on 2012-01-28
Please close it ;)

Just installed it with wubi at my backup disk wich isnt a raid system and it works without any Problems. All of my hardware works great and i love to use it. 
The best thing is that i can use the windows bootloader. Also can use Windows and ubuntu side by side.
Thanks for your help :lolflag:
BennX

---

