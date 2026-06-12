---
title: "[SOLVED] dmraid recognizes two array, where one Stripe exists; Raid 0"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by AbstauBaer on 2008-02-04
Hi,
prior to anything:
```
Ubuntu - 7.10, 32bit
Mainboard: MSI K8MM3 
North: Via K8m800 
South: Via VT8237R
```

I'm about to reinstall my system; Untill now I always ignored the following Error-message and succeeded, after some problems, to set up a dual-boot system with Ubuntu and Windows XP on a RAID 0 Array:
```
ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing... 
/dev/sda: "sil" and "nvidia" formats discovered (using nvidia)! 
/dev/sda: "via" and "nvidia" formats discovered (using nvidia)! 
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing... 
/dev/sdb: "sil" and "nvidia" formats discovered (using nvidia)! 
/dev/sdb: "via" and "nvidia" formats discovered (using nvidia)! 
/dev/sda: nvidia, "nvidia_diaegcic", stripe, ok, 312581806 sectors, data@ 0 
/dev/sdb: nvidia, "nvidia_diaegcic", stripe, ok, 312581806 sectors, data@ 0
```

I guess the error occured as I got a new Maindboard. The old one carried two Raid Controlers: Nvidia and Silicon Image. The new one got a VIA Chip. The Metadata seems to be a mix of those.

Before I deleted that metadata I always used a set called nvidia_diaegcic in Ubuntu; It seems to me that dmraid used the nvidia-metadata though the Drives are connected to the VIA-Chip.

Now I've deleted the metadata by using dmraid -rE and created a new Set in the Raid-Bios, but dmraid found this:
```
root@ubuntu:~# dmraid -s 
*** Set 
name : via_dacjehfhhg 
size : 312581760 
stride : 128 
type : stripe 
status : ok 
subsets: 0 
devs : 1 
spares : 0 
*** Set 
name : via_dicaidjaib 
size : 312581760 
stride : 128 
type : stripe 
status : ok 
subsets: 0 
devs : 1 
spares : 0
```
Dmraid recognizes two stripe-arrays with the size of the real array, but when I use gparted on one of the arrays it displays 160 GB, the size of one disk.

I tested how windows copes with the new metadata: The Installation was no problem but I guess that I deleted the metadata-dumpfiles, that dmraid might have created when deleting the metadata; I didn't know that they exist at that point.

Is there a possibility to rename those sets and/or deactivate one of them or to do anything else to make this work?

Thanks alot for any Help and Ideas
Greetings Baer

---

### Post by AbstauBaer on 2008-02-04
Problem solved:

I made the Array "bootable" in Raid-BIOS and dmraid recognised it as one array with two devices :]

---

