---
title: "How to uninstall redundant ubuntu partition"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by nuke_fluke on 2008-08-25
After formatting Vista and reinstalling it I didn't know how to get the Ubuntu grub boot menu as the windows boot menu did not detect existence of ubuntu in the comp..

So I reinstalled ubuntu 8.04 from the live cd...

Now the problem is ,I got back my old ubuntu 8.04 once I booted from this new ubuntu...
I want to uninstall this new ubuntu as its unnecessary and wasting disk space and better if I can allocate this partition for my 'old' ubuntu....

Help please !!!

---

### Post by Berean on 2008-08-25
In Vista open Computer Management>Storage>Disk Management> and there you will see how your hard disk is partitioned.  Once you know which partition your unwanted Ubuntu is on it should be a case of simply deleting it.  Ensure ALL files etc are backed up before you attempt anything.  Vista will state that it didn't make the partition and therefore are you sure you want to delete it?  If you're absolutely certain that partition is the one to delete simply click yes.  As long as you don't delete a Vista partition, the worst that can happen is to reinstall Ubuntu.  Don't delete anything Vista!  Good luck and God speed.

---

### Post by gatenby_jp on 2008-08-25
Should have got yourself a super grub disk ... it is the best way to re-instate grub after running a "repair/reinstall" of windows ... it always wipes your grub loader from the mbr. Super grub will scan the computer and give you the chance to reload grub ... if Iunderstand your problem you now have two partitions with ubuntu installs ... when you delete your partition with the latest install you are still not going to be able boot into the old install ... as the grub directory that the mbr calls is going to reside in the partition you deleted ... you probably wont be able to boot either vista or ubuntu

---

### Post by coffeecat on 2008-08-25
Vista will be fine if you want to reformat the redundant Ubuntu partition to a Microsoft filesystem, but if you want a Linux filesystem, go to Synaptic and install Gparted. You can open this from System > Administration > Partition Editor. It's a nice easy-to-use partitioner that can deal with Linux and Windows filesystems.

---

