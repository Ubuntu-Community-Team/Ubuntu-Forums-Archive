---
title: "Dual boot problem (GNU Grub minimal)"
date: 2019-09-13
forum: Installation &amp; Upgrades
---

### Post by gezginrocker on 2019-09-13
I'm dual booting Windows & Linux. After initial install I was getting the Grub menu on boot. Then after a few reboots, it suddenly started showing this one:


[[IMG]https://i.ibb.co/r3zXgBt/1.jpg[/IMG]]("https://ibb.co/G98rXZJ")


If I type exit, the screen below comes up. And when I choose Ubuntu, normal Grub menu comes up. Then I can boot into Linux or Windows.


[[IMG]https://i.ibb.co/1M0d4yy/1.jpg[/IMG]]("https://ibb.co/QkJCxSS")


I used Boot Repair and afterwards it started showing normal Grub boot menu again, but this time I wasn't able to boot into Windows. So I removed Linux, deleted Efi entries and then reinstalled Linux, but I'm facing the same problem yet again. 


What is causing this, and is there a way to fix it except using Boot Repair?


Also, Windows & Linux are on different hard drives. But according to Grub menu both Efi entries are on the SSD. Shouldn't Linux efi entry be on the 2nd hard drive? 


Thanks

---

### Post by oldfred on 2019-09-13
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Ubuntu's Ubiquity installer only installs grub to first ESP it sees. Old bug, but now work around if desired.
       
 Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)

---

### Post by #&amp;thj^% on 2019-09-13
See if this helps: [https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives](https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives)
Ninja'd by oldfred :D

---

