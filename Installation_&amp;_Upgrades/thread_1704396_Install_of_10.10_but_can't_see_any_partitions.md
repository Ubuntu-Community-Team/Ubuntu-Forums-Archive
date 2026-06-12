---
title: "Install of 10.10 but can't see any partitions"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by Larrylens on 2011-03-10
Hi,
 
I'm somewhat new to Ubuntu. Have only used it while running it from a CD. I want to install it on my machine but I have a setup which, after reading through some posts, may be causing me hassle. Here is my setup:
 
2 drives in my PC, one 250GB and the other 320GB. The 320GB is my data drive. The 250GB is partitioned into 3. One partition has Windows7, one has Windows XP Pro and the other is formatted but blank and I want to install Ubuntu to this.
 
The problem is when I load up the installer from the CD it can only see my 320GB disk. If I unplug the 320GB disk then the installer says there are no paritions available and the list to choose from is empty. If I continue on to run from the CD (Try Ubuntu) then I can see the drives under Places.
 
Have I got too many partitions? Any help would be greatly appreciated and as I said I'm new to Unbuntu but I'm a techy so can try anything anyone suggests.
 
Thanks

---

### Post by Hakunka-Matata on 2011-03-10
Welcome to the forums.

No, you don't have too many partitions.  Use Gparted "System > Administration > GParted" to look at your disc partitioning.

Also run ```
sudo fdisk -l
``` in a Terminal and paste the output into code tags #past text here# then post back,

---

### Post by billbear on 2011-03-10
The partition table may have some problems.
Please provide the info Hakunka asked for.
also provide the outputs of ```
sudo fdisk -lu
```
and
```
sudo parted -l
```

---

