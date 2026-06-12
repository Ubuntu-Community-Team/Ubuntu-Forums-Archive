---
title: "Dual boot, how to install over previous Linux install"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by Foxblood on 2010-10-08
Hi, I'm trying to install Zorin, a Ubuntu-based distro. Zorin uses, from what I remember, the same installer as Ubuntu. I dual boot Win 7 and Sabayon. I have a 1 Tb hard drive that I divided equally, more or less, between Win 7 and Sabayon. I want to intall over the existing Sabayon install. The installer seems to only see the Win 7 partition, which gives me the only option of Specify partitions manually (advanced). 

In the prepare partitions settings screen I have these:

sda1 ntfs 503007 MB 89128 MB used
sda2 ext4 524MB 48 MB used
sda3 no type specified 496670 MB unknown used
sdb1 ntfs 500105 MB 469564 MB used

I don't know how these need to formatted. Any help would be appreciated. Thanks.

---

### Post by andrewthomas on 2010-10-09
> **Foxblood said:**
> Hi, I'm trying to install Zorin, a Ubuntu-based distro. Zorin uses, from what I remember, the same installer as Ubuntu. I dual boot Win 7 and Sabayon. I have a 1 Tb hard drive that I divided equally, more or less, between Win 7 and Sabayon. I want to intall over the existing Sabayon install. The installer seems to only see the Win 7 partition, which gives me the only option of Specify partitions manually (advanced). 

In the prepare partitions settings screen I have these:

sda1 ntfs 503007 MB 89128 MB used
sda2 ext4 524MB 48 MB used
sda3 no type specified 496670 MB unknown used
sdb1 ntfs 500105 MB 469564 MB used

I don't know how these need to formatted. Any help would be appreciated. Thanks.
from the looks of it you could
 set sda3 as ext4 mounted at / 
and sda2 as /swap although that seems a bit small. 
 If you have plenty of RAM and do not hibernate you should be ok.

---

### Post by Foxblood on 2010-10-10
Thanks, I did as you advised and had a problem-free install. Now to sort out my signature;)

---

