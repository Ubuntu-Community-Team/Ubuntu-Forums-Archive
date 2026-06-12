---
title: "Help Moving system folder/partition"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by peachstone on 2008-03-13
When i installed Ubuntu, i made 4 partitions, 
Partition 1- fat 32 - XP
Partition 2- ext 2 - Ubuntu System 
Partition 3- Wanted it to be /home for my files
Partition 4- swap
I unknowingly made that 3rd partition the **/usr** folder and not /home. Can anyone tell me how to fix this?

Also, if i add drives to this machine whould i partition them with ubuntu or windows? And what file system for windows and ubuntu?

Thanks

---

### Post by logos34 on 2008-03-14
[This guide]("http://yavin4.anshul.info/2006/07/17/moving-usr-to-another-partition/") looks like it should work--just reverse the process.

(skip the step "rm -rf /usr_new/*")

Basically you're just making a new directory in root, copying everything (with cp -dpR or cp -a) on the /usr partition to the new directory, then deleting the fstab entry. Then after you're sure it boots and works fine, erase the old separate /usr.

To move /home to separate partition, use [this howto]("http://www.psychocats.net/ubuntu/separatehome").

Use **Gparted** in linux to format/partition new hard disks.  NTFS or fat32 for win (preferably the former because you can write to it from linux with ntfs-3g) and ext3 for linux.  (butyou could also use reiserfs or others like xfs)

---

