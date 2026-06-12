---
title: "Installing Windows XP to Separate Hard Drive."
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by dougr on 2005-10-06
I have a box that I recently built, and installed Hoary as the primary OS.  I have been running Ubuntu as my only OS for about 2 years(other nix distro's longer).    I would like to add an XP install so that I can do a little bit of gaming, and would like to just add another hard drive to this system, and install XP.  I would like it to then be a dual boot system.  I know that installing XP first, then linux is pretty straightforward.  But from what I know installing windows after having linux installed is another matter entirely.  When I search for dual booting 2 drives I always find people wanting to "dabble" in linux, and not linux people wanting to dabble in windows.  If anyone knows how to do this, I would appreciate it.

---

### Post by aysiu on 2005-10-06
Well, as far as I know, the only difficulty with install XP second is it messing up the MBR. So I would install it, and then follow [these instructions for restoring Grub to the MBR](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub%20restore)

---

### Post by Zelut on 2005-10-06
Well if you can use a partition manager and create a partition for windows (FAT32) then you can install XP and tell it to look at that partition and you should be fine.  Making sure you use FAT32 will allow you read/write access from ubuntu to the partition (unlike NTFS).  Also, I don't remember if grub will auto-sense the second OS but grub is easy enough to edit.

Anyone else have any other suggestions?

---

### Post by efpc2003 on 2005-10-06
[QUOTE=dougr]I have a box that I recently built, and installed Hoary as the primary OS.  I have been running Ubuntu as my only OS for about 2 years(other nix distro's longer).    I would like to add an XP install so that I can do a little bit of gaming, and would like to just add another hard drive to this system, and install XP.  I would like it to then be a dual boot system.  I know that installing XP first, then linux is pretty straightforward.  But from what I know installing windows after having linux installed is another matter entirely.  When I search for dual booting 2 drives I always find people wanting to "dabble" in linux, and not linux people wanting to dabble in windows.  If anyone knows how to do this, I would appreciate it.[/QUOTE]
I don't speak english, I hope you understandme.
I've got 2 disks too....
Before (a few weeks)....I had just 1 hard disk with windows.
I diconnect windows's hard disc. 
Then I added a new hard disk at primary controller master and install hoary...
After that I put the windows disk into/at secondary controller master.
All hard disks master.
And edit grub and add it lines:
title windows xp 98 95 me
rootnoverify (hd1,0)
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
boot

---

