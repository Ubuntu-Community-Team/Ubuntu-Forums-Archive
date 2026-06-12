---
title: "Problems in recovering grub2 after installing windows 7"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by sydcanem2010 on 2010-10-21
Hello,
 
I used to dual boot between windows 7 and ubuntu 10.04. But after reinstalling windows 7 on my pc, i lost the grub menu. I followed the instructions on this site
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
but after the *sudo grub-install --root-directory=/media/(mylinuxUUID) /dev/sda5*i got this following error.
grub-install: warn: Attempting to install grub on a partition instead of the MBR. Not a good idea...
 
it says to use *--force *command to continue the installation. After the installation finished and rebooted, I can't see the grub2 menu. Tried pressing the shift key during boot but still there's no grub2 menu appeared.

can anyone have an idea on this?

---

### Post by mikewhatever on 2010-10-21
You can't see the Grub menu because you've installed Grub to a partition and not the MBR, in other words, /dev/sda5 instead of /dev/sda. The guide you followed doesn't have the '5'. Why do you?

---

