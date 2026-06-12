---
title: "Installation Partition Problems"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Phib3r_0ptik on 2007-10-19
I have a Toshiba laptop with and 80gb HDD.

 I currently have windows xp installed, and I want to install Ubuntu on a 2gb partition and dual boot.

When running the Ubuntu 7.04 installer I get to 'prepare disk space' I chose 'guided' and selected a 20.3gb partition and pressed ok. I then receive an error 'Resize operation failure - an error occurred while writing the changes to the storage devices. The resize operation is aborted'. 

I have tried rebooting my computer and trying again, I have even tried using the Ubuntu 6.06 installer and the same thing happened. :confused:

HELP!!!

Thanks
Ben

---

### Post by ldesilva on 2007-10-19
I will suggest you use a 3rd party disk re-sizer. I did that using System RescueCD 0.40. It's has a free disk repartitioning utility. That is what I have done on my Vista laptop and it works very well.

---

### Post by zyg0t3 on 2007-10-19
I'll second system rescue. It partitions like a charm. Just make sure you know what your doing if your dual booting cause you could loose access to your vista partition if you delete the linux partition. MBR's and all that nice stuff. Anyway,

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Have fun.

---

### Post by ElSeeDee on 2007-10-19
> **zyg0t3 said:**
> you could loose access to your vista partition

Dude, the OP is running XP. If he was running Vista, he could do the re-partitioning through Vista's Disk Manager.

---

### Post by Chainz on 2007-10-19
Have you tried "manual" instead of "guided" partitioning?

---

### Post by bigken on 2007-10-19
ist you should defrag windows a couple of times and use vista to resize your hdd

sorry your running xp try using the gparted live CD

---

