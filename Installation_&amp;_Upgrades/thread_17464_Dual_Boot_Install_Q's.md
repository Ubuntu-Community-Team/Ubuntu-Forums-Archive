---
title: "Dual Boot Install Q's"
date: 2005-02-28
forum: Installation &amp; Upgrades
---

### Post by ytseshred on 2005-02-28
Okay, I've read helpful information bits and pieces around the forums, so I'm just going to spell out my questions here, and see if anyone can tackle them all at once:


MY GOAL:  Have a dual boot Windows XP & Ubuntu machine, using only 1 hard drive, and preferably w/ XP under FAT32 (if possible), so that the OS's can read (and write?  maybe not bi-directional..) each other's data.

I was previously starting off by booting off ubuntu, and writing the partitions with that.  Let me know if I should do something else, or if it is sufficient.

My harddrive is 102 GB, I'd like the windows to have 76GB, and ubunto to have 20gb, w/ 6gb of swap.

1) Describe how I should partition the drive, including the general paradigm for linux partition (swap, /, and /home? or swap, /, and /usr? or just swap, /?):
  Provide the following information for each partition:  mount location, filesystem, bootable flag, formatting options, mount options (if any)

2) Previously when I wrote the partition table, Ubuntu would start installing the base filesystem.  I believe the general consensus is to stop here, and install Windows first.  How do I make it only write the partitions and not install Ubuntu?   I think i read Ctrl+Alt+F1 somewhere?

3) If installing windows xp under FAT32 is possible, what do I need to do to get around the "NTLDR missing" problem after the initial restart?

4) After windows is installed, how do I install Ubuntu w/o having the partitions destroyed?  I believe it says it has to write the partitions before it installs.  If no changes were made, will it still "write" them without deleting what was on there?  

If anyone can tackle these questions, I'd appreciate it, thanks.

---

### Post by Bondings on 2005-02-28
[QUOTE=ytseshred]Okay, I've read helpful information bits and pieces around the forums, so I'm just going to spell out my questions here, and see if anyone can tackle them all at once:


MY GOAL:  Have a dual boot Windows XP & Ubuntu machine, using only 1 hard drive, and preferably w/ XP under FAT32 (if possible), so that the OS's can read (and write?  maybe not bi-directional..) each other's data.

I was previously starting off by booting off ubuntu, and writing the partitions with that.  Let me know if I should do something else, or if it is sufficient.

My harddrive is 102 GB, I'd like the windows to have 76GB, and ubunto to have 20gb, w/ 6gb of swap.

1) Describe how I should partition the drive, including the general paradigm for linux partition (swap, /, and /home? or swap, /, and /usr? or just swap, /?):
  Provide the following information for each partition:  mount location, filesystem, bootable flag, formatting options, mount options (if any)

2) Previously when I wrote the partition table, Ubuntu would start installing the base filesystem.  I believe the general consensus is to stop here, and install Windows first.  How do I make it only write the partitions and not install Ubuntu?   I think i read Ctrl+Alt+F1 somewhere?

3) If installing windows xp under FAT32 is possible, what do I need to do to get around the "NTLDR missing" problem after the initial restart?

4) After windows is installed, how do I install Ubuntu w/o having the partitions destroyed?  I believe it says it has to write the partitions before it installs.  If no changes were made, will it still "write" them without deleting what was on there?  

If anyone can tackle these questions, I'd appreciate it, thanks.[/QUOTE]

Don't partition your hard disk with Ubuntu. I think that's why my computer doens't want to boot xp.

---

### Post by Domhnull on 2005-02-28
I'm running a dual-boot XP / Ubuntu machine.  I started from scratch and reformatted my hard-drive (after backing up my XP files).  Then I installed XP but only gave it half the drive (using FAT32).  I didn't worry about the other half.  When I installed linux I let it partition the remaining empty space.  Seems to have worked just fine.

---

