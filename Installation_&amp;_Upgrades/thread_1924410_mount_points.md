---
title: "mount points"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by ubunewtu on 2012-02-12
k im sure this has already been posted in here but my search is not giving me what i want to know.  im doing a clean install of ubuntu 11.10 im having trouble understanding the difference between the mount points and what i should use for the best results. i usually just partitioned a swap area and then used the rest of the disk space for "ext4 journaling file system" and choose the mount point to be /.  when i read posts i see that often there are three partitions used (/boot and /home) i guess my question is what do theese mount points really mean and how much space should i allocate to each one.

---

### Post by darkod on 2012-02-12
The boot folder holds the boot files, and it can be just a folder inside / or can be separate partition with mount point /boot.

Looking from inside ubuntu, the path is the same, /boot, but the difference is between a folder or separate partition.

Maybe it was useful earlier because BIOS was not able to find boot files on the back of the hdd, so you could create /boot partition on the front of the hdd and that way you are sure the files will be at front. These days separate /boot is rarely used for home system.

The same applies for /home. It can be a folder inside / or a separate partition. But having separate /home does have benefits. You can do a clean reinstall in the future, and you can use the same /home partition with the same mount point, that way all data is still there. Just make sure you don't tick the format box, and you select the same filesystem you had earlier, if it was ext4, select ext4 again, etc. Because selecting different filesystem will automatically look to reformat it, losing your data on it.

So, what I usually do for a home system, is /, /home and swap. When I do clean install I select / to be / again, formatting it, and /home to be /home again WITHOUT formatting it. All data and settings is there.
Of course, in order your Home folder to be there in your new clean install you will have to use the same username as in the old install. As long as it's the same, all is there.

---

### Post by nonkreon on 2012-03-23
if i create /usr and some other mount points as needed, can my software be still there if I install another distros? can I create a multidistro system such that a lubuntu and red hat distro share software with each other?

---

