---
title: "Raid array not available after upgrade"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by tim_m on 2010-07-11
After upgrading my ubuntu install my raid array is gone. The drives appear in blkid as "Linux raid member" and both have the same uuid. If I try to mount the drive via fstab I get a message that the drive is not ready or present. If I try to mount each of the two drives, one mounts successfully the other reports serious errors. Issuing a cat /proc/mdstat shows md_d0 as inactive.

How can I re-establish my raid array? I have the data backed up so if I have to wipe out the disks to start over that's an option.

---

### Post by cbowman57 on 2010-07-11
I have only experimented with RAID under Ubuntu and derivatives but I'd try upgrading with the alternate install disk if you haven't already.

The graphical install doesn't support RAID out of the box.

---

### Post by tootlet on 2010-08-24
Greetings,
I have a similar problems to Tim_M. I have a master hard drive that currently runs openSUSE 11.2 with 3 additional hard drives in RAID5. I would like to switch to Xubuntu 10.4 but all the tutorials I've read make you reformat the hard drives. openSUSE will let you upgrade from one to another but I've been having more problems with it and want to move to Xubuntu. Anyone know how to perserve the md0 RAID5 and data on the openSUSE install and get Xubuntu to see it?

Thanks,
Tom

---

