---
title: "Noob install - Partitioning Recommendations"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by Dabbler on 2006-09-07
This is my first post with this crowd,so please be gentle  ;) 

I'm installing ubuntu 6.06 for the first time, based on it's user-friendly reputation and my success with running off the CD.  Not so lucky with slackware or mandrake dual-boot setup several years ago, so I walked away.  

This time, setting up on a dedicated P2 333MHz, 384MB Ram 4GB Scsi HDD, 1 GB IDE Hdd.  I'm looking for feedback on partitioning with my limited space.  

I configured the following:
KEEP: the compaq sys utils partition (~10MB)
Create on 4 GB drive: /home ~1GB Primary partition
Create on 4GB drive: / ~3GB Primary partition (for easier upgrades)
Create on 1GB drive: swap (entire drive)

Seems to have worked, but is this optimal given my limited RAM and Disk space?  Are there other recommendations?

---

### Post by zxee on 2006-09-08
Given the cpu you have you might want to give xubuntu a look-it uses xfce instead of gnome, but if the live cd ran satisfactory for you maybe ubuntu will work. Your partitioning is fine AFAIK,(although swap doesn't need to any bigger than twice your ram, but that won't save you much) maybe consider picking up a larger scsi drive on ebay?
Welcome to Ubuntu!

---

### Post by Original Brownster on 2006-09-08
Hi,
There's nothing wrong with the partitioning you have done. I would also say your swap is too big for a desktop, 500Mb is ample. 
My own experience over the years of creating partitions is that it inevitably ends up limiting yourself in someway; the x Mbs you thought for /home is not enough or you didn't envisage that /var took so much. Nowadays I just have one partition for the whole system including /home, the exception for me being I put all my music/video files on one partition that's huge, and mount that as /mnt/multimedia, that way its easy to change distro's (though to be honest I've been using Ubuntu for over a year now and I don't see any need to change). 
If later you buy another disk, it's easy to either move /home onto it, or just create a mount point for the new disk and hang it off of there.

Another good alternative is to use 'logical volume manager' (LVM). Boot needs to be on a standard partition though, not an LVM one. Then you can slice up into whatever partitions using lvm partitions and use LVM to assign extra space to a partition as required, this is cool as you can add a disk, turn it into a volume controlled by the LVM and use it for any of your partitions, /home  or whatever. 

HTH

---

### Post by Dabbler on 2006-09-08
Thanks for the tips.  Added the xubuntu xfce desktop and dropped my baseline idle cpu utilization (no other apps running) from 20% down to 15%.

---

