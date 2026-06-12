---
title: "ubiquity cannot see hard drive when trying to install 14.04"
date: 2015-12-14
forum: Installation &amp; Upgrades
---

### Post by mtmigs on 2015-12-14
I am trying to install Ubuntu on a 932GB SATA hard drive. First I was trying to use a Acer M3410 which has some sort of raid SATA controller. I could boot the live-cd just fine. It would see the drive with gpart. I created partitions, formatted them, and deleted them without any problems. But when I tried to install it never saw the drive. I could not assign a mount for root because there were no options and pushing the + button did nothing. I tried going into the bios and changing to both IDE and AHCI with no difference.

I even tried installing fedora but its install also did not see the drive.

The I tried an old version of opensuse. That at least saw the drive but it saw the drive twice. Once as the regular 932GB SATA drive which it would not install onto and a second time as long name including the word raid. Opensuse allowed me to partition only the second name and then failed to install.

Next I tried putting the drive into a Dell Precision T3500. It had the same result, gpart saw the drive but the load (ubiquity) did not. The original 991GB SATA drive in the Dell was seen by the install just fine but the drive onto which I wanted to install ubuntu was not seen. I tried changing the SATA controller to IDE and AHCI but that made no different. But the BIOS screen that allowed specifying what controller type was wanted seemed to give a hint asto what was wrong with the drive. It said the controller type (unless the drive had a raid configuration.)

It seems something has been written to the drive forcing it to be considered a raid drive no matter what the bios says.

Does anybody know why ubuntu does not see the raid drive? Does anybody know how to remove the raid signature from a drive?

---

### Post by sudodus on 2015-12-15
You can try to wipe (overwrite with zeros) the first megabyte of the drive. It that does not help you can overwrite more, but often it is enough with the first megabyte, and after that format the drive (or let the Ubuntu installer format it).

See this link: [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by mtmigs on 2015-12-16
Actually, I found the super block is at the end of the drive. Using the dmraid -r command I found the drive did have a raid signature and also the location of the signature. I then used dd if=/dev/zero of=/dev/(that drive) seek=(that location) to clear it.

---

### Post by oldfred on 2015-12-16
If RAID left on drive you can run this command to remove RAID.

 Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
Even if raid not used BIOS may have set parameters, Also check BIOS settings, should be AHCI
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

