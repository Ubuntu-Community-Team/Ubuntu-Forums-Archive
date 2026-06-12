---
title: "Modifying Ubuntu's parition"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by nimeni on 2008-04-08
I have a bit of a problem, meaning that the partition where Ubuntu is installed is getting full, so i got some space to add to it. The problem is that Ubuntu's partition is locked and i cannot add space to it, while free space on it becomes less. Is there any way i can do that?

---

### Post by mikewhatever on 2008-04-08
First run <sudo apt-get clean> and <sudo apt-get autoremove>. To resize a partition, it has to be unmounted, so use Gparted Live cd.

---

### Post by renzokuken on 2008-04-08
you cant change partitions while the partition is mounted (i.e. you are booted into ubuntu)

i'd recommend using the gparted livecd instead (google for it).

make sure you know what you are doing though before you try anything

---

### Post by fela on 2008-04-08
gparted is included in the Ubuntu LiveCD, so i reccomend using that.

---

### Post by housam on 2008-04-08
the [[COLOR="Red"]_newer version of Gparted _[/COLOR]]("http://gparted-livecd.tuxfamily.org/")will allow you doing this task

---

### Post by nimeni on 2008-04-09
Thanks a lot.

---

