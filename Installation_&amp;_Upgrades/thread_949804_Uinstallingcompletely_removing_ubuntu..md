---
title: "Uinstalling/completely removing ubuntu."
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by smooth_dudes on 2008-10-16
well my problem is:
I have installed ubuntu 8.04 on my laptop and i would like to install windows xp. Now when i try to install windows i get this blue failure screen. Now im quite sure that this is due to the harddisk formatting which is ext3. So im trying to format the harddisk into something which windows will recognize, but this however seems impossible. When i try to run the ubuntu liveCD and open gparted, i do not have the option to format the harddrive...

so essetially my question is: how do i completely overwrite or remove my ubuntu installation? so that i can install something else.

(I plan to re-install ubuntu as a partition after installing windows, because i want both systems)
(The reason i think the windows installation problem has something to do with the format, is because i managed to install it in virtualbox with no problems at all)

---

### Post by Elfy on 2008-10-16
I suspect that it's because swap is mounted. In gparted is there a key/padlock next to the swap - if so right click and unmount.

You should be able to resize the existing partitions leaving room for xp to install to if you prefer.

If that is the case, please open aterminal and run this, post the output and we give more informed advice.

```
sudo fdisk -l
```

If you do want to start both from new then delete all the partitions.

---

### Post by smooth_dudes on 2008-10-16
Alright now i got it done with gparted. The error in the windows installation still occurs though. Now first thing that hits me is that gparted says that the partition is unallocated, that the filesystem is unallocated, and that the size is 232.88GB.

now why is it 232.88GB? my harddisk is supposed to be 250GB... what takes up the remaining 28.22GB? and could that be the cause to windows still failing to install? or is it something entirely deffirent? :P

---

### Post by zvacet on 2008-10-16
If you want to uninstall Ubuntu download [Gparted live CD]("http://gparted.sourceforge.net/") and delete all that you have on disc.After that install Windows.

---

### Post by qwertymodo on 2008-10-16
One gigabyte is ACTUALLY 1024 megabytes, which is ACTUALLY 1024 kilobytes which is ACTUALLY 1204 bytes.

A hard drive is ADVERTISED as 250 gigabytes using the measurement of 1000, not 1024.

i.e. your hard drive was ADVERTISED as 250 gigabytes, but it is ACTUALLY 250,000,000,000 bytes, which is ACTUALLY 232.83 Gb based on the real calculations.

Basically, 250 looks better than 232.83 on the side of the box. :P

---

