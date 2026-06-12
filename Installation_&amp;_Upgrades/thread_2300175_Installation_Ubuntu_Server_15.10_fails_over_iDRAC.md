---
title: "Installation Ubuntu Server 15.10 fails over iDRAC"
date: 2015-10-24
forum: Installation &amp; Upgrades
---

### Post by idefix-b on 2015-10-24
Dear all.

I tried to install Ubuntu Server 15.10 on a Dell PowerEdge R310 using the idrac console (I do not have physical access to the machine).
I have the image on my local computer and "mounted" the image with the virtual device functionality in iDRAC.

While the system is booting it loads fine all the data from the "virtually mounted" CD. The Installer starts and I can configure my language and keyboard.
But it fails then with the error message:
Failed to retrieve the preconfiguration file.

I checked the messages and it seems to have to CDs mounted. One /dev/sr0 and one /dev/sr1.
The device /dev/sr0 is currently mounted on /cdrom.

But the preseed folder is on the disk on /dev/sr1.

Do I have to set here something different that the installer can read the information form the CD?

Thanks.

---

### Post by idefix-b on 2015-10-24
I got it installed by doing:
umount /cdrom
mount /dev/sr1 /cdrom

---

