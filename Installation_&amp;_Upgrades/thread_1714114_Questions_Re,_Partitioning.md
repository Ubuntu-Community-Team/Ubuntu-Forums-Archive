---
title: "Questions Re, Partitioning"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by a12345 on 2011-03-24
Hi,

I was going to dual-boot Ubuntu, and I have used "Storage Management" in Windows Vista to create a spare 40GB partition, but I have a few questions.

Firstly, I didn't realise two partitions would be created - swap and the ext3 partition. These will use the free space, correct?

Secondly, on this Ubuntu help article: [https://help.ubuntu.com/8.04/switching/installing-partitioning.html#installing-partitioning-dual](https://help.ubuntu.com/8.04/switching/installing-partitioning.html#installing-partitioning-dual)

It says
> Partitioning does not occur until you finalize the installation, so  you can decide to abort the installation at the very last minute if you  require. After finalizing the installation, however, the hard disk will  be re-partitioned and all existing data stored on it will be lost. **Ensure that you have made and tested a backup copy of all important data.**

What's this about all data being lost? I thought it just changed the partition table and put Ubuntu in the new partitions (occupying the free space I created earlier)?

Confused - any assistance would be greatly appreciated. :confused:

---

### Post by Zzl1xndd on 2011-03-24
Anything on the Partition will be lost (not the whole drive) as it will reformat that section to ext3 (Unless you select the whole drive, then everything will be lost). 

Although it is still a good idea to make a back up of anything important. Normally things go smoothly but anytime you mess with partition tables there is a chance of things going wrong.

When installing you might have to select the manual partition option and select the new Partition you created, can't say for sure as I haven't done a dual boot in a while.

---

### Post by a12345 on 2011-03-24
OK, I do remember going into manual install and selecting a partition. However I freaked out so I exited the install. I shall try again. Thanks. :)

---

### Post by Zzl1xndd on 2011-03-24
> **a12345 said:**
> OK, I do remember going into manual install and selecting a partition. However I freaked out so I exited the install. I shall try again. Thanks. :)

Good luck, and like I said make sure anything important is backed up. Even the best of us make a mistake or an install goes belly up.

---

