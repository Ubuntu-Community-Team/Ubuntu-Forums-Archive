---
title: "Raid broken after upgrade to Hardy Heron"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by yzf600 on 2008-04-26
I upgraded to Hardy Heron last night. Upon reboot I freaked as my /dev/md0 RAID0 parition could not be mounted. 

Luckily, I was able to fix it this morning by re-assembling it: 

```
sudo -s
mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
mdadm --examine --scan >> /etc/mdadm/mdadm.conf
exit

```

Be sure to change the md0, sda1, and sdb1 to the proper values for your configuration. 

I'm putting this thread out here so if anyone else runs into this, they won't have to spend an hour looking for a solution.

---

