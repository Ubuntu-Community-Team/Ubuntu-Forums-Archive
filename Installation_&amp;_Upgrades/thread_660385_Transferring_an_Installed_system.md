---
title: "Transferring an Installed system"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by Scorpuk on 2008-01-06
I am considering moveing from software raid to hardware raid, but that will require reformatting the hard drives to the new hardware raid (thinking on ADAPTEC RAID 31205)


I currently see my option is to create a raid big enough to copy over the current system and then add in the other hdd's, after wiping them.


So my question is how do I, or can I even, transfer the current system onto the new raid?


tnx in advance. :-)

---

### Post by Scorpuk on 2008-01-09
I guess I will just export my mythtv database, doa clean install and import the database back in.

---

### Post by Gina on 2008-01-09
You could use PartImage to backup and restore partitions.  Be careful to create the right sized partition(s) before restoring into them though.

---

### Post by wieman01 on 2008-01-09
Restore them to the right sized partition(s) and resize the partitions afterwards if you have to. Otherwise Partimage will create problems. See my signature for more.

---

