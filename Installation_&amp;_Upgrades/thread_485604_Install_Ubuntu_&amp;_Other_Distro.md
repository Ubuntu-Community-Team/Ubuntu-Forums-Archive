---
title: "Install Ubuntu &amp; Other Distro"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by icarusjun on 2007-06-27
I have an old working computer with 8GB harddisk... is it possible for me to partition/divide it by 2 (4gb each) and install Ubuntu on the 1st partition... and another Linux distro on the 2nd...

How will I go about doing this...

---

### Post by renzokuken on 2007-06-27
this is acually fairly straight forward.

you could get yourself a gparted livecd, boot it up and format/partition the drive as you desire.

once done, boot up the ubuntu cd, when it comes to the disk manager bit, install it to the first partition (the options on the install wizard are pretty obvious)

then when thats finished, boot up the cd for your second distro and install it on the second partition. the second distro should automatically install GRUB for you so you can choose which distro to boot into when you turn your PC on.

---

