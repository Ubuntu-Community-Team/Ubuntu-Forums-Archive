---
title: "Second ext3 disk permissions"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by LaserGuidedStefan on 2007-12-18
Ng,

I'm trying to share files between window$ and ubuntu on the same host. I have three partitions, NTFS for winXP, ext3 for ubuntu 7.04 and another ext3 'in between'. I usually run winXP in a virtual machine on my ubuntu host, and I connect to the ext3 partition via samba. This setup works fine...

However, when i mount the second ext3 partition, all files that I create get [-rw-r--r--] permissions. So I can't manipulate them from winXP. The partition is pretty straight forward. My fstab entry looks like this:

  /dev/sda6  /media/mezzanine  ext3  defaults  0  0

My 'unmounted' mount point looks like this:

  drwxr-xr-x  2 root root 4.0K 2007-12-18 08:49 mezzanine

After mounting it, I issued:

 ~$ sudo chown -R myUserName:myUserName /media/mezzanine
 ~$ sudo chmod -R 775

This takes care of the current files, but all files that I create get [-rw-r--r--] permissions. I would like them to get [-rwxr-xr-x] so that others can manipulate the files on my second ext3 partition (i.e. users connecting to the disk from winXP via samba).

I've tried mount options like 'umask' and 'gid / uid'. But they don't work on ext3, and I know that I could use FAT32, but I need the journaling stuff...

---

### Post by vanadium on 2007-12-18
It looks like you want the 'others" permissions for new files created by you to default to read/write for documents and read/write/execute for directories. This is controlled by the umask. Before working on the drive, issue the command

umask 0000

then any file you newly create will get the permissions you want. The default umask is 0022 (type "umask 0022" to reset it).

For existing files, you eventually need to change the permissions:

chmod 666 <filenames>

Linux is tricky in file permissions. If you want to work more "insecure" than the default, you explicitly have to tell the system, which for example here can be somewhat slightly inconvenient. Perhaps, there is another possibility I am not aware off.

---

