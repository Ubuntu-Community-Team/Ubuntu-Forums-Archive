---
title: "Help! need to restore /home partition..."
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by Baldrick_NZ on 2013-10-26
Hi all,

Having upgraded to 13.10 using a fresh DVD install but using my old /home partition, I decided to back-up only the important files in my home partition and reformat that drive. 

The problem is that now when I reboot, system tells me it can't find my /home partition. 

It'll be something silly that I'm forgetting to do, so any help to resurrect my home partition would be very greatly appreciated!

EDIT: To clarify, I can see the new /home patition and have the UUID to point to. I just need some guidance as to how to point to it.

---

### Post by oldfred on 2013-10-26
If you reformatted it after your install, then the UUID in fstab has an old UUID not the new UUID. You may just need to change it. Or if you installed without mounting the /home then you do not have an entry in fstab. Your /home then is inside your / (root) and you need to move existing settings into your partition.

 If just update to UUID.
       # To clear cache and get new view:
sudo blkid -c /dev/null -o list
      
 # modify fstab to mount directory
gksudo gedit /etc/fstab

Also shows typical mount in fstab. 
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

