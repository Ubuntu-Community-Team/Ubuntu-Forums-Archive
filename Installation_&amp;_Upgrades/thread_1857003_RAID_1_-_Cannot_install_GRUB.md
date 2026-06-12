---
title: "RAID 1 - Cannot install GRUB"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by Wednesday on 2011-10-09
This is a repost from 
[http://ubuntuforums.org/showthread.php?p=11325012&posted=1#post11325012](http://ubuntuforums.org/showthread.php?p=11325012&posted=1#post11325012)

I am having similar problems. I need help. I have made a fresh install from the alternate CD and have set up a raid 1 array with my first two disks. (Please ignore the other disks - one is blank and the other came with the dell machine). 
I created a set of identical partitions on the first two disks and then assembled the raid1 arrays. The Installation fails 
"unable to install grub in /dev/sda 
executing 'grub-install /dev/sda' failed".
I then booted into the repair disk and tried the following command:
grub-install --root-directory=/ /dev/md0

This failed with the following:

/usr/sbin/grub-setup: error:unable to identify a filesystem in /dev/sda; safety check can't be performed.

/dev/mapper seemed to only contain control and nothing else

I tried to follow the suggestion:
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && gksu boot-repair
but a window appeared showing
" Enabling RAID. This may require several minutes" bit it did not stop ( I waited 20 mins).

I attach my message.txt from the boot_info_script
Please can somebody help me?
Thanks

---

