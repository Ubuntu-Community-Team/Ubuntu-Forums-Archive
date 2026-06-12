---
title: "MOUNT error - PLEASE help"
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by monkeywork on 2005-10-02
I'm in a real pickle here and I hope one of you can help me out.   Was running Ubuntu Hoary and decided to try out Ubuntu Breezy just to see how things went.   Well after I installed it I found my vmware and a few other apps were broken and I decided to blow away the Breezy install and go back to Hoary.  

My machine is setup with two physical hard disks, HDA and HDB - the OS is installed on HDA and my important data is on HDB (a single JFS partition).  When I blew away Breezy to go back to Hoary I simply deleted the partitions on HDA and recreated them and left HDB unused.

After the OS is installed I've tried to remount the drive and running into some problems:

:# mkdir /store
:# mount -t jfs /dev/hdb1 /store
mount:  wrong fs type, bad option, bad superblock on /dev/hdb1, missing codepage or other error.

Concerned that I may have blown away the partition on HDB by accident I did the following:

:#  fdisk -l /dev/hdb

It tells me that I have the full disk used with an ID 83 Linux System partition, so it's still there.

I've tried the mount command without specifying the filesystem to see what it would do and the same problems happen.   Any suggestions would be great as I really need access to this data.

---

### Post by GreyFox503 on 2005-10-02
Not a permanent solution, but you could use a Knoppix CD to try to view the contents of the partition.  Then you could confirm it still exists, and perhaps do a little work, or copy pertinent files somewhere else.

---

### Post by Emerzen on 2005-10-02
I'm not sure if the syntax you used is accepted, but here is the way I would have typed the mount command:

:# mount  /dev/hdb1 /store -t jfs

---

### Post by monkeywork on 2005-10-03
Thanks to both of you  -  found the solution,  I needed to do a fsck /dev/hdb1 and it did a quick check to say the journal was ok then allowed me to mount it.   I've never had an issue like that with JFS before, but seems to be fine now.

---

