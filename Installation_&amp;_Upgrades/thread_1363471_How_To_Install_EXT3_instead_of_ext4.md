---
title: "How To Install EXT3 instead of ext4"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by ossimusraadicus on 2009-12-24
Hi al!



I'm new to Linux and need to install Ubuntu Server 64-bit and 32-bit OSs with EXT3 rather than the default ext4 in a Virtualbox virtualized environment.

Can anyone help me on this?  I have been through the Ubuntu Server installer so many times to try to find an option for this and I'm pulling my hair out now.  Is the installer incapable of allowing an initial install of EXT3 rather than ext4?

I'm using Karmic Koala.

I originally posted in this topic as a reply in Beginner Talk.  However, due to an altogether too-short session timeout on this website, my original entry was not even posted.  Then, after re-typing a shortened version, I waited some hours and searched for my post again (to look for responses) using two methods:

1.  Looking around in my profile to see if maybe there was an option to view my past posts like in other forums I participate in.  If this is an option, it is not easily found on this board.

2.  Searching in both the specific forum I posted in and in the general board using keywords from my post AND heading.  

Neither of these worked.  This is frustrating.

---

### Post by Zoot7 on 2009-12-24
When the installer brings you to the partitioning section if you select "Manually Set up partitions" then you can choose the file system to be ext3.
I'd recommend creating the partitions beforehand with something like gparted, the partitioner in the installer isn't the easiest to use (unless it's changed since Hardy).

---

### Post by ossimusraadicus on 2009-12-24
Zoot7, thank you!  After some poking around I saw that option.  I'm going to look up gparted usage.

---

### Post by Zoot7 on 2009-12-25
No worries. I normally use the text based installer, I find it much easier and quicker to use tbh.

---

