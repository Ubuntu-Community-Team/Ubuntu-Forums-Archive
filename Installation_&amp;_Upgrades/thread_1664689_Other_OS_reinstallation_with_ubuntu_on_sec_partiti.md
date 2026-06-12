---
title: "Other OS reinstallation with ubuntu on sec partition"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by Freeman-sr on 2011-01-11
Hello again.

I have Win XP on a single partition and Ubuntu is on HDD's rest. I figure that if I format the primary partition, the grub data is going to be lost and likely Ubuntu will be cut off. To prevent this, I guess I only have to make backup of grub's data and put them back on C: when I reinstall the Win.

Am I right about this, and what files on C: are actually related to grub? Thanks.

---

### Post by oldfred on 2011-01-11
No part of grub is in C: unless you have wubi. When you reinstall windows it will automatically install its boot loader to the MBR, overwriting grub's MBR. 

You just have to reinstall grub to the MBR and probably after rebooting run sudo update-grub. Besure to have a good liveCD of Ubuntu (or any Linux repair CD) to reinstall grub2 to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

