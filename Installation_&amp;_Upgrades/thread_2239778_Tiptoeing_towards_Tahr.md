---
title: "Tiptoeing towards Tahr"
date: 2014-08-15
forum: Installation &amp; Upgrades
---

### Post by Panawe on 2014-08-15
Having had no luck upgrading from 12.04LTS to 14.04 via Package Manager (another thread!) I looked at installing from a DVD. 

It started okay but when I went for the option to install alongside the existing OSes the program offered me only the option of installing on my backup hard drive (sdb) instead of replacing 12.04 on my primary had drive (sda). I'm sure everything would have worked but I don't want 14.04 on my backup drive!

12.04 is currently installed on partition sda5 on my primary HD.

I can always stick with 12.04 for the time being I guess, I'm just curious about 14.04.

---

### Post by oldfred on 2014-08-15
Best to only use Something Else. 
The reinstall options even if they say overwrite Ubuntu erase entire hard drive.
       Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not highlight changing boot loader to sdb, if installing to external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by Panawe on 2014-08-16
Yes, thanks for this. I shall study carefully before upgrading.

---

