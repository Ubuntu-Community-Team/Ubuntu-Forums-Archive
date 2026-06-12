---
title: "Installer cant find partitions and XP-installation"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by sepplo on 2010-03-15
Hey there

I am trying to install ubuntu on my notebook but i am encountering a problem!

The instaler doesnt find my partitions and the XP that is installed too! For some reasons i cannot delete the whole hdd... if i format the partition, where (i want to install ubuntu) with fat, the pc crashes during the installing process after the tastaturlayout question! if i try some other formats, the installer tells me, that there are no Operating Systems installed and the hdd is unpartitioned!

if i start ubuntu live from the cd, the system finds all partitions, but if i run cfdisk in a terminal, i get a fatal error (cannot open disk space)...

My machine is a acer aspire 1694 WLMi (pretty old, but should be no problem), bios is up to date, Windows is XP home edition with SP3.

Thanks!
greetings from madrid
Michi

---

### Post by Mark Phelps on 2010-03-15
I didn't catch which version of Ubuntu you're trying to install, but for partitioning, the GParted LiveCD generally has newer and more up to date versions than the Ubuntu installer.

You can get that LiveCD by going to distrowatch.com, downloading the ISO image, and burning it to CD.

Once you boot from that CD, if it sees the partitions, you can either wipe them (if you want to use the whole drive), or shrink the XP partition to make room for Ubuntu.

---

### Post by leorolla on 2010-03-15
What do you see when you run
```
sudo fdisk -l
```
from the LiveCD ?

GParted is a good idea. Anyway it is recommended that you boot XP and run a defrag first.

---

### Post by sepplo on 2010-03-16
cant try sudo fdisk -1 right now! (will try later)


but tried the gparted and it also just told me that there is one disk, totally empty and no partitions...

i will defragment the other partitions right now and see, if that makes any change!

thanks for your responds!


edit: the version i am trying to instal is 9.10!

---

### Post by leorolla on 2010-03-16
Don't!

Unless you don't care about what is in the HD now.

There are problems with the partition and it's possible to fix them, but not with GParted.

---

### Post by dE_logics on 2010-03-16
Download [this](http://www.cgsecurity.org/wiki/TestDisk_Download) utility called testdisk.

Extract all it's contents and open terminal in that location (just CD to that location).

Then ```
cd linux
``` and then > ./testdisk_static

Select no log in the menu that opens.

Select the HDD that's giving the problem.

Select Intel

Then analyse

Then search for partitions.

Then press enter (After analysis). In the next menu select Write.

Then quit...that's about it.


The usual warnings exist...backup all your data, although data loss is unlikely.

---

### Post by sepplo on 2010-03-16
hey!

i found a phantom entry in the partition table, that was the problem! with testdisk i could erase it after a while! thank you very much! now everything works fine!

buy and thanks again!

---

