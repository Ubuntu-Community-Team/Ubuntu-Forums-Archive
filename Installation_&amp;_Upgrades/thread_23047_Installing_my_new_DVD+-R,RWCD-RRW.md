---
title: "Installing my new DVD+/-R,RW/CD-R/RW"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by jery_wang2002 on 2005-03-30
I just bought new LG DVD+/-R,RW/CD-R/RW as secondary slave (dev/hdd). Somehow it was not autodetected by Hoary. I installed Hoary Array CD 7 few days before I installed the new drive.

I googling around and got info on adding something to /etc/fstab

Somehow the config in this /etc/fstab is not so reliable, i.e.

1. Cannot eject
2. Difficulty in mounting (it's not automounting)


And I am totally in the dark with the entry in the /etc/fstab

Furthermore, I'd like to have UDF support in my Hoary too, so that I can use my DVD+RW media as backup for my work.

Anyone can share with us?

Many Thanks,
Jerry

---

### Post by kagou on 2005-03-31
How can we help you if you don't show us your /etc/fstab ?

---

### Post by jery_wang2002 on 2005-03-31
[QUOTE=kagou]How can we help you if you don't show us your /etc/fstab ?[/QUOTE]
 Here is my /etc/fstab

My DVDRW is /dev/hdd

proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd  	/media/dvdrw  	auto  defaults,noatime,user,noauto 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/pktcdvd/dvdwriter /media/dvdrw udf noauto,noatime,rw,dev,users 0 0

---

