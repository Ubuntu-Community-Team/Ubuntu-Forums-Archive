---
title: "Can Home be shared with another distro?"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by SuperFreak on 2012-09-15
Thinking of installing Mint along side of 12.04 Ubuntu. I have Home in it's own partition and woder how/if I can somehow have Mint installed such that it shares my Ubuntu Home directory. Also so files in my home directory are not deleted during Mint install.

---

### Post by oldfred on 2012-09-15
Not really recommended. 

Those that say you can just use the same partition and a different user ID, so you have two users in the same partition. But then you are not sharing anything. 

You may end up with conflicts. And they may not show right away.

Better to keep /home inside / (root) with multiple installs and create a shared data partition for all user data, but not the mostly hidden user settings from /home. My /home is less than 2GB with over 1GB of that as .wine. All the rest of my data is in two shared data partitions, one NTFS from when I still used XP and the other ext3 (I would use ext4 now) for new data to share with different Ubuntu installs.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by SuperFreak on 2012-09-15
Thanks Old Fred. I have a Storage Partition that contains most of my data so it isn't a big deal. I'll put Mint into one partition(home and root). Can my existing swap partition be used or do I need a new one?

---

### Post by oldfred on 2012-09-15
If you do not hibernate as system is storage into swap nor have encryption as each would be different, then you can share swap. 
I only have one swap per drive (except SSD), but some of my installs seem to still find more than one. I use manual install and it normally finds swap on its own.

---

### Post by SuperFreak on 2012-09-15
Thanks

---

