---
title: "Dual Boot"
date: 2006-02-23
forum: Installation &amp; Upgrades
---

### Post by former86camaro on 2006-02-23
Currently Ubuntu is the only OS on my laptop.  A IBM Think Pad t20.  I need XP back on and need ubuntu.  Any recomendations on setting it up right from the start so dual boot works.  Thought I would ask before I had at it.  I know many are against Dual boot, but when you need Windows ya need windows and for this class I need both again.  Also I am a newb still...

Thanks....

T20
256MB RAM
25GB HD
Linksys Wireless

---

### Post by dailyplanet on 2006-02-23
Sorry, didn't mean to reply. Ignore this post.

---

### Post by former86camaro on 2006-02-24
ttt

---

### Post by soonindallas on 2006-02-24
once you have Ubunbtu installed on it's own it seems you can't install Win as the 2nd OS on that HDD and dual boot.

If you need Windows and Ubuntu together on the same drive you need to install windows (apparently you can't protect your Linux data, Windows will take the whole disk) then resize your Win partition and install Ubuntu.

---

### Post by Coelocanth on 2006-02-24
I don't know if Windows will necessarily take the whole disk, but it does want to be installed on the fisrt partition. It will not play nice if you don't do that.

---

### Post by cotcot on 2006-02-24
I would think moving the ubuntu partition to the end of the disk creating space for xp (use parted, Gparted or QTparted from a live CD); then hide the ubuntu partition (use fdisk or Ranish) ; install xp (will overwrite the MBR) and reinstall grub (see [http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652) ).

---

