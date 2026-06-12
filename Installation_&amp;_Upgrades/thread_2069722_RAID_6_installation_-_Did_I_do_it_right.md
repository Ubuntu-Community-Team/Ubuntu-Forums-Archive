---
title: "RAID 6 installation - Did I do it right?"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by coolnicklas on 2012-10-11
Before my installation of 12.04 server I read a lot on the forum about raid install and problems with Grub not being able to boot from anything other than a raid 1 array. However I had no problem at all with installation on a raid 6 array (5 disks) using mdadm.

What I did using Alternate 12.04 CD:

1. Choose Manual partion
2. Wipe all 5 drives
3. Assign all drives to a Raid 6 array
4. Create a LVM volume group and assign the the raid 6 array to this group
5. Create the three volumes; boot, swap and /
6. installed Grub (Grub2)

It boots up without any problems. It seems to good to be true, did I forgot anything?

---

### Post by darkod on 2012-10-11
No, it seems right.

Most raid problems with grub are affecting fakeraid it seems, not software raid (mdadm). On top of that, since the live cd can see the fakeraid, people keep using it to install despite the recommendation to use the alternate cd for raid.

The alternate installs grub on fakeraid almost always without problems, but the live cd fails to do this.

---

### Post by coolnicklas on 2012-10-11
Thanks!

I'll have another go tonight with a 12.04 installation on a raid 1 + raid 5 combo on another HP n36L.

---

