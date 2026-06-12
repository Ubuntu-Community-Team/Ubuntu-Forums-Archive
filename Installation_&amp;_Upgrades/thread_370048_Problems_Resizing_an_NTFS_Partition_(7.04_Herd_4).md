---
title: "Problems Resizing an NTFS Partition (7.04 Herd 4)"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by afreshtwig on 2007-02-25
I am trying to install Feisty Fawn for testing purposes, but when I get to repartitioning the drive, I always get an error about how the partitioner could not resize my NTFS partition (which is about 74GB, 23 of which are free). I've tried using other partitioners as well, but everything tells me it can't resize it. I attempted to run error checking on the drive, but Windows never seems to want to schedule the error checking on restart.

Anyone know what's wrong?

---

### Post by afreshtwig on 2007-02-25
Bump. Can anyone help me?

---

### Post by eapache on 2007-02-25
get into a windows cmd line and type

chkdsk c:

(assuming c: is your system partition). This will run a windows disk verification within Windows itself, without the need to restart. If that turns up errors, run the same command with the /f option to have it fix them automatically.

The /f option may break something if it detects a windows corrupt system file and overwrites it, but just the chkdsk with no options shouldn't hurt anything.

---

### Post by afreshtwig on 2007-02-26
> **eapache said:**
> get into a windows cmd line and type

chkdsk c:

(assuming c: is your system partition). This will run a windows disk verification within Windows itself, without the need to restart. If that turns up errors, run the same command with the /f option to have it fix them automatically.

The /f option may break something if it detects a windows corrupt system file and overwrites it, but just the chkdsk with no options shouldn't hurt anything.

This still gave me the requirement to restart, but this time it actually went through with the chkdsk on restart. 

A couple hours later and now I'm posting from Ubuntu Feisty Fawn! Thanks a ton.

---

