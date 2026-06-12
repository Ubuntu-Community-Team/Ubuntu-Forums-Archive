---
title: "LVG creation 6.06 Server error"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by petrol on 2006-07-06
All,

I have a fresh install of the Dapper Server. I have a very clean install on a 10GB IDE drive(very pleased). I have a PCI SCSI card that has an external SCSI drive enclosure attached. I am able to see the disks in fdisk and make partitions on them. mkfs seems to go smoothly with ext2. The problem comes when trying to make a LVG. First I activate the partitioned drives by using 'sudo pvcreate /dev/sda1 .../sdb1 .../sdc1 .../sdd1'. They are all successful. I then try to run 'sudo vgcreate datasilo /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1'
and I them get the error:

No physical volume label read from /dev/sda1
/dev/sda1 not identified as an existing physical volume
Unable to add physical volume '/dev/sda1' to volume group 'datasilo'.

I have tried mkfs with ext3 and linux LVM, but they all return the same result. One interesting thing that I did see after the pvcreate is that there was a device /dev/mvhs(or something like this)/sda1 I think I saw this when using sudo pvdisplay. I am unable to replicate tonight as I am away from my server. If more details are needed I will be able to replicate Thursday.

Thanks to all who take time and/or brain cells to help me.

Jeff
:grin: 
It's good to be back after a brief hiatus from the forums.

---

### Post by zitch on 2006-07-06
Can you copy and paste the exact input and output here?  Using SSH from another system?  I'm not seeing anything immediately wrong here.  I might do a quick test later tonight in a VM to see if I can recreate this.

[This HOW-TO](http://www.tldp.org/HOWTO/LVM-HOWTO/index.html) was a big help to me whenever I was doing my own server upgrade with LVM on RAID 1 recently, but I'm sure you've seen this already.

---

