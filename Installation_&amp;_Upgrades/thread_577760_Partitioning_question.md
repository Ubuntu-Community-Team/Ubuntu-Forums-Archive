---
title: "Partitioning question"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by OMRebel on 2007-10-16
I have a Dell laptop that has an 80 GB HD in it.  I have a 10 GB partition that I am wanting to install Ubuntu 7.10 on.  Going through the installation, it doesn't give me the option to install Ubuntu on that 10 GB partition (it will only display the 80 GB drive).  Anyways, when I click on Manual, I have the following:

/dev/sda
    /dev/sda1  fat16  /media/sda1  82 MB
    /dev/sda2  fat32  /media/sda2  10737 MB
    /dev/sda3  ntfs    /media/sda3   69204 MB  (has Vista installed on it - required for school and work)

So, I am wanting to install Ubuntu on /dev/sda2. 

So, I deleted the /dev/sda2 partition, and whenever I go to create it, what sizes should I create and what types?  Primary/Logical, ext3/swap, beginning/end, etc....?

The laptop has 1 GB of RAM.

Thanks everyone!

---

### Post by OMRebel on 2007-10-16
Found a great tutorial that I went by to get it going.  Should have search just a little bit more.  

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

:o)

---

