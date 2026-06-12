---
title: "HELP! Ext3 partition refuses to mount during fresh install."
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by el_escorpion on 2007-05-08
Quick rundown of situation.
i have a shared partition between windows and Ubuntu. It's Ext3.
A little while back during unmount it unmounted and refused to mount back.
Had to run fsck on it. Fixed a lot of errors. But refused to mount still.
I thought it might have been something in ubuntu i broke (i tweaked with it a lot)
Right now installing 7.04 (fresh install)
Do manual partition. Select all the mount point for all the partitions.
Go to install and get an error:

> "The attempt to mount a file system with type ext3 in IDE1 master, partition #2 (hda2) at /shared failed.
You may resume partitioning from the partitioning menu."

When i ran fsck on it again it comes clean. 
> ubuntu@ubuntu:~$ sudo fsck /dev/hda2
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/hda2: clean, 9069/7684096 files, 13685988/15360148 blocks (check in 4 mounts)


Honestly got no idea what to do. :confused: 
Formatting the partition is out of the question too much stuff on it to back up due to lack of sufficient storage space.
And using windows for the next while doesn't seem like a fun prospect.

---

### Post by hal8000 on 2007-05-08
Can you post your /etc/fstab, it may be a bad option in the filesystem table.

Have you tried mounting the partion manually from a terminal as su?
e.g. sudo mkdir /root/tmp

sudo mount /dev/hda2 -t ext3 /root/tmp

this may reveal some more detail, then check system messages:

tail /var/log/messages

---

