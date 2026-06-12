---
title: "chmod of symlink to NTFS volume for multi-boot systm"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by markosjal on 2013-01-30
I am actually using Mint 14 cinnamon but as these forums are more active, I am looking for an answer wherever I can

I have finaly set up my dream multi Boot Win7/OSX/Mint system with one exception. The mint part which I thought would be the easiest is turning out problmatic.

You see I have 5 partitions as follows
Win NTFS
OSX HFS+
Mint ext4
Files NTFS (for commn documents folders from all OSs)
Linux Swap

In windows I can define locations for user documents, and set to Files

In Mac OSX I can mount NTFS with read/write and FUSE then made a symlink to Files

In Mint however I made a symlink much like OSX, and at boot Mint complains because other users have write privlidges to the "user" directory apparently as defind by the symlink. I can not even seem to change the permissions on the symlink. I was finally able to recreate it in the userspace without "sudo" so the owner shows correctly. When I previously tried to chown it woud not work. I also tried to chmod 755 on the symlink and can not change the permissions. Is there somthing I am missing ir a better way to define the user file locatons?

---

