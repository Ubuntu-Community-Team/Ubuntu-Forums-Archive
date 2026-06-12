---
title: "Compaq n610c Installation Error: &quot;failed to create a filesystem&quot;"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by ubusaj on 2006-08-12
During the Dapper Installing System phase it says "creating ext3 file system for / partition in #1 of IDE1 master (hda)..." and it gets to 5% and says "failed to create a filesystem".

My hard disk is fine, so I'm not sure why I'm getting this error.  How can I get past this?

---

### Post by ubusaj on 2006-08-12
Ok, disregard.  I downloaded 6.06.1 and the installation is progressing nicely.

---

### Post by ubusaj on 2006-08-12
Ok, I spoke too soon.  Installation get to the copying files stage and is stalled at 50%.  After 30 minutes at 50%, the entire system was frozen.  Keyboard, mouse, CTRL-ATL-DEL, nothing worked.  I bailed and shutdown.

Anyone know what's going on here?

---

### Post by dancin_fool on 2006-10-07
I got this message trying to install ubuntu on top of an existing Red Hat Fedora Core 5 install on a Dell Inspiron laptop.

I was able to fix it by running fdisk and deleting all existing partitions, and using the ubuntu installer to do the partitioning.  Note that to run fdisk you need to be root, so run
```
sudo su -
```
before running fdisk.  Also, you need to specify which disk.  This will probaby be /dev/hda1:
```
fdisk /dev/hda1

```
Years ago I was afraid to run fdisk, but have learned that if your data is backed up there is absolutely nothing to fear.  You can quit without changing the disk partition table, and as the prompt says you just need to enter m for help. More details are available on the man page
```
man fdisk

```
Hope this helps!

---

