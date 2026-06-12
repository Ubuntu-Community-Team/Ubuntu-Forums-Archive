---
title: "Partitioning Help"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by Arandomcow5 on 2006-08-21
Ok so i decided to get rid of windows (yay!) and now i need to partition some stuff.

So far i have everything set up almost the way i like it:
1GB linux-swap
10GB ext3 (for the OS)

then a 138.05GB extended partition with:
43.18GB unallocated
94.87 ext3 (for /home)

i want to get the extra 43.18GBs into the home folder (and maybe delete the extended partition if needed)...but i cant figure out how to do so w/o deleting my /home partition (which i really don't want to do because it would take me months to retrieve most of that data back)

what should i do?
edit: right now im just going to install linux like this and figure out the partition some other time...i need a non-live-cd-OS atm

heres an screenshot of the partitioner:
[IMG]http://img174.imageshack.us/img174/7117/screenshotxs7.png[/IMG]

---

### Post by BitTorrentBuddha on 2006-08-21
Unfortunately, this isn't possible, it would require moving partitions as more space can only be added to the end (not the beginning as you have it.) It's frustrating but it's the way it works.

---

### Post by catlett on 2006-08-21
You are making things more complicated than they need to be. Just format the unallocated space as an ext3 partition and that's it. Just have it as an accessable partition. [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html) That will tell you how to mount a partition after you create it.
Just use gparted live. It is a live cd with the partitioner gparted on it. Make the unallocated space an ext3 partition. If you are going to install (I think you said you are going to install but keep the home untouched) then the installer will autopmaticaly mount it and you won't need the link above. Just make the partition before you install. It is the simple solution but it will keep your data safe and give you access to that space. Oh yeah here is gparted's site [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Arandomcow5 on 2006-08-21
Could i mount both partitions to /home? or would that screw everything up?

---

### Post by catlett on 2006-08-21
No but you could mount it to /home/extra (extra is just an example but you could mount it to a folder in home)

---

### Post by BitTorrentBuddha on 2006-08-22
If you have/can make extra room in a separate partition as big or bigger than your home partition, you can move your home partition to a further left block and then delete the old one, making room to the right for the new partition to increase in size. Follow [these instructions](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) loosely for moving your partitions. Hope that works for you.

---

