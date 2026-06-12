---
title: "Help with partition"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by ramsforums on 2012-06-14
Hello

I am setting up UBUNTU 12.04 desktop for sharing files with about 10 users in small office. It is HP Proliant ML 150 G6 server with 2 TB HDD.


Basically I share one directory where users will put shared contents. 

The server has 2GB Memory. I have also plan to use this server for running  a small CRM application which uses PostGresSQL.

I need help with the following.

Initially I thought I will partition  as follows

Boot  300 MB
SWAP  6 GB
/     300 GB
/HOME 1.5 TB


I had some hanging problem so I reformatted the drive and used default install. 

Default install did not Partition drive with multiple partition.

What is the best size I should set for partition.   Anything I missed while deciding partition? Do I need separate partition for /usr  /bin etc?


Thank you in advance.

---

### Post by aromo on 2012-06-14
It looks right given that it's a huge disk.

I have a 40GB disk and have something like:
128 MB /boot
2 GB swap
8 GB /
30 GB /DATA (shared directory)

Every 6 months with every new Ubuntu release, I blow up the /boot and / partitions and keep the user data intact.

---

### Post by ramsforums on 2012-06-15
thanks for the info.

---

### Post by darkod on 2012-06-15
You might enlarge the /boot to 500MB just in case, although 300MB should be fine for a few kernels. And you can always remove the older kernels. But if you want to avoid doing that regularly, think about 500MB for example.

A 300GB / is more than plenty, it would depend mostly on the applications you plan to run (their size) and the data size of the CRM application, and whether that data will be in / or /home.

If the databases are in /home, 300GB is way way too much. You can do with as little as 20GB since you seem to need only few apps on it. Lets say 50GB tops. You can dedicate the rest to /home if you plan to keep all your main data and large data there. On the other hand, on a 2TB disk you can spare the 300GB I guess.

The auto methods of installation would create only the standard / + swap installation. To have a separate /home and /boot you will need to use the manual install. The manual is recommended anyway because it gives you most control.

Also, I'm not sure if you plan to install Desktop and add Samba to share and PostgreSQL, or the Server version. Since you need this as a server, the server version looks like a better choice, but it depends how familiar you are with the command line because the server version installs that by default.

Also, depending on the importance of this data, have you considered buying one more 2TB disk and using a software RAID1 (mirror) to guard you against disk failure?

---

