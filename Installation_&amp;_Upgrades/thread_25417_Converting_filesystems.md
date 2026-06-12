---
title: "Converting filesystems?"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by Ubunted on 2005-04-10
I'm wondering if it is possible to convert the default file system on all partitions (there's no dual-boot here, it's all Ubuntu) into reiserfs without a reinstall - as one would do in Windows converting from FAT32 to NTFS? I'm trying to eke out as much performance out of my trusty old laptop as I can.

EDIT: Whoops,thought I was in the main App Support forum when I made this. My bad!

---

### Post by maqi on 2005-04-10
From what I understand (not much), it's a fairly simple thing to convert from et2 to ext3 without needing to reinstall. However, I do not think the same is true of a conversion from ext3 to reiserfs. ext2 & ext3 are essentially the same but ext3 includes journalling so the change essentially just adds the journalling function to ext2.

reiserfs is a totally different filesystem and therefore requires reformatting of the drive - and reformatting will trash your data. I suspect you would have to do some serious partition juggling if you want to do this  without losing your current set up.

cheers,
maqi

P.S. In addition - unless you are comfortable with editing /etc/fstab and /boot/grub/menu.list or your lilo configuration you would probably end up doing a reinstall anyway.

But theoretically you could:

Copy your existing partitions to new partitions then edit fstab and your bootloader configuration so that you boot from the new partitions. You could then use gparted to format the old partitions as reiserfs and copy your partitions back to their original positions and delete the partitions you made to copy your original partitions. 

However, unlike Windows, there is no linux utility of which I am aware which will allow you to modify partitions on a mounted device - so if you stuff it up you won't know until you try and reboot - which could be tragic. And you may need to do all this partition juggling from a command line or from the partitioning tool included with the install disc.

So it's not impossible, but is the performance gain (cue the ext3 vs reiserfs flame war :twisted: ) worth the time, effort and risk?

---

### Post by Ubunted on 2005-04-10
Bah, I don't have anything even mildly important other than my Firefox profile stored on this thing. I'll just do a clean reinstall.

Now is there a specific command I need to enter at some point to be able to use reiser? I don't remember it from the partition editor last time.

---

### Post by Ubunted on 2005-04-10
Anyone? Gimme some reiser lovin! :grin:

---

### Post by maqi on 2005-04-13
To select reiser I think you will have to do manual or expert partitioning I think. I never use the auto and I'm not sure if the guided partitioning lets you choose the file system. But since you're in your current situation it sound like you can play with it until you get what you want - you won't be doing anything that a reformat & repartitio won't fix :D

Traditionally in *nix systems quite a few directories are mounted on their own partitions. For home use this probably isn't necessary unless you're planning to run a server. So for a desktop install - keeping the options basic - you can create just 2 partitions, eg:

/dev/hda1  with a mount point of / (ie, root file system - this will contain your whole operating system and could take up almost all of the disk); and

/dev/hda3 with a mount point of swap (not that big)

This (or something like it) is the default if you let the installer do it on auto I think. 

Better is to manually create one more partition with the mount point /home. This way if you bork you system you don't lose your data, eg, documents, email, music, etc, and you can reinstall the OS on the / partition.

When you're in the partitioning part of the install, if you do the partitioning manually you can do this and choose partition sizes and file systems by highlighting the partition and hitting <Enter> - if I recall correctly. A list of possible mount points & file systems will come up - choose reiserfs - yay. 

Of course I don't actually know how much room you have - but keeping /home separate is a good idea - devote most space to this as you will end up downloading, saving, etc most stuff here. This is the one that will accumulate the most data over time.

Oh, and once you're into the partitioning bit of the install there is some help info available.

Hope this helps :)
maqi

---

### Post by haiku72 on 2005-06-21
Well I'm a newbie but I had to move from Reiserfs to ext3 for some reason and was looking for the same thing.  There is a nice command for it: convertfs

[http://members.optusnet.com.au/clausen/ideas/convertfs.txt](http://members.optusnet.com.au/clausen/ideas/convertfs.txt)

You can install it through synaptic if you use the universe repositories and it allows you to change between various filesystems.

If you have the liveCD you could run it from there.

It worked mostly but gave some trouble on one partition so eventually I just moved all data of that partition to another partition, formatted it with the right fs and moved the data back in place.

---

