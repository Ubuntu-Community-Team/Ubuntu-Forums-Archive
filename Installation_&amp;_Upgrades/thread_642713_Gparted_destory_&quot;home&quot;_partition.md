---
title: "Gparted destory &quot;/home&quot; partition"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by Sugi on 2007-12-16
I just installed Gutsy Gibbon hour ago.  Everything went fine, except when for gparted for making partitions.  I made two partitions for Gutsy.  512MB for swap, and 10GB for /root, and I already had my third partition for my /home folder.  

After partition editor, I installed Gutsy and everything was prefect.  I rebooted and everything worked fine.  So, I didn't like my /home directy because it was messy,  So, I popped in my ubuntu live-cd and went to Gparted and reformat my /home folder, but during the reformat Gparted crashed.  So, I open it back up and finish the reformat and did a reboot.  

When my laptop restart, it said it couldn't find the OS.  I'm like, crap I forgot that would mess up the GRUB (or the boot loader).  So, I just reinstall Gutsy Gibbon and reformat my swap, /root, and /home.  Everything went fine the second time around, but when I reboot into the already OS.  The /home (sda3) wasn't there.  So, again I reboot to the live-cd and look into Gparted.  It said it was unmounted and it didn't show any flag for the partition (I gave the sda3 the flag of /home during the installation).  When I look into my /Computer folder and my /media folder there is no sda3 partition.

So, how do I mount my unmounted partition (sda3 aka /home)?  Why is it giving me so many problems?

---

### Post by kdarkentity on 2007-12-17
How do you mount an unmounted partition?, try sudo mount /dev/sda3

---

### Post by avik on 2007-12-17
You can try:

```

sudo mount /dev/sda3 /home

```

---

### Post by Sugi on 2007-12-17
>.<

---

