---
title: "wrong label on mounted volume"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by jyp on 2007-10-06
Just installed Ubuntu 7.04 in order to upgrade to 7.10 (in a few days !)

I have 3 HD and a few partitions on them ; 

-> HD-1 : /dev/sda1 mounted on / , /dev/sda2 swap, /dev/sda5 mnt on /home, /dev/sda6 mnt on /usr/local. No problem here.

>>> HD-2
/dev/sdb1 mnt on /media/archive_01 ; on the desktop the **label is /data** 
/dev/sdb2 mnt on /media/home_bu ; on the desktop the label is correct /home_bu

>>> HD-3
/dev/sdc1 mnt on /media/archive_02 ; on the desktop the **label is /archive_01** which is pretty confusing since the mount point is /media/archive_02 !!
/dev/sdc2 mnt on /media/fat32 ; on the desktop the label is correct: fat32 but no /

So 2 of 4 labels wrong ; I never labeled any of those partitions ; the installation did it for me, thank you.

Since the mount points are recorded in /etc/fstab, I cannot easily umount .

How can I correct the faulty labels.

Thank you.
jyp

---

### Post by logos34 on 2007-10-07
If they're ext3, use tune2fs or e2label to rename them, then edit fstab
[http://www.linux.com/base/ldp/howto/Partition/labels.htmlt](http://www.linux.com/base/ldp/howto/Partition/labels.htmlt)

---

### Post by jyp on 2007-10-07
Thank you for your reply; I will bookmark the link for future use.

I did try to use both these tools (e2label and tune2fs) but I got an error message in both cases. I then try to use gconf-editor to change the labels but no success there either.

I did a fresh install of Kubuntu and everything is ok; the partitions carry their sd* id so there is less confusion. I think I feel more comfortable in the kde environment anyway but no hard feelings against gnome. 

Thanks again.
jyp

---

