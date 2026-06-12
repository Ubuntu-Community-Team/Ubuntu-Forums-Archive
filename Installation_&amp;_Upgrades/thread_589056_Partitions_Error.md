---
title: "Partitions Error"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by JustKoichi on 2007-10-23
I'm trying to set up a dual boot on my laptop. I have XP installed right now and I put in the ubuntu disk 7.10 and when I install and click Guided - resize partition # 1 and use freed space and set it to 65.5GB I get an error which says

An error occurred while writing the changes to the storage devices. 

The resize operation is aborted

then I clicked OK and it sends me to the prepare partitions part. 

Last time I did I this it didn't give me a error and it didn't send me to to the prepare partitions part.

Does anyone know why? Because I'm not sure what to put in the partitions part. I have no knowledge in partition things. So if anyone could help me out it would be awesome or teach me step by step on how to create a partition.

---

### Post by Pumalite on 2007-10-23
Defrag XP several times, erase all temp files, then use Gparted Live CD to resize your XP partition (right click). You can keep on making the partitions you'll need:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for home. Then install and use the partitions you made.
(go Manual)

---

### Post by Pumalite on 2007-10-23
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

