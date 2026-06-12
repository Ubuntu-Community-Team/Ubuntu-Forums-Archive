---
title: "Help needed with LVM on Edgy (server/LAMP)"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by foxmulder on 2006-11-07
Ok I need help setting up my server using Edgy Server edition using LVM.

I have 3 harddisk that I want to use with LVM (160gb, 40gb and 60gb).

I am in the partition screen: 

How do I take if from there?

There is no how-to whatsoever that is specific for Edgy Edge server and using LVM??? ](*,)

---

### Post by foxmulder on 2006-11-08
Anyone? How do I use the install to make everything work with LVM please?

---

### Post by foxmulder on 2006-11-09
Really is the *no one*  that even uses LVM with Edgy?

Why is support for LVM so terrible bad?

I guess Ubuntu is really the "Kiddy Linux" then....

(it will work but don't demand any difficult stuff)

---

### Post by hvc123 on 2006-11-10
use vgccreate matey

---

### Post by foxmulder on 2006-11-10
> **hvc123 said:**
> use vgccreate matey

Listen: that option does not exist in the partion method of the installation menu so that doesn't help at all...

---

### Post by foxmulder on 2006-11-11
GUYS it there NO one at all that knows HOW to set up LVM with my 3 disks using the installer during a clean install?

---

### Post by Lenn on 2006-11-15
Somethimg like this.

Partition your drives/partitions as physical lvm volumes. (That's the partition TYPE)
Save the partition tables.
Configure Lvm.
make an VolumeGroup.
Add the physical volumes to your VolumeGroup
Make Logical Volumes in the VolumeGroup.
Save your LVM config. (back to your partition screen).
select your Logical volumes and give them an mount point and filesystemType

that's it.

PS: If this doesn't work with multible disks then make an volumegroup on the first disk and after the install you can add the other 2 disks to your volumeGroup. see the LVM howto.

succes&#729;

---

### Post by cdeszaq on 2006-12-02
From what I have read elswhere, LVM is not "nativly" supported in Edgy. You must get the correct packages(can't remember which right now, sorry) and set up LVM post-install. It will work, but it is not included in the CD's.

Cdeszaq

---

