---
title: "XFS destroyed?"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by chefweb on 2007-05-10
Hello, 

I need your help. The harddisk of my NAS has an error. Now I have installed the drive into an USB-case and Ubuntu cant mount it. (superblock damaged) The repair with  "xfs_repair -v -o assume_xfs /dev/sdf" was not successful, after some hours comes the notice "Sorry, could not find valid secondary superblock" .....

What can I do to rescue my data?
Is it possible to generate a "synthetic" superblock?

---

### Post by kidders on 2007-05-11
Hi there,

I'm not intimately familiar with XFS, but I saw that your thread has remained unanswered for quite some time, so I thought you might appreciate a reply. (At the very least, my post will bump you back up the recent posts list hehe!)

Afaik, filesystem superblocks can't really be "manufactured" terribly easily. Even if they could though, the fact that you haven't been able to find any backups is concerning. Since the superblock is so important, most filesystems (and I'm assuming XFS is no exception) create a large number of backups ... so if not even *one* can be found, that suggests that a large chunk of the filesystem has been very badly damaged or erased.

Basically, I'd say it's forensic data recovery time. :-( There are a few tools out there (including one or two in the software repositories) that might be worth a try. At the very worst, you can expect to be able to perform a metadata-based recovery, which relies on the fact that certain files (eg jpegs, gzipped archives, etc.) have clear, predictable file formats that facilitate their identification.

One piece of advice I would give (assuming the lost data are very important) is not to make any permanent changes to your damaged filesystem without creating a backup first (perhaps using **dd**). That way, you can always undo anything that makes the situation worse.

I hope that's of some help.

---

