---
title: "Unable to mount RAID 0 automatically at boot"
date: 2014-10-17
forum: Installation &amp; Upgrades
---

### Post by Derek_Gentle on 2014-10-17
Hello All

I just had to reinstall my OS due to a dead motherboard. I am now trying to mount the existing RAID 0 (4 x 3TB).  I'm not sure what I am missing, maybe someone can help point out where my error is?

My fstab:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=342d45fc-4d6c-4804-9095-039a1cd1f7f8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc1 during installation
UUID=76c1417b-2577-4637-a1d1-fb9b0544143a none            swap    sw              0       0
# media RAID array
/dev/md/0 /mnt/media ext4 noatime,commit=60,data=writeback,nodiratime,journal_async_commit,nouser_xattr 0 0

```

and my mdadm.conf:
```

#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 UUID=a6c6ed3c:aa19630d:b2302c3b:6d010118

# This file was auto-generated on Fri, 17 Oct 2014 16:30:54 -0400
# by mkconf $Id$
ARRAY /dev/md/0 UUID=a6c6ed3c:aa19630d:b2302c3b:6d010118

```

When attempting to mount manually, I get the following:

```

mount: special device /dev/md/0 does not exist 

```

What have I missed?

Thanks!

---

