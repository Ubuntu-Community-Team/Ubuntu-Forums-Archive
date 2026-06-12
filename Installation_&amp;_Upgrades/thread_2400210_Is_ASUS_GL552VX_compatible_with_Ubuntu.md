---
title: "Is ASUS GL552VX compatible with Ubuntu?"
date: 2018-09-03
forum: Installation &amp; Upgrades
---

### Post by topraka on 2018-09-03
Hello  all,

I tried to install the latest version of Ubuntu (ubuntu-18.04.1-desktop-amd64) on my Asus laptop, but after I choose install it hangs after about five minutes.


I thought I should first check if my computer is compatible with Ubuntu.


Here are my computer suspects which is currently running Windows 10 home edition:


Model:	 GL552VX
Processor: Intel I 7 – 6700 HQ at 2.60 GHz
RAM: 16 GB
System type: 64 bit operating system, x 64 – base processor


256 GB of space on  SSD,  87 GB free
1 TB of space on HDD, 193 GB free

Thanks!

---

### Post by oldfred on 2018-09-03
Similar models from same brand have same or very similar issues.
Bigger differences between Intel & AMD.

You probably need a boot parameter like these:

       ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
ASUS X540U pci=noaer instead of pci=nomsi and it also worked
[https://ubuntuforums.org/showthread.php?t=2391201](https://ubuntuforums.org/showthread.php?t=2391201)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)

---

