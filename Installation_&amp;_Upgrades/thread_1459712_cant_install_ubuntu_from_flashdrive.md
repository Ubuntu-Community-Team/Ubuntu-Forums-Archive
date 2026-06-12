---
title: "cant install ubuntu from flashdrive?"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by durps on 2010-04-21
well i have a spare hdd but will only be getting it in aboit a week or so, so I'm usiing my flashdrive as an hdd for my laptop. installed ubuntu 9.10 and it's workng pretty well now, besides my messed up keyboard. well the problem is that ubuntu will only work if i use the option to try ubuntu out without any changes. when i try to install it, i run into a problem in the installation steps. in step 4 of 7, when its says prepare partitions, it wont proceed to step 6. it says "no root system is defined, please correct this from the partitioning menu"
what does this mean? is it because i installed the OS on a flashdrive?

thanks for any input!

---

### Post by durps on 2010-04-21
oh yeah, the flashdrive is formatted to fat32 and i dont see any memory options in the partitioning menu.

---

### Post by oldfred on 2010-04-21
Are you using manual install to select partitions or have you not set partitions. The no root means that you have not selected a partition for / (root) and usually swap also has to be selected. If you want a separate /home you also have to select that.

Possibly you have used all 4 primary partitions?

---

### Post by durps on 2010-04-21
im new to modifying pcs and stuff so i dont get exactly what you mean.
but how do you set up a partition?

---

### Post by oldfred on 2010-04-22
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

---

