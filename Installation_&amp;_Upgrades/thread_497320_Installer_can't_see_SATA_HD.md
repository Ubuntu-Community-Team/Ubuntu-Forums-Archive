---
title: "Installer can't see SATA HD"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by mastercheif on 2007-07-10
Hey, I'm new to linux and I need a little help getting Ubuntu installed. I am trying to install from the Live CD. When running the installer, it only recognizes my secondary HD, my 40GB on IDE formatted for NFTS. My main HD is a 160GB Samsung on SATA, also formated NFTS. I am using a Nvidia N-Force 3 Ultra mobo with a silicon imgage SATA controler. 

Thanks!

EDIT: Always check your connections ;)

---

### Post by phidia on 2007-07-10
From the livecd open terminal type fdisk -l <enter> does the sata drive show in the output?
You can also type dmesg <enter> in the terminal and the output should show the system boot up/hardware recognition process.

---

### Post by dabl on 2007-07-10
You might do better partitioning and formatting your SATA partition with a GParted Live CD first, and then use the Ubuntu Alernate Install CD and use text mode to install Feisty.  Here's where you download the GParted Live CD ISO image: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

No guarantees -- your combination is known to be tough -- here's a thread that shows how it can be done: [http://kubuntuforums.net/forums/index.php?topic=3083082.0](http://kubuntuforums.net/forums/index.php?topic=3083082.0)

---

