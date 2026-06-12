---
title: "Replacing SuSE with Ubuntu server + keeping existing LVM"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by sylaan on 2008-04-25
Hello all, 

I am running my home fileserver on OpenSuse 10.3, I am using it mainly for media storage (movies, music, images, files, etc). I currently have a 520GB LVM volume spread on 3 physical disks. One of those disks has also the /, swap and home partition. 

Specifically, OpenSuse takes sdc1 (swap), sdc2 (/) and sdc3 (home). The LVM volume uses the rest of sdc - sdc4 - then also sda1 (full disk) and sdb1 (full disk). 

My intention is to install Ubuntu 8.04 server edition on the existing sdc drive, without re-partitioning. I don't want to lose the LVM. I am hoping that I will be able to keep the partition structure and I am also hoping that I will be able to safely import my existing LVM. 

Is that possible ? How exactly I import my LVM, or make Ubuntu recognize the existing volume ? Will it do it by default ?

Any pointers or info will be much appreciated :)

Thanks,
Sylaan

---

### Post by sylaan on 2008-04-26
Anyone ? :-)

---

### Post by sylaan on 2008-04-26
Nevermind, it seems it imported the existing volume just fine.

---

