---
title: "Not enough partitions: three already taken by Vista/Dell"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by rujith on 2008-10-25
My Dell Studio Desktop with Windows Vista comes with three primary
partitions already installed (details below).  I want to install
Ubuntu with dual-boot to Vista.  Can Ubuntu live on one extended
partition?  I was thinking of creating a fourth extended partition,
and putting two logical partitions on it, for / and swap.  But that
seems a crummy way to do it.  Can Ubuntu even boot off a logical
partition?  I'd prefer to delete some of the existing partitions, but
am not sure whether that's a good idea.  The existing partitions are:

[LIST]
[*]Partition 1   OEM       55MB	  No drive letter
[*]Partition 2   Primary   15GB    D:   Some kind of recovery utility
[*]Partition 3	Primary	  451GB	  C:   Windows Vista
[/LIST]

The first partition is something called "EISA Configuration."  I don't
think I really need it, but am not sure.  

Any advice on how to re-partition the disk would be appreciated.  I
expect to use the machine mainly for Ubuntu, so it seems a shame to
keep three partitions for Windows and cram Ubuntu into one partition.

- Rujith.

---

### Post by Mazin on 2008-10-25
From what I've seen around the forums, it seems that Ubuntu works just fine on an extended partition.  The recovery partition on your computer most likely holds the programs and data that restore your computer back to its factory state.

If you plan on mostly using Ubuntu, then you always have the option of only installing Ubuntu, and then installing Vista as a virtual system inside Ubuntu with Virtualbox.

---

### Post by bulldog on 2008-10-25
Yes,ubuntu can boot from an extended partition!
Make three logical partitions instead of two.
One 10GB for / 
One 2GB for swap
One as big as you like for /home
Now you can do a reinstall of ubuntu without loosing your data because you remount /home again but do not format this partition.
One word of advice though.
If you want to install for example 7.10 at this moment,but you decide to install 8.10 later on,and want to use the same /home,MAKE SURE TO CHOOSE A DIFFERENT LOGIN AND PASSWORD!!
Now you get a new map in your /home with different names from the old one and no mixing up will take place.
You can copy things like mozilla and thunderbird if you want offcourse.

---

