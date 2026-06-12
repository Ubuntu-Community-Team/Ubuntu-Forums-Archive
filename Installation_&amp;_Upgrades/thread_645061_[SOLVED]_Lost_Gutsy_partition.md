---
title: "[SOLVED] Lost Gutsy partition"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by cadlewv on 2007-12-19
After many problems (including the need to reload my XP partition), my system is now completely good (and backed up).  The only problem is, after all that I've had to do, the partition with Gutsy on it is not bootable anymore.  It's still sitting there beside my XP partition (C:).  

What I need to know is how to recover it somehow and make it part of a dual-boot system with XP Pro.  I have Acronis Disk Director and have pasted a screen shot of the disk structure.  Obviously the Ext 2 partition is the Gutsy one, with the one in between being a swap file for Gutsy.

Please help with any instructions you may have.

Thanks.

---

### Post by Pumalite on 2007-12-19
If you have installed Ubuntu, reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by cadlewv on 2007-12-19
One question first:  I think the space that Gutsy is on isn't an active partition, yet I don't think it's unallocated space either.

Any thoughts?

---

### Post by Pumalite on 2007-12-19
If you installed Gutsy on it, it cannot be unallocated. Reinstall Grub.

---

### Post by cadlewv on 2007-12-19
Ok, one more silly question:  When I install Grub, I -will- have a dual boot system with XP and Gutsy, correct?

I'm very new and green here, but have made the commitment to learn to use Linux and migrate to it completely in the next several months.  I just need to learn how to do all of the things that I am able to do in Windows.

Thank you!

p.s. nice signature.  got a chuckle out of it.

---

### Post by Pumalite on 2007-12-19
You'll have dual boot. I'll be here to help you if you have any problem.

---

### Post by cadlewv on 2007-12-19
All went well with the Grub installation, but I got the following error when trying to boot into Ubuntu:

Error 17:  Cannot mount selected partition

It may help to understand that the partition Gutsy is on doesn't have a label or drive letter assigned to it, well, until I just did both via Acronis Disk Director.

Thoughts?

---

### Post by Pumalite on 2007-12-19
Try switching the boot order in your hard drives

---

### Post by cadlewv on 2007-12-19
See my last post as well.  It's been edited.

My greenness will probably start to be annoying, but how would I switch the boot order?  Also, I -was- going to ask how to set XP as the default (1st in line) in the boot order anyway.

---

### Post by Pumalite on 2007-12-19
Get Gparted Live CD. Make a partition of that unallocated space. Format ext3. Install Gutsy to that partition.

---

### Post by cadlewv on 2007-12-19
Would there be an issue with me using Acronis' Disk Director for the task?  And, have we come to the conclusion that it -is- unallocated space?

---

### Post by Pumalite on 2007-12-19
Acronis and Ubuntu don't mix very well. Use Gparted Live CD.

---

### Post by cadlewv on 2007-12-19
Ok.  One last question for now:

On the prepare partitions screen during the install of Gutsy, the device that I needed to install onto is /dev/hda3, ext3, with the mount point of /media/hd3.  I remember when I clicked forward, it kept giving me this error code that 'No root file system is defined.  Please correct this from the partitioning menu'.

What mount point should I use in the drop-down list for 'mount point'?  It's automatically populated with /media/hda3.  Or was there some other setting that I needed to be changing?

---

### Post by Pumalite on 2007-12-19
How many GB do you have in that partition?

---

### Post by cadlewv on 2007-12-19
I set aside 10GB, with a 512MB swap after my primary (XP) partition.

---

### Post by Pumalite on 2007-12-19
During the installation go Manual and follow this scheme:
5 GB for '/'
5 GB for /home

---

### Post by cadlewv on 2007-12-19
Just to make sure... again, I'm very green.

On the prepare partitions install screen I see the following:

/dev/hda
   /dev/hda1   ntfs   /media/hda1
   /dev/hda2   swap
   /dev/hda3   ext3  /dev/hda3
/dev/hdb
   /dev/hdb1   ntfs   /media/hdb1
   /dev/hdb5   fat32  /media/hdb5

So, I edit the '/dev/hda3   ext3  /dev/hda3 <-mount point line [B]twice[B], each time changing the mount point (once to '/' and once to '/home' and changing the size to 5GB?

And is the mount point listed on the main partitions screen of '/dev/hda3' correct?

---

### Post by Pumalite on 2007-12-19
You are basically dividing your hda3 in two. To one half you give mount point /: to the other half, mount point /home. Then press 'Follow'. Install Grub to MBR (this is done by default). Good luck. 10.4

---

### Post by cadlewv on 2007-12-19
So, I'll be editing this line by going into it twice, correct?:  /dev/hda3 ext3 /dev/hda3 (and /dev/hda3 is correct?  initially it said '/media/hd3').

---

