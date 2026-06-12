---
title: "Upgrade problem with SATA/IDE mix"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by paradog on 2008-05-04
(hope this isn't a repeat; I couldn't find a thread about it).

This computer has two disks, one IDE and one SATA.  Previous versions of Ubuntu were installed on the IDE, which was identified as /dev/hda.  There was a mount point in fstab for the SATA disk (then identified as /dev/sda) at /home2; I used it for rsync backups.

After the upgrade, the IDE partition appeared to have been turned into /dev/sda1.  A "df" showed that the SATA disk wasn't mounted.  I see in a thread here that this relabelling is to be expected.

However, the weird thing is that / was hard linked to /home2!    "ls /" and "ls /home2" show the same files. "ls -i" shows that both / and /home2 point to the same inode.

I created a new mount point at /home3 for the SATA disk, but surely this behavior isn't anticipated.  And, while everything works now, I'd just as soon delete the hard link, but I'm not too familiar them and I'm wondering whether it's safe
to delete /home2 without affecting the files at /. 

FWIW, this motherboard supports hardware SATA RAID, but I've never used it and I'm not sure whether this is a factor.

---

