---
title: "fsck check failure following upgrade from edgy to fiesty"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by maddentim on 2007-04-23
I have desktop system that was running edgy.  I did the upgrade to fiesty.  All seemed fine but when I rebooted, the /dev/hdd1 failed.  

The error message was (I wrote most of it down on paper so there might be gaps):

fsck.ext3: no such file or directory while trying to open /dev/hdd1^M
/dev/hdd1
superblock could not be read or does not describe a correct ext2...

It then goes not to say that it may repairable by running : e2fsck -b 8193 <device>

I substituted /dev/hdd1 for <device> but the command did not work.

Any help greatly appreciated.  /dev/hdd1 is /home so I would like to at least get the data off it...

---

### Post by pepsi_max2k on 2007-04-23
check /etc/fstab for errors (could use vi to edit it). is /home deffinately on hdd1, and definately ext3?

---

