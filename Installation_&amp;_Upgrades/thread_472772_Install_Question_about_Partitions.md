---
title: "Install Question about Partitions"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by DirtDawg on 2007-06-13
I have Ubuntu Dapper installed on a 40Gig hard drive with a "/storage" partition of about 20Gigs that I used to use for file sharing between Windows and Dapper. Since, I have gotten an external HD of 250Gigs, so I no longer need the wee /storage partition.

SO I want to use the free space to install other distros. The plan is to erase the /storage partition and install new distros that share the the /home and /swap partitions.

My question is, if I erase the /storage partition, will it confuse my Dapper install? Do I need to unmount the /storage partition before I start, removing it from fstab, etc? Is there any danger that reformatting the /storage partition will corrupt other information on the hard drive?

Thank you.

---

### Post by sriram on 2007-06-13
hi,
i tried installing suse along with ubuntu it had no problems at all as i had grub select the choice and the home directory could me mounted in both of them ..
no confusion..

---

### Post by DirtDawg on 2007-06-13
> **sriram said:**
> hi,
i tried installing suse along with ubuntu it had no problems at all as i had grub select the choice and the home directory could me mounted in both of them ..
no confusion..

Thank you for responding. 

However, I am still unsure about deleting a partition that already exists and mounted by my current Dapper install (the /storage partition). Maybe I don't need to do anything or maybe I just need to remove it from fstab before deleting it? 

Thanks again.

---

### Post by DirtDawg on 2007-06-13
Okay found the answer. It is required to delete the relevant line from /etc/fstab.

The End

---

