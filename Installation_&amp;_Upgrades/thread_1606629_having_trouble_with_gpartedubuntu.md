---
title: "having trouble with gparted/ubuntu"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by mcsinny99 on 2010-10-26
I am trying to add hard drive space to give ubuntu more room and keep hitting a brick wall.  Rather than going into to much detail I am attaching a screen shot to show where I am.  Complete noob here, so please take it easy on me, I have tried to google the issue and no dice. Also I did try the gparted live cd and couldn't get it to do it that way either.
 I am trying to allocate the unallocated space into ubuntu.  Thanks for all help!

---

### Post by faheemezani on 2010-10-26
Hi mcsinny99,

Based on the screenshot which you've attached, I believe that the 'unallocated' space of 14.39GiB resides in the primary partition. Your Linux partition (/dev/sda5), however, is in an extended partition (/dev/sda3). Unless the 'unallocated' space was part of your extended partition, expanding your Linux partition would not have been a problem. Otherwise, the only suggestion I can give is for you to:

1 - Backup your files in Linux
2 - Delete your extended partition (which will also delete your Linux partition and Linux Swap space)
3 - Shrink your Windows partition (/dev/sda2)
4 - Make the whole empty space after the Windows partition (/dev/sda2) into an extended partition
5 - Reinstall Ubuntu in the extended partition created

If reinstalling Ubuntu is not in your favour, I'm sorry but this is the only suggestion I can provide. Anyone out there with a better idea?

---

### Post by mcsinny99 on 2010-10-27
I guess that's what I'll do then, kinda sucks, but at least I haven't added a lot to it.  Thanks for the reply!

---

### Post by plucky on 2010-10-27
This is probably too late,but you do not have to delete Ubuntu as Gparted on the Live CD will allow you to move and resize your partitions.

[Gparted Tutorial](http://www.dedoimedo.com/computers/gparted.html)

You have to use the Live CD as it will not allow you to make changes to any mounted partitions.The Live CD will also mount the swap partition,so you have to turn swap off before you can change the extended partition.

To be safe,make sure you have a backup of your data,just in case anything goes wrong.

Good Luck

---

### Post by Mark Phelps on 2010-10-27
Can't open the screenshot, but if your "Windows" install is Vista or Win7, do NOT use GParted to shrink it. Doing that runs the risk of partition corruption, which will render the Vista/Win7 install unbootable.  Instead, use the Vista/Win7 Disk Management utility to do the shrinkage -- and use GParted to manipulate the OTHER partitions.

---

