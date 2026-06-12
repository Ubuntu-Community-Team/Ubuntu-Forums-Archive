---
title: "Unable to resize NTFS partition"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by Scythe!? on 2006-07-24
Hi, I really want to install Ubuntu. I'm trying to resize my windows partition (80gb, NTFS) so Ubuntu will have 8gb to play with. I have booted off the Live CD several times and have tried to use GParted to resize it, but its not having it. Everytime it says "The device /dev/hda1 is unaccessable" or something along those lines. I have defragged many times now but its still not working, can you help?

---

### Post by gerbman on 2006-07-24
> **Scythe!? said:**
> Hi, I really want to install Ubuntu. I'm trying to resize my windows partition (80gb, NTFS) so Ubuntu will have 8gb to play with. I have booted off the Live CD several times and have tried to use GParted to resize it, but its not having it. Everytime it says "The device /dev/hda1 is unaccessable" or something along those lines. I have defragged many times now but its still not working, can you help?According to GParted, operations on NTFS filesystems are not supported. You'll need to use something like Partition Magic.

---

### Post by az on 2006-07-24
> **gerbman said:**
> According to GParted, operations on NTFS filesystems are not supported. You'll need to use something like Partition Magic.

Gparted also uses other toold like ntfstools.  Gparted on the live cd should be able to resize ntfs partitions just fine.

I do not reccommend partition magic.

---

### Post by aysiu on 2006-07-24
> **gerbman said:**
> According to GParted, operations on NTFS filesystems are not supported. You'll need to use something like Partition Magic.
Where are you getting this information? I've resized NTFS with GParted and have had no problems.

Personally, I recommend DiskDrake on PCLinuxOS, though.

---

### Post by gerbman on 2006-07-24
> **aysiu said:**
> Where are you getting this information? I've resized NTFS with GParted and have had no problems.See attached screenshot. I've never tried, but assumed based on that table that ntfs was not supported by GParted. Did I miss something?

---

### Post by gerbman on 2006-07-24
Whoops, forgot to install ntfsprogs first. The table in GParted now looks correct. Sorry about the bad information.

---

### Post by Scythe!? on 2006-07-25
I managed to get it working perfectly. The Ubuntu Live CD wouldn't resize it but the GParted Live CD did it perfectly and managed to set the partitions up simply.

---

