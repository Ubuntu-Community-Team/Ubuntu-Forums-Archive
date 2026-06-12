---
title: "Strange partitioning question"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by Jax Kovak on 2006-07-12
On my system I have 3 hard disks:

HD1 (hde): C: = Windows 2000 plus D, E, F that contain data
HD2 (hdf): G: = Windows XP plus ( H: ) hdf2 which is Ubuntu
HD3 is just a data drive.

Everything boots from the boot.ini file on C: (win2K) and everything is working at the moment, however, I have come to a point where I no longer really need Windows XP on the system at all (Phew!) and I would like Ubuntu to have the whole of HD2 to itself.

Questions:
1)
Is it possible to expand Ubuntu so that it 'grows' and takes over the whole drive *without* a re-install?

2) If 1) is not possible, can I format the WinXP drive so that it becomes part of Ubuntu (Like a second storage partition), and if so how would I make any use of it?
For example could I move my /home folder onto this new partition and thus free up some space on the main partition?

Please remember that I am *very* new to Ubuntu (About 4 days old!), and this is my first post out of the 'Absolute Beginner Talk' forum! I really do need things to be kept as simple as possible.

Thanks

Jax

---

### Post by OpsVentus on 2006-07-12
You can use GParted to join the 2 partitions, but it's not very safe.
The easyest and safest way, IMO, is to boot from a live cd.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) < special live cd to do stuff to partitions and only 30 MB to download.

Then you can format the first partition of the second drive(the XP one) to ext3. Then copy all the data from your Ubuntu partition to the new ext3 partition, then test if it will boot from it(remember to ajust your boot loader), if so, expand the partition to the entire disk.

GParted have documentation on there site on how to work with there live cd.

Clear?

---

### Post by Jax Kovak on 2006-07-12
Excellent! Ill give that a go as soon as I get home. Thanks very much.

Jax

---

