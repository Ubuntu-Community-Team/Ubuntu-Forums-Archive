---
title: "Reinstall newer version of Ubuntu on an existing partition"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by anupamamr on 2012-08-09
Greetings !
 
I started with a Windows 7 machine and wanted to have Ubuntu as well.
I used the "Install Side by Side" option to install 9.10. So I had a dual boot system (ubuntu 9.10 and Windows 7) with Grub Loader.
 
After this point, I got a "black screen" when I boot into ubuntu, because of the display driver incompatibility, specific to my laptop (lenovo g550). 
 
I did not bother to fix the issue, because I had to get going. I used Wubi to install 9.04 inside windows, which worked well.
 
Now I want to upgrade my ubuntu to 10.04. I want to do a fresh install of 10.04 over the 9.10 (which is not working). 
 
How can I do this ? I want to do this without losing anything on any of the partitions (windows 7 or Ubuntu 9.04) except the one on which the 9.10 is installed.
 
Thanks for any help.
Anupama.

---

### Post by oldfred on 2012-08-09
Welcome to the forums.

You will need to use manual install or something else. It will give you the option to choose which partitions to use for what / (root), /home and it swap exists it should automatically find it. You also have to specify format usually ext4 for / and /home if you have it. If you have /home but want to save the data DO NOT check format on /home.

You also can from liveCD use gparted and  just delete the / & swap partitions and then let is install side by side to the unallocated space.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

