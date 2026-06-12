---
title: "Partitioning dual boot Vista &amp; Ubuntu?"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by hobojoe2k1 on 2008-06-01
I just bought a new Toshiba Satellite laptop with two 200gb hard drives, one at 5400rpm and the other at 4200rpm.  I plan on dual-booting Vista and Hardy, but I'm not sure how I should partition the hard drives.  From what I understand, it would be better to have the operating systems on the faster hard drive, is that correct?  Also, I'd like to have a partition that both Vista and Ubuntu could access, so that I can put my music, documents, etc. in one place rather than having two copies of everything.  Should this be on the faster drive also?  How should I format a partition so that both can use it?  Any other partitioning suggestions?

Thanks!

---

### Post by Pumalite on 2008-06-01
In general is best to have both OS's where you have Vista. For installation; you first have to allocate space for Ubuntu with the Vista partitioner. Then install Ubuntu.
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by e_racer1999 on 2008-06-01
I'd like to preface this with the fact that I'm not 100% sure, but what you will want to do is do 3 partitions on one of the drives for ubuntu. One will be the '/' partition, which will be for the OS and programs, one will be the '/home' partition for files, etc, and one will be the 'linuxswap' partition. If you google 'Linux partitions' you can come across a site that should help you determine the best size for these partitions. In order for Vista to be able to recognize your Linux partitions, you are going to want to format them as 'ext2' instead of 'ext3' and there will be a software that you can download to Vista that will allow you to recognize the 'ext2' partitions.

If anyone sees any errors in what I wrote, please do not hesitate to correct them :)

EDIT - a little slow to the draw, and luckily my memory served incorrectly. Fixed.

---

### Post by Pumalite on 2008-06-01
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by mihailojocic on 2008-06-01
If you decide to install both OS I suggest you to install Acronis OS selector to. It is very useful application when mess up something in MBR. ;-) Helped me so many times!!!

---

### Post by Pumalite on 2008-06-01
Monsense. Grub is the best boot loader around.

---

### Post by mihailojocic on 2008-06-01
> **Pumalite said:**
> Monsense. Grub is the best boot loader around.

OK, you are probably right, but I'm not so familiar with grub and I'm stuck few times so... It's easy application and have boot CD so if I mess up i just run CD and click repair. Sorry if I'm stupid but I don't know why is that bad or whatever your opinion is.

---

### Post by zvacet on 2008-06-01
> you are going to want to format them as 'ext2' instead of 'ext3' and there will be a software that you can download to Vista that will allow you to recognize the 'ext2' partitions.

Ubuntu use ext3 filesystem format and [this]("http://www.fs-driver.org/") program is what you need to install on your Vista partition and you will be able to see Ubuntu partition.

---

### Post by Pumalite on 2008-06-01
Or install this driver to see ext3:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

