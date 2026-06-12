---
title: "Move space into extended partition from &quot;real&quot; partitions"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by fhsm on 2010-11-30
I've got a windows partition with a lot of free space followed by an extended partition. The extended partition has three sub-partitions: grub/boot&everything else, home, swap.

I'd like to take some of the free space out of the NTFS partition and move it down into the extended partition for Ubuntu to use.

I've successfully shrunken the NTFS partition. Now I've got 5gb of unallocated space between the end of NTFS an start of the extended partitions.

Now I want to extend the boot/everything else sub-partition within the extended sub-partition.

Using the gParted live CD I'm:
[LIST]
[*]Resizing the extended partition (growing it forward by 5gb)
[*]Resizing the boot/everything sub-partition forward by 5b
[/LIST]

When I try to apply the changes I get an error: *Unable to satisfy all constraints on the partition.*

Is it possible to move this space into my extended partitions so Ubuntu has more space?

---

### Post by SecretCode on 2010-11-30
Don't you have to grow the extended partition first, and only then grow the partitions inside it?
(Which I fear may mean moving all the data in all the logical partitions back by 5GB, which will take a long time.)

Can you post a gparted screenshot?

---

### Post by fhsm on 2010-11-30
I tried doing it step wise as you described. Its the extending the logical partition step that results in the error.

---

### Post by SecretCode on 2010-12-01
So were you able to grow the **extended **partition OK? Logical partitions live inside the extended partition.

> **SecretCode said:**
> Can you post a gparted screenshot?

---

### Post by fhsm on 2010-12-01
No the step when gparted tried to expand the extended partition is what caused the error.

I'm using the gparted live CD so I don't think I can do a screen shot.

---

### Post by SecretCode on 2010-12-01
Even gparted live should be able to do a screenshot. Try pressing PrtSc. If not, do you have a Ubuntu CD? Gparted is built into that, and you can do a PrtSc, and you can get online (or save it to a memory stick)

Failing all that, post the output of 
```
fdisk -lu
```
(_sudo_ fdisk -lu if running from ubuntu)

---

### Post by srs5694 on 2010-12-02
I have two suggestions:


[list]
[*]Try fiddling with partition alignment  options. These have changed a lot in recent versions of GParted, so I'm not sure exactly what the options you have might be. Try unchecking an "align to cylinders" option or changing any other alignment options you might have. (I don't recall the exact wording in all the versions.)
[*]Try resizing the extended partition, but leaving a little gap between the end of the primary partition and the beginning of the extended partition.
[/list]

---

