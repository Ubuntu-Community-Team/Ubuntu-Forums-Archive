---
title: "Win7/Ubuntu Separate HDD boot issues"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by Dagger576 on 2010-06-05
Hey guys. I'm having some problems with getting Ubuntu 10.4 installed correctly and I'm not sure what else to do. 

I've got 5 Sata hard drives, none of them are set up in a raid. 4 of them are 500gb and one of them is 160gb. I've got windows 7 running on one of the 4 500 gb hard drives, and I've installed Ubuntu on the 160gb. 

The issue I'm having, is that Grub won't load. After a little digging I found I had to specify where to install Grub, so I went ahead and had it install to the 160gb drive and figured I'd set that in the bios to boot first. Whenever I try to run from the hard drive I get a quick error message that occurs too quickly to catch, then a blank screen. A few moments later, Ubuntu comes up without ever giving me the option to boot windows. 

I did some reading in the forums and saw that some people suggested opening the terminal and trying sudo update-grub2, so I tried that. When I did, I got the following:

> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-22-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Drive" [2/4] on /dev/sdc
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Drive" [2/4] on /dev/sde
done

I also found something about trying sudo grub-mkconfig or something along those lines, and when I ran that, I got the same message at the end.

Anybody have any suggestions?

---

### Post by oldfred on 2010-06-05
You said you do not have raid, but were the drives ever raid? Drives save meta data that now interfers with grub2. DO NOT run this if you have raid.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
etc if more drives
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

