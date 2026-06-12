---
title: "52 gb free on partition, but home folder is only 2 gb?"
date: 2011-11-28
forum: Installation &amp; Upgrades
---

### Post by grumol on 2011-11-28
i believe i messed up when i manually partitioned the hard drive -- installed 11.10, in place of an older version of ubuntu, and alongside winxp, and a fat partition -- everythings fine, but, as the title says, the home folder says its capacity is 2 gb, yet in terminal it is clear that this ubuntu is installed on a 53gb partition, with 52 still free -- maybe this is due to me putting the mount point as /boot?

---

### Post by fantab on 2011-11-28
> **grumol said:**
> i believe i messed up when i manually partitioned the hard drive -- installed 11.10, in place of an older version of ubuntu, and alongside winxp, and a fat partition -- everythings fine, but, as the title says, the home folder says its capacity is 2 gb, yet in terminal it is clear that this ubuntu is installed on a 53gb partition, with 52 still free -- **maybe this is due to me putting the mount point as /boot?**

What do you mean? have you used /boot instead of /home? 

Could you give some more details about your partitioning and mount-points?

---

### Post by Skaperen on 2011-11-28
Please show outputs from these commands:
```
sudo fdisk -lu /dev/sda
cat /proc/partitions
df -a
```

---

### Post by grumol on 2011-11-29
thanks, but woke up with a clearer head, and i used the live cd gparted to remove my install, then re-installed, and this time i let the installer do the partitions -- now my home folder is over 40gb -- i had made the mistake of thinking i remembered how to do the partitions manually, but it had been a few years

thanks again for your help

---

