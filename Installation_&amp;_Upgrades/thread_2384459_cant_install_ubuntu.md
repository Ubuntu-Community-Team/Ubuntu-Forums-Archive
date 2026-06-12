---
title: "cant install ubuntu"
date: 2018-02-07
forum: Installation &amp; Upgrades
---

### Post by bclaussen on 2018-02-07
I have a alienware and trying to install ubuntu as my new operating system.  I am using a USB as installing it.  When I get to the window asking Installation type, there is no option.  It is completely blank.  Does anyone know what is the problem?

---

### Post by TheFu on 2018-02-07
Best to search for help on the exact, specific, model.  "ubuntu install alienware xyzabc" to see what others have figured out.

There is also a common blank screen issue that is solved with a boot option, but different systems seem to get this for different reasons with different releases.  [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)  I think 17.10 changed much of that, but hopefully you are trying to install 16.04.

---

### Post by oldfred on 2018-02-07
Old BIOS system with all 4 primary partitions used?
Or newer UEFI system but Windows fast start up is still on?
Dell (and its cousin Alienware) may have RAID on, you need to install AHCI drivers in Windows and change UEFI drive setting to AHCI.
Those are main reasons why installer will not see or let you add partitions.

       Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr)

---

### Post by bclaussen on 2018-02-07
thank for that info...and yes the window fast start up in on.  When i get home from work i will try again.  again thanks

---

