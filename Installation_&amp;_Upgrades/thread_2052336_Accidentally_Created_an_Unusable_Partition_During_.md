---
title: "Accidentally Created an Unusable Partition During Installation"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by 1cube1wheel on 2012-09-03
On my netbook I have Windows installed one of my hard drives.  Upon attempting to partition some of the 100GB of space on that hard drive during my Ubuntu installation, I partitioned 60GB with Windows on it, and a 40GB unusable partition.  I tried reverting to get rid of the unusable partition, but it did not work.  Is there anything I can do to get rid of that partition?  Is it at all possible to "merge" it back together with the 60GB partition, as if I had never partitioned the drive in the first place?  If not, is it possible to change the format of the 40GB partition?

---

### Post by 2F4U on 2012-09-03
I don't understand what you mean by unusable partition. Unusable for what? Did you create this partition or was it already there? As far as I know, Windows and many hardware vendors create hidden recovery partitions to avoid to have to deliver DVD's to their customers.

---

### Post by SlugSlug on 2012-09-03
install gparted and try that

---

### Post by angry_johnnie on 2012-09-03
Before you go about resizing a Windows partitin, you'll need to defragment it, and make a backup of anything important.

Boot from a ubuntu live cd.

Use gparted partition manager to delete 40 gb unused partition.

Use gparted again to resize 60 gb partition back to it's full size.

Again, remember that since you'll be mingling with your 60 gb windows partition, it would be a sensible idea to back up any important data you may have on it, just in case.  Windows may not like being resized, and after resizing it, once you boot to windows again, it may want to check the drive for errors.  Just let it do that, until it finishes.


As long as you didn't have Ubuntu on that 40 gb partition, it shouldn't be a problem.   If you did, and if it installed grub to mbr, then you'll need to re install the windows bootloader, otherwise you won't be able to boot.

How the windows bootloader is reinstalled, depends on what version of windows you have.

---

### Post by 1cube1wheel on 2012-11-29
Wow, I forgot to comment on this or mark the thread as solved, but using gparted worked just fine.  Thanks.

---

