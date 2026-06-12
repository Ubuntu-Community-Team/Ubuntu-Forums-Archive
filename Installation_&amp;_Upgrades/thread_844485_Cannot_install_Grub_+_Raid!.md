---
title: "Cannot install Grub + Raid!"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by Makuki on 2008-06-29
Hello, I'm new here also my english is not good but I will try to explain my problem.

I used this:

[http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation#Installation_on_RAID_0](http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation#Installation_on_RAID_0)

[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)

I finished my install of Ubuntu there is an error in 95% with Grub. Now I want to install it. That what I did:

- Close the installation.
- Open console
- Write this: sudo mount -t ext3 /dev/mapper/<RAID_SET_NAME><PARTITION_NUM> /target

Of course I used my Raid Name and Partition Number but there is an error. It cant use /target (or something like that :p).

Any ideas?

Sorry for my English,
Makuki!

---

### Post by dstew on 2008-06-29
You have to create the /target mount point first, before mounting your RAID partition to it:```
sudo mkdir /target
```It seems this step was omitted from the HowTo.

---

