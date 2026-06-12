---
title: "root part @ 100% after fresh install"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by eeerik on 2007-09-27
hey!

I just did a fresh install of ubuntu, using guided partition setup during install (alternate cd, text mode install, feisty fawn). /dev/hdc1 is master and is harddrive is 80gb but it seems that installation process made / only 2.1gb which meant that upon boot it was already at 100% and I am basicly locked to not doing anything - x will not allow me to login giving me the error "GDM could not write your authorization file - this could be due to full harddrive or permissions etc". Initially I thought it was the permissions, but df -h gives 100% at /. 

I dont know why the installation process made the partition so small, and I suppose I could reinstall it and manual setup the partitions, but is there anyway I can resize the root partition?

Thanks in advance,
Erik.

---

### Post by Pumalite on 2007-09-27
Repartition with Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and make partitions ahead of time:
10 GB '/'
500 MB /swap
The rest for home.
Install and utilize the partitions already made.

---

### Post by PmDematagoda on 2007-09-27
It would be better if you posted the amount of RAM you have in your PC, because 500Mb of swap may not be enough for your PC, especially if you do tasks that use a lot of memory.

---

