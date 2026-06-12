---
title: "uninstall ubuntu"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by martin622292 on 2007-10-23
how do i uninstall ubuntu?

---

### Post by solar george on 2007-10-23
Try searching the forums.

---

### Post by martin622292 on 2007-10-24
1: remove hard drive

2: take it to a computer repair store

---

### Post by g4m3b0y on 2007-10-24
well, it depends on your hard drive setup. if all you have on your hard drive is an extended partition and a swap then that's no problem. but what OS are you going to run? I wasn't too pleased with 7.10 xubuntu (bugs) so I had to revert back to 7.04 xubuntu. when running off of the live cd I had problems just re-installing because the live cd had the hard drive (on my system /dev/sda) mounted. so I here are the steps I took to reinstall that worked for me:

used gparted and unmounted the hard drive
deleted the primary partition
turned swap off in the extended / logical partition
deleted those partitions as well
format the whole drive as unformated / unspecified filesystem

then i went into the terminal and ran the following command:

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

* the output file "/dev/sda" may be different to your system but that was my hard drive in my laptop.
* the above command wipes your mbr (master boot record) clean

not a super huge linux expert like a lot of people here. i'm just a programmer. using linux as my primary OS and running M$ in virtualbox if i need to test compatibility on a project.

hope this helps you out. just wondering why you would want to get rid of ubuntu (unless you have similar reasons as to why i had to revert)? 

I'm thinking about going back to FreeBSD or swithcing to debian or gentoo so I don't have to constantly reinstall or upgrade as much as every 6 months. I'm just starting to get tired of it and I don't want to have to use an LTS version when the packages are outdated... I've been a faithful user since warty but I  just don't know anymore.

---

### Post by Sef on 2007-10-24
> how do i uninstall ubuntu?

If you want to install another os, then just format over it.

If you don't want to install another os, then use [gparted]("http://gparted.sourceforge.net") to reformat that partition.

---

