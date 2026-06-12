---
title: "“Ubi-partman crashed&quot; in Ubuntu 18"
date: 2018-05-07
forum: Installation &amp; Upgrades
---

### Post by athrunzala on 2018-05-07
Help this Ubuntu 18.04's _***"ubi-partman crashed: ubi-partman failed with exit code 141"***_ always show during my installation process in my ASUS X540U laptop.  I never had this problem with my Ubuntu 17 installations before. 



Btw, I have Windows 10 and Linuxmint in my Harddisk partitions.  Any help will be truly appreciated!

---

### Post by oldfred on 2018-05-07
Have you tried partitioning in advance with gparated from live installer and then use Something Else to choose (change button) the partition you want to use as / & format as ext4.

Post this:
sudo parted -l

Did you boot in UEFI boot mode? Assuming all other installs are UEFI.

May be similar model?
 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by athrunzala on 2018-05-08
Finally got it. There are no problems regarding UEFI. 
I just inserted the pci=nomsi before the "quite slash" option in the first installation boot by Typing 'e' at the installation menu of Ubuntu where it displays Try Ubuntu or Install Ubuntu. 

 Actually I also tried pci=noaer instead of pci=nomsi and it also worked! So guys if pci=nomsi doesn't work for you, just try pci=noaer.

Actually, it is pci=noaer which I used as my correct solution before when my pci bus errors is filling up my sys logs last year everytime I load my ASUS computer. It just so happens that in Ubuntu 18, this is the first time that this occurs during_ my first installation process, _this did not happen in Ubuntu 17.

Thank you for your help oldfred!

---

