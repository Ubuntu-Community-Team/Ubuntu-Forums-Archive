---
title: "How to partition second hdd for use as backup/data"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by GROwen on 2010-09-29
Hi all,

My primary drive is 250GB and has the root, home and var (I'd read it's good to put var on a separate partition for MythTV which I'm planning on doing) on separate partitions.

I have a second 1TB drive that I'll be using to backup the 250GB drive and also host less critical data.

I've created two partitions on this drive, one 250GB and the other covering the rest of the drive.

I'd like to move the Videos directory out of Home on the 250GB onto the 1TB drive but can't find a definitive way of doing this. Should I just follow this [guide]("https://help.ubuntu.com/community/Partitioning/Home/Moving")  for moving the home folder to a new partition?

Next question is when performing a backup of the 250GB drive how do I make sure it's going to the 250GB partition on the 1TB drive? Can the different partitions be mounted separately?

Thanks in advance for any help that can be offered with this.

---

### Post by madverb on 2010-09-29
Yes, each partition can be mounted seperately. Look into how to modify the fstab file.

What you will need to do is copy all the data from your videos directory to the 750GB partition. You will then need to create an fstab entry that mounts the 750GB drive (on startup) to /home/<username>/videos or whatever the directory is.

I'd also add an entry to mount the backup drive to something like /media/backup and use deja-dup, or similar, to backup to it.

Peace!

---

### Post by GROwen on 2010-09-29
Cool thanks man, much appreciated.

---

