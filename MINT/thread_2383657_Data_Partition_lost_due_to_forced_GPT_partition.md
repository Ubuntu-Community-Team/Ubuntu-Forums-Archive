---
title: "Data Partition lost due to forced GPT partition"
date: 2018-01-28
forum: MINT
---

### Post by jowi-krause on 2018-01-28
Hi everybody:
I work under Linux Mint (Rosa/Linux Trusty). When I tried to install REMIXOS on my multi HD system, the installation process really mixed up the hard disks. I have solved most of the problems, but a major one remains: On a "1TB" disk I had one big partition for a lot of my data. It was formatted as EXT. On this disk, the REMIX installation program seems to have changed the partition table to GPT, and inserted a new partionion for the REMIX Android at the beginning of the disk. The former data 930 GB partition with about 500 GB of data was "moved" without changing the size parameters. So now it seems out of the physical range.
I have been trying all sorts of resources, but I'm not getting anywhere. Finally all I can use with some level of experience is TESTDISK. SFAT, gpart, gparted seem to have no help available.
What can I do to retrieve my data?
PS: I do not have another 1GB disk to spare to which I could copy an image of the disk. So unfortunately I will have to do everything on the live disk. But It is a pure data storage disk, no OS activity, no writing going on.
Thanks for any help anybody can give me, in English or German.

---

### Post by howefield on 2018-01-28
Thread moved to the "*MINT*" forum.

---

### Post by oldfred on 2018-01-28
Not sure what your installer did.
Is data readable, some systems (Windows) have added partition at beginning of a drive and wiped partition table (effectively destroying everything).
And some users have used a drive as the ISO installer. And that often uses dd to create hybrid structure at beginning of drive, also effectively destroying data.
In those cases the only way to recover some data is with software like photorec. 

Post this:
sudo gdisk -l /dev/sdb  (or whatever drive is).

If drive was not gpt, then the old MBR only has partition table at beginning of drive. The newer gpt has a backup partition table at end of drive.

Parted rescue or testdisk may recover missing partitions, but if critical struction overwritten, it may not recover everything.

---

