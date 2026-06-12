---
title: "Ubuntu will not load, How to reinstall."
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by jquillian on 2012-04-23
I have Ubuntu installed on one partition and windows on another.
 
Ubuntu will no longer load.
 
Is there a simple way to erase the old load and replace it with a new one?
 
I have already burned a copy of the latest 64 bit version.
 
I want to make sure I don't write on the windows partition.

---

### Post by kc1di on 2012-04-23
> **jquillian said:**
> I have Ubuntu installed on one partition and windows on another.
 
Ubuntu will no longer load.
 
Is there a simple way to erase the old load and replace it with a new one?
 
I have already burned a copy of the latest 64 bit version.
 
I want to make sure I don't write on the windows partition.

Is this a wubi install or regular install?

---

### Post by finnbob3334 on 2012-04-23
> **jquillian said:**
> I have Ubuntu installed on one partition and windows on another.
 
Ubuntu will no longer load.
 
Is there a simple way to erase the old load and replace it with a new one?
 
I have already burned a copy of the latest 64 bit version.
 
I want to make sure I don't write on the windows partition.

If the install is in two partitions, then the simplest way to replace Ubuntu is to insert your Live CD/USB and reinstall. When you get to the partitioning stage, make sure that "Format" is selected on the Ubuntu partition and that you use a decent filesystem like ext4. This will wipe the old install and install Ubuntu.

Hope this helps!

---

### Post by darkod on 2012-04-23
> **finnbob3334 said:**
> If the install is in two partitions, then the simplest way to replace Ubuntu is to insert your Live CD/USB and reinstall. When you get to the partitioning stage, make sure that "Format" is selected on the Ubuntu partition and that you use a decent filesystem like ext4. This will wipe the old install and install Ubuntu.

Hope this helps!

To add to this, to be precise.

To use existing partition you will have to use the Something Else (manual) option. Otherwise it will just install along side the existing windows and ubuntu. Ubuntu will never overwrite existing partitions unless you specifically tell it to.

When you enter the manual partitioning step, you will have to select the root partition, click the Change button below, and change the Do Not Use into ext4. Tick the format box. Select mount point /.

Be careful to select the correct partition. You can tell by the partition size and also by their filesystem. The windows partition will have ntfs, the ubuntu will have ext4.
That should be it.

---

