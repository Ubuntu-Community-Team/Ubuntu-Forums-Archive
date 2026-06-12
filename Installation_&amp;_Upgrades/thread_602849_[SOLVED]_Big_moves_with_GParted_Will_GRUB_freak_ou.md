---
title: "[SOLVED] Big moves with GParted: Will GRUB freak out?"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Battie on 2007-11-04
A little while ago I posted about blowing away my Windows partitions and adding the freed space to my root and home partitions.  I'm going to use the GParted boot disk as suggestion and have everything ready to go, but I'm worried about what will happen with GRUB, which is on the root partition.

This is my current layout:

/dev/sda1 (ntfs)-- Windows root
/dev/sda2 (ntfs)-- Windows docs
/dev/sda3 (extended)
/dev/sda5 (ext3) -- /home
/dev/sda6 (ext3) -- /root
/dev/sda7 (swap)

This layout looks a little stupid to me, leftover from when my newbie self was setting up the dual-booting (Windows came first, than Ubuntu).

I don't want /root, /home, ans swap to be under an extended partition (this is probably why swap doesn't even seem to work).  So, if I delete the Windows partitions, can I move /root, /home, and swap into primary partitions?

Then, so I simply edit the grub menu.lst to reflect the new location of /root?  I assume this involves changing the hd(0,5) line and the path to whatever the new location is.  Or will GRUB get lost too since it's in the /root partition?

Thanks for any help.

---

### Post by Battie on 2007-11-05
I did more research, and once I understood better what would actually happen when I did this I decided to try it.

I found and downloaded the Super Grub Disk just in case, but since my Linux partitions kept the same identifiers there was no problem.  Now Windows is gone and Ubuntu has a lot more room to stretch out.

---

