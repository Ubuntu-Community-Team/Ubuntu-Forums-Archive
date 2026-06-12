---
title: "Issues Installing to a Flash Drive"
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by willrayjohnson on 2016-10-22
So I was trying to install from a bootable flash drive to another flash drive. I set up the partion table and got the installation going. It started looping some error (I cannot remember what it was), so I foolishly thought I should shutdown the computer and try again. I shutdown, but the shutdown was hanging, so I made another mistake and did a hard shutdown.

Now the flash drive I was trying to install to is getting an input/output in gparted. I've tried to format it in disk utilities, but that doesn't seem to work either. 

Is there anything I can do, or is this drive lost?

---

### Post by oldfred on 2016-10-22
Does system see drive?
If install format should be ext4, unless you changed to some other.
You may need to run fsck on all ext4 partitions. Abnormal shutdown, whether power failure or forced by user often needs fsck. (Windows requires chkdsk).

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

