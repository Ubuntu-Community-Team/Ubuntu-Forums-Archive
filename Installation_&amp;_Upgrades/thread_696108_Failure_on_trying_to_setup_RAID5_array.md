---
title: "Failure on trying to setup RAID5 array"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by gubemton on 2008-02-13
A slight problem.

I'm not exactly knowledgeable on all things Linux, but I'm trying to setup a fileserver with 3x500gb SATA disks in a RAID5 array.

I follow all the instructions with an install of Xubuntu, create the array with:

MDADM --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda /dev/sdb /dev/sdc

However one of the drives is DOA and gives errors after 1% of the syncing. In disgust I pull it out and send it back, but without doing anything command wise.

Now I have the problem that mdadm still thinks the drive exists, and tries to add the new drive as a spare. I do whatever I can to get rid of the old md0 and I can get it to look like its creating and syncing OK. Except...

...when the sync gets to 30% it reports a failed drive (a different drive to before), together with a click from the drive. However the drive reports no errors to testdisk and I'm not convinced there is anything actually wrong with it.

When this happens, the old failed drive data seems to reappear.

Help !!! How do I get it to forget the past and move on, and in particular how do I get the sync to retry rather than crapping out where I doubt there are any real errors.

---

