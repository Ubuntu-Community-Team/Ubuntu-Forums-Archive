---
title: "Soft Raid possibilities"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by Saxis on 2006-06-30
I've got a Compaq EVO Business Desktop that I do some server testing with.  It has a 20GB and 40GB on ide's 1 and 2.  I have Windows Server 2003 installed on 10GB on hdd1, with a 20GB partition on hdd2 for data (mainly sql databases and such).  I've got it set up so there's exactly 9.4GB left over on each drive, and want to try a Soft Raid setup for Ubuntu.   I want something like: RAID0, 17.8 GB for /root and a RAID0, 1 GB for swap. Is this possible with different sized drives like this, where drive geometry will not match on each RAID partition? 

I attempted to do an install of this twice already, and the first time GRUB failed to install on the MBR. Then I re-partitioned to include a RAID1 100 MB /boot partition and it failed to install there also, but it did install on the MBR this time.  The install finished successfully - or so I had thought. Upon booting, the GRUB menu appeared normally, and I could boot into Server 2003 no prob, but I got an error about not being able to mount my RAID partition.

Any insight on if this should work, or not because of the drive geometry mismatch?

---

