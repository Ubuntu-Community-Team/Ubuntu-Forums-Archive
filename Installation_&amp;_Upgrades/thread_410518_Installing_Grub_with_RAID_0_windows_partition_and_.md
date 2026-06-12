---
title: "Installing Grub with RAID 0 windows partition and extra HD for ubuntu"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by DemaSRV on 2007-04-15
I can install ubuntu, but after the reboot, I get a Grub error 15 (the one where grub cannot find the partitions to boot)

Now I have been doing some reading and spent a lot of time on google and been told that RAIDs and grub do not get along but here is my situation:
I have 2x 160gb drives in a RAID 0 which has ONLY my xp install.  I also have a 9gb drive I want to and can put ubuntu on.  I think grub is giving me the error because it is installing on the first disk and not seeing the 2 drives as one, and then grub cannot find the 3rd HD with ubuntu on it, or the windows installation.  

That's my problem, I havent found much of anything, and what I have found involves installing ubuntu on a share RAID 0.

THanks for your help!  I've ran into a lot of problems and worked through them, this is the only one I can't get.

---

### Post by DemaSRV on 2007-04-16
bump.

---

### Post by confused57 on 2007-04-16
What you could do is install grub to your 3rd hard drive, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
for example, if "find /boot/grub/stage1" returns "root (hd2,0)", then "setup (hd2)".

Then set your bios to boot first to your 3rd hard drive, if you get a grub menu at boot, highlight your Ubuntu entry, press "e", then change the line with root from (hdx,y) to (hd0,y), then press "b" to boot...this change is temporary, if it works it can be made permanent in your /boot/grub/menu.lst.

---

