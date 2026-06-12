---
title: "Organising partitions to support upgrades?"
date: 2015-03-26
forum: Installation &amp; Upgrades
---

### Post by m-brooks on 2015-03-26
My current lubuntu installation is my second. I had to abandon my first after I found that it was unable to upgrade itself due to filling its root partition.
So I asked the question on this forum - where does the upgrade process consume space? I was told that it is /var/cache/apt/archives.
I have an EeePC, hence my space limitations. It has a 4GB main SSD and an 8GB SD card.
So for my second installation I configured matters so that /var had loads of space. It still does - 3.1G still free out of 3.7G.
However, I have just hit the same problem. The upgrade is reporting that it needs 360M and that in order to get that I have to free up 320M. This tells me that I have only 40M on the filesystem location that it is interested in.
df -h gives me:

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       3.7G  3.4G   39M  99% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            995M  4.0K  995M   1% /dev
tmpfs           201M  1.1M  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1004M     0 1004M   0% /run/shm
none            100M   24K  100M   1% /run/user
/dev/sdb1       3.7G  1.5G  2.0G  43% /home
/dev/sdb5       3.7G  365M  3.1G  11% /var

As you can see I have 39M free on the root. So the upgrade isn't looking for space in /var.

Can anyone give me any more useful info here? I don't want to go through all this again.

Regards,
Michael

---

### Post by TheFu on 2015-03-26
On such a small drive, I'd ... 
a) replace it with a larger SSD.  30G at least - 60G seems to be the $50 spot.
b) Only have 1 partition on each SSD if they are less than 16G.
c) Not use any DE, stick to a pure WM GUI and minimal OS install.

Disks run out of room for 2 reasons - inodes and sectors.
```
df -i
df -k
```
On really small partitions, inodes go first. You may want to manually allocate and tune the inodes for any ext2/3/4 partition smaller than 10G.

Also, it would be really helpful to me if you used **code tags** so things line up, please.

---

### Post by Impavidus on 2015-03-26
Updates are cached in /var, so if you don't clean it regularly /var will grow. But as they get updated, packages may slowly grow too, and the files belonging to these are spread all over your system. Old kernels are not automatically removed, so /boot can grow quite rapidly. Try removing some old kernels + kernel headers, if you don't do that regularly. It may free a few hundred MB. The packages you're looking for are called linux-image-<some version> and linux-headers-<some version>

You could try moving /usr to the SD card (it's much bigger than /var), but I agree that the best solution would be to install a larger SSD. 4GB is so small that you will get trouble whatever you try.

---

### Post by TheFu on 2015-03-26
Do not just delete files - always use the package manager if that is how something was installed, then that file must be removed in the same way. Deleting files that are managed by the package manager will cause difficulties.

---

### Post by grahammechanical on 2015-03-26
Seeing as you have /home on sdb1 you can do a fresh install without risking your data in /home. You would use the Something Else option and mount sda1 as / sdb1 as /home and sdb5 as  /var if you still want to keep that partition arrangement.

It is sda1 that is running out of space. When we install we are asked to confirm that the minimum disk space requirement is met. Although I recently installed Lubuntu I did not pay attention to this minimum requirement as the partition I was installing to was large enough to install Ubuntu in and then some.

I am not sure, but I am wondering if the 3.7 GB space of sda1 is large enough to install Lubuntu in. /dev seems to have 995 M set aside for it but only using 1%.

Regards.

---

### Post by m-brooks on 2015-03-26
Guys, thanks for all the helpful replies - much appreciated. :)

Michael

---

### Post by m-brooks on 2015-11-19
In the end I tried replacing the 4GB SSD with a 32GB one. However, it transpires that Asus did a sneaky with the Eee PC 901 and fitted an SSD card whose header pins are standard but the size of the card itself (and most importantly the screw holes for securing it) isn't - the new standard sized card would not fit. I tried carefully redrilling the holes but the card wouldn't work afterwards.
So instead I used the 8GB card as the primary and loaded the image onto that. It has finally successfully managed a release upgrade since then.  :)

---

