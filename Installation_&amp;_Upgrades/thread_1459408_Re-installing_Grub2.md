---
title: "Re-installing Grub2"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by atliia on 2010-04-21
I have a problem similar to the one outline in[ this]("http://ubuntuforums.org/showthread.php?t=1392314") thread. I updated my dell datasafe backuo for the first time, my laptop restarted and then I received the error listed. 

I have booted with my windows 7 install and my installation of windows is still present. Based on this information I believe the problem is with the grub. I would like to just re-install however, I am not able to open a terminal. When I boot from my live CD of 9.10 the desktop is acting strange visually. There are vertical lines running across my screen and nothing is really visible. This only happenes when I try to install from main menu or try ubuntu with out any change to your computer. 

If anyone has another way for me to access a terminal or fix my grub install I would be grateful!

---

### Post by atliia on 2010-04-21
the problem I am having is that I can not get a terminal going. the gui from the live cd is mess up to say the least.

---

### Post by atliia on 2010-04-23
I have found another live CD and was able to run a terminal. 

In the terminal I use the ```
Mount /dev/sda6 /mnt
``` command to mount my ubuntu partition. This and then run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

I would reboot remove the live cd and my grub menu would come up. however, I would need to reboot in the live cd at the next boot because I get the same error on each attempt. 

At this point I decided to do a fresh install of ubuntu 9.10 from a live CD on sda6 partition. 

At this point when I boot I get a grub loader menu with out any boot options and only a command prompt. 

My hdd is set up in the following partitions
/dev/sda1 Dell utility 
/dev/sda2 HPFS/NTFS(recovery When I run fdisk this is the only boot I see marked) 
/dev/sda3 HPFS/NTFS(C: Drive)
/dev/sda4 Extended partition
/dev/sda5 NTFS Shared Partition
/dev/sda6 EXT4 Ubuntu Partition

---

### Post by linuxd00 on 2010-04-23
hi, have you seen my thread? does this sound like your problem?

[http://www.uluga.ubuntuforums.org/showthread.php?t=1443763](http://www.uluga.ubuntuforums.org/showthread.php?t=1443763)

---

