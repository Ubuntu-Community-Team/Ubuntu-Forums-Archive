---
title: "Changing installed OS from USB case  to IDE port"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by diogobaeder on 2008-03-11
Hi there, guys,

I'm trying to find a solution for putting my HD, with Ubuntu installed, from the external case to a IDE port without having to reinstall everything again.

My filesystems are now mounted this way:
/dev/sda3 => /
/dev/sda1 => /boot
/dev/sda2 => swap
/dev/sda4 => /home

And I want it to redirect these to something like this:
/dev/hda1 => /
/dev/hda1 => /boot
/dev/hda2 => swap
/dev/hda4 => /home

How can I prepare the disc to change these mounting points? What's the complete procedure to do this migration?

Thanks!

---

### Post by froy02 on 2008-03-11
I usually back up my whole drives using Acronis back up and recovery disk which comes with Seagate and Maxtor hard drives.  If I want to migrate it to a new hard drive I just restore the back up's.  Acronis makes the partitions with the same UUID's.  It would even restore both Window$ and Linux that are in same drive and they will boot normally like nothing happened.
It only takes 10 minutes to backup 18 gb and 10 minutes to restore. 
So if you have Seagate or Maxtor hard drive just download the utility from seagate website.  Still need window$ to make a bootable Cd though.  
Acronis back up and recovery is also available commercially.

---

### Post by diogobaeder on 2008-03-12
Thanks, froy!

But I'm looking for a simpler solution, since I only need to rebuild the references from mount points to devices, knowing that the filesystems types are not going to change (except for swap, they're all ext3). Also, I don't like the idea of having to count on commercial software for doing this, and I'm sure there must be a way to do this using Linux solutions.

For example, I don't know if, if I take out the HD from the case, it will keep the partition tables intact and the MBR, so that I can change the kernel path only editing the disk's attributes (maybe a UI to access the partition table, I don't know).

But thanks, anyway! :-)

Diogo

---

### Post by jken146 on 2008-03-12
Put the drive in and see what works and what doesn't.  You may have to fix some things from a live CD.

You'll most likely need to change the entries for /home ant /boot in /etc/fstab to point to the correct partition, and you may need to do the same for / in /boot/grub/menu.lst

---

### Post by diogobaeder on 2008-03-12
Thanks, jken,

That's sort of what I was looking for, and I was thinking that way. My only fear is: can I configure all these things from the own Live CD? Is this procedure made during the installation process, or is there a partitioning tool to reallocate the mounts?

Thanks!

---

