---
title: "Reinstall on box with RAID"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by jdavis on 2007-10-04
I am planning a re-install of my Ubuntu machine when Gutsy comes out and have a question.
 
I curently have the following setup: 
>  
1x80GB hard disk (SDA1 - 40 for '/' and SDA2 40 for '/home') No RAID
2x400GB drives in a RAID1 array (SDB/SDC which becomes MD0)

 
When I reinstall I will be reformatting both partitions of the first SDA disk, which is no problem to me. I realise I could do a dist-upgrade, but I have done 3 dist-upgrades on this machine and I feel like having a fresh start with gutsy.
 
What I would like to know is when I do the re-install with the alternate CD, what will happen to the MD0 raid array? Will my system detect it automatically and I just need to mount it? or will I need to re-create the array, mount and re-sync it? 
 
Obviously I am worried about losing data on these disks as around half of it is not backed up anywhere else! Any advice is much appreciated!
 
thanls, Jonathan

---

### Post by MrHippocampus on 2007-10-04
It *should* detect it automatically, if not you should be able to reassemble it without the need to recreate/resync, i think the syntax would be:

> mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdd1

edit:
You could also try this command to tell mdadm to auto-configure any raid it finds:
> mdadm --assemble --scan

---

### Post by jdavis on 2007-10-04
Sounds good! Thanks for the fast reply!

Jonathan

---

