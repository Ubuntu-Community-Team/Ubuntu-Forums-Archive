---
title: "reinstalling and using manual partitions"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by Jguy on 2009-12-11
Hi, 

I am currently in the process of reinstalling Ubuntu 9.04 x64 and wanted to split my /home directory off of my / partition before the OS installs and I have to go through the trouble of doing it manually. I just want to make sure that my partitions will work when the system comes online, and if I'm forgetting anything.

Here are my disks:

/dev/sda - 150GB
/dev/sdb - 500GB
/dev/sdc - 164.6GB (my old 9.10 install reported this disk as having many bad sectors)
/dev/sdd - 500GB
/dev/sde - 640GB (currently an external hard drive, don't want to install here. XD)

And I have the following going in the partition editor of the Ubuntu installer:

/ as ext4 using 120GB mounted as /dev/sda1
swap using 8GB mounted as /dev/sda2
/boot as ext3 using 150MB mounted as /dev/sda3 (can I use ext4 for the boot partition?)
/home as ext4 using 500GB mounted as /dev/sdb1

My main question is:

Do I really need to specify a mount point for /tmp, /usr, /var, /srv, /opt and /usr/local if / is already to be installed in a 120GB partition?

Thanks for any answers you can provide.

---

### Post by audiomick on 2009-12-11
The prevailing advice is that if you are not doing anything out of the ordinary, you do not need to separate more than / and /home. For a modern machine with lots of RAM, a swap is, I believe, not strictly necessary, but is strongly suggested. For one thing, you need a swap that is as big as you RAM in order for the suspend / hibernate functions to work.

As far as / goes, mine has only got 6GB in it, and that after three updates and installing anything that caught my attention for the last 2 years. A fresh install I did recently only had about 2.7GB in there.

The common consensus seems to be:

/ 10 - 15 GB
swap a bit bigger than your RAM
/home the rest.

Given that you have so many discs, put the / , /home and swap on one. Format the others to a linux file system, and choose a mount point for them during the installation. I believe you have the option to do this.

---

### Post by presence1960 on 2009-12-11
> **audiomick said:**
> The prevailing advice is that if you are not doing anything out of the ordinary, you do not need to separate more than / and /home. For a modern machine with lots of RAM, a swap is, I believe, not strictly necessary, but is strongly suggested. For one thing, you need a swap that is as big as you RAM in order for the suspend / hibernate functions to work.

As far as / goes, mine has only got 6GB in it, and that after three updates and installing anything that caught my attention for the last 2 years. A fresh install I did recently only had about 2.7GB in there.

The common consensus seems to be:

/ 10 - 15 GB
swap a bit bigger than your RAM
/home the rest.

Given that you have so many discs, put the / , /home and swap on one. Format the others to a linux file system, and choose a mount point for them during the installation. I believe you have the option to do this.
when you select the manual option of the install process you are going to have to select each partition (/, /home, /boot) and click Edit. Then you will select Use as (filesystem) & from the mount point drop down box select the appropriate mountpoint for each partition, i.e. / for root partition, /home for home partition and /boot for boot partition. For swap highlight the swap partition and make sure use as is set to linux-swap. If you already have data on the newly created /home **DO NOT TICK the format box as you will wipe it!** Then proceed with the install.

If you do not specify mountpoint for root the install will not continue. If you do not specify mount points for /home & /boot they will not be mounted when you boot after the install, if you can even boot into Ubuntu at all  since your boot files are in /boot

The others you can leave in /. Just make it big enough (10-20 GB)

---

### Post by oldfred on 2009-12-11
I am not sure why you even want a separate /boot nowadays. In the old days when linux was primarily a server everything was a different partition and each was sized depending on what applications the server was runing. It made it a little easier to monitor if some partition was filling up.

Now with large hard drives there is little reason for all the partitions. I hear the reasons for a separate /home and I just did that on my new install of Karmic. My install for the last 3 years was just root & home with a NTFS shared partition for some windows stuff. I also now created a /data partition and the vast majority of my data is in the data partition. My /home only has some config info and a little else. I also noted that I did not want to copy all my old /home as it also had 3 years of stuff that was not all current.

Also if you elect to install some other Linux, they may require a separate boot but you cannot share a boot partition with other linux.

---

### Post by presence1960 on 2009-12-11
[QUOTE=audiomick;8482897]

mistake

---

