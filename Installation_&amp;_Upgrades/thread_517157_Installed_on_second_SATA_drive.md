---
title: "Installed on second SATA drive"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by JFDsouza on 2007-08-04
I installed Ubuntu 7.04 on my second HDD which is a SATA 80 GB drive on partition /dev/sda3 from live CD. I have PCLinux 2007 on /dev/sda1 and a common swap on /dev/sda5. Partition for / is 4GB and partition for swap is 2GB which is twice the amount of RAM that I have. What I want is to have a common /home partition for both PCLinuxOS and Ubuntu - how do I go about doing this?
Second is that I do not know if the grub installed in hda which is first drive or MBR of sda how can I know? Can I shift the grub to sda - if yes how? [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Pumalite on 2007-08-04
Use this to find out where is your Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
2 GB of Swap is a waste. With the amount of space you are working, better give it 500 MB. 4 GB for '/' is too little. Minimum should be 10 GB. Shared /home will have to be answered by somebody else. Good luck

---

