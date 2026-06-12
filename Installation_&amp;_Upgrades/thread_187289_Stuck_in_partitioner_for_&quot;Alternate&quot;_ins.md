---
title: "Stuck in partitioner for &quot;Alternate&quot; installation"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by flabbah on 2006-06-02
Hello:

I am trying to fresh-install Dapper (with the alternate installer) on a box that previously had Breezy with LVM.

After hardware detection, I wind up at the menu asking if I want to manually edit the partition table. I say yes, and wind up in the partitioner.

So far, so good. Next:

I create a primary partition (w/bootable flag) for the LVM physical volume.

I set up my volume groups:
vg01

I set up 3 logical volumes for vg01
boot
root
swap

I specify the partitions on the logical volumes (vg, lv lv name, mount point, filesystem type):

vg01, boot, /boot, ext2
vg01, root, /, xfs
vg01, swap, ,swap

(formatting is set where applicable)

Now at this point, everything looks good.

However, I get stuck in a infinite loop where the only options (from the root level of the partitioner) are

Undo Changes to Partition
Finish partitioning and write changes to disk

<Go Back>

If I say "Finish Partitioning" , absolutely nothing happens, and I am at the root level of the partitioner still.

If I say "Go Back", I wind up at the Ubuntu Installer Main Menu. From there, no matter what I select, I always get taken to the partitioner again.

Anybody have any ideas?

---

### Post by Lux Perpetua on 2006-06-04
Sorry, /boot cannot be on a logical volume. It must be on a genuine disk partition. I'm not sure that was the only problem, but that's the most obvious thing that I see.

---

### Post by flabbah on 2006-06-05
[QUOTE=Lux Perpetua]Sorry, /boot cannot be on a logical volume. It must be on a genuine disk partition. I'm not sure that was the only problem, but that's the most obvious thing that I see.[/QUOTE]

Thanks very much ... I made /boot an ext2 bootable primary partition outside of lvm. The partitioner allowed me to make my physical lvm partition bootable ... and allowed me to create a lv which mounted /boot ... I guess I was led astray.

Again,
Thanks

-Alex

---

