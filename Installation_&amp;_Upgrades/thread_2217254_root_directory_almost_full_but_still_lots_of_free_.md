---
title: "root directory almost full but still lots of free space on the partition"
date: 2014-04-16
forum: Installation &amp; Upgrades
---

### Post by knabbits on 2014-04-16
hey people,
some time ago I installed 12.04 from windows xp on a separate "linux" partition via wubi. this partition was allocated 50 GB. my problem now is that obviously the root directory does not have access to the entire volume but only to about 10 gigs which is now not very far from being stuffed.  the attached system monitor image should explain it

as you can see I have the hard drive divided into 3 partitions altogether: the windows volume (sda1) with 146 gigs, a "save" volume (sda6) for backups and stuff with some 103 gigs and the linux volume (sda5) with about 50 gigs of space being host of this strange subdivision loop0 where the root directory seems to be placed (so this 10 gigs of the loop0 division seem to belong to the sda5 partition, at least thats what I get)

my question is: how can I make the ubuntu root directory to have access to the full 50 gigs of the partition instead of being restricted to the loop0 subdivision

easy to notice I yet dont know much bout linux file structure but still thats the issues that make you want to understand it

thanx

to give you some more info about what really belongs to what I put two additional screen prints of gparted and terminal df and mount commands

---

### Post by oldfred on 2014-04-16
Wubi is not a partitioned install. One of its advantages was that a new user did not have to partition.
It just is a large file inside a NTFS partition and uses the Windows boot loader.
It also has a max of 30GB, so it does not matter what size you made a partition to hold it.

If you like Ubuntu & plan to continue to use it, it is time to convert to a full install.

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: > Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

I would backup everything & reinstall using Linux partitions. Backup /home and if you installed a lot of applications, you can make reinstall easier by exporting a list of installed apps.

If you have space you can convert.
HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

