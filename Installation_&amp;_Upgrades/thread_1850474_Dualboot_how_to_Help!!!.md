---
title: "Dualboot how to??? Help!!!"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by hJ1ub5V4 on 2011-09-26
Hi floks,

i had linux 10.10 on my netbook. i created a partition to install windows 7, i installed it on ntfs partition. but now it only loads windows 7!!!! i booted from gparted cd, and the ext4 partition with ubuntu in was there. i actually knew a program to show windows and linux on the boot screen. but i forgot it's name (this program was installed on windows). cas someone help me???)    ):P

---

### Post by JRV on 2011-09-26
You need to re-install grub2, the Windows install wiped out the grub2 installation in your Master Boot Record.

To fix it I downloaded the Rescatux disk from this site: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Boot this live CD and follow the prompts.

This is the easiest way I know of to fix Grub2.

---

### Post by raja.genupula on 2011-09-26
+1

another method here, its worked for me. 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
all the best

---

