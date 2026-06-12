---
title: "Installing Ubuntu 18.04 LTS freezes on 'Installation type'"
date: 2018-05-16
forum: Installation &amp; Upgrades
---

### Post by gunnnnii on 2018-05-16
Hi, I'm trying to install Ubuntu on a Lenovo Yoga XXXX. Trying it out works perfectly fine, but in the installation process I hit a wall. 
The problem comes up with the "installation type" screen. When I click "Install now" I get the "no root file system detected". Pressing any other button causes the window to either freeze or crash.
The installation type screen also looks significantly different from the one in the installation instructions.

The error report gives me this message:
ExecutablePath: /usr/lib/ubiquity/bin/ubiquity
Package: ubiquity 18.04.14
Problem type: Crash
Title: ubiquity crashed with TypeError in partman_dialog(): argument of type 'NoneType' is not iterable.

I've found people that have gotten the same error when fast boot was enabled on windows 10, but I have already turned that off.


[IMG]https://i.imgur.com/yk1qTUS.jpg[/IMG]
[IMG]https://i.imgur.com/mwFaYli.jpg[/IMG]

---

### Post by dino99 on 2018-05-16
Looks like you have missed the 'partitioning' steps

[https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by yancek on 2018-05-16
Do you have anything related to fastboot and/or hibernation off?  Do you have any unallocated space available on the drive outside your windows partitions?
On the installation type screen you should see the drives and partitions available on the machine.  If you are installing with a windows 10 system already on the drive you are best off using the manual Something Else option.  You need to select unallocated space or an already existing partition and then click either the + tab or the change tab below the main window.  If you have the system hibernated, it probably won't show anything and you won't be able to do this.

---

### Post by gunnnnii on 2018-05-17
The problem was with the disk being set to RAID but I had to change it to AHCI. Working like a charm now :)
Thanks for the help anyways guys.

---

