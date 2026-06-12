---
title: "gparted doesn't work"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by jonny330 on 2008-10-13
The title says most of it really, i tried installing ubuntu but didn't get any further than the partitioning step when it said that both of my hard disks were empty (most of the room on both of them is actually taken up by vista's c drive), i've heard that this can be fixed by running a gparted live cd and using testdisk on that to write the partition table to the disk, i was just wondering, if i did this, would it wipe anything off the hard disks or would everything be ok? I want to dual boot with vista and ubuntu so i don't want to have to go about reinstalling vista.

Thanks for your patience with a linux noob.

---

### Post by imbuto on 2008-10-13
premise: I am not an expert
I have a Vista/Ubuntu dual boot. When I first tried to install Ubuntu I could not get past the partitioning step, so I:
 - rebooted on Vista
 - defragmented
 - resized the windows partition from Windows
 - rebooted with the Ubuntu installation cd and installed successfully on the just created space
If I had to do install Ubuntu again I would do it this way.

---

### Post by Mark Phelps on 2008-10-14
Lot's of people posting here don't care and would be happy to fix a hosed Vista system by removing it, but your comments don't sound like that's a result you want to have to deal with.

So, not to start a debate (again), but I strongly advise against using any Linux utility to resize your Vista partition.  While it may work, and often does, if it does NOT work, your Vista installation is hosed -- big time!

My advice is to use the Vista built-in resizer to shrink the Vista partition to make room for Ubuntu.  If it won't shrink, try turning off hibernation and removing the hibernation file.  That should free up a GIG or more of disk space.

Also, you said something about BOTH disks using your "C" partition.  Unless you're using RAID, or Dynamic Volumes, I don't see how a "C" drive can span two disks. Maybe I'm just misunderstanding what you said.

If you are using RAID or Dynamic Volumes, that's a whole lot MORE difficult to change to dual-boot Vista and Ubuntu.

---

### Post by redonwhite on 2009-01-14
Im having the same problem except im installing ubuntu on an XP drive.  Im going to try the Defragment idea and see if that helps.  My girls gonna be angry if she comes home and Grub pops up but she wont even be able to test out the ubuntu.  Shell be like what the hECK is Ubuntu and why do i have to select XP everytime now! hehe...sigh....anyways ill update this after i defrag XP drive.

---

### Post by redonwhite on 2009-01-15
update-  Defraged XP but still cant get 8.10 partioner to work.  Just says there is an error and Aborts everytime.  But when booting up computer Grub pops up.  Any ideas?

---

