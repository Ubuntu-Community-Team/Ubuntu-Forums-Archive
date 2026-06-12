---
title: "Update from Sept. 1 stopped my system from booting, running RAID"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by MrWookie on 2007-09-03
After the update on Sept. 1 2007, my system would no longer boot.  I came here and looked around and thought I'd found the solution, but I managed to keep digging myself into a deeper and deeper hole.  Maybe I should have started a thread about my personal configuration earlier.  Oh well.

First off,  a run down of my system.  I'm running Ubuntu 7.04, the 64 bit version on an intel core2 quad 6600.  I have four hard drives configured to use RAID.  The first 15 GB of each drive is for a RAID 1 array, all of them tied together and found at /dev/md3, subsequently mounted at / and housing the OS.  The second partition on each is a 1 GB section configured for RAID 0 at /dev/md1 for swap.  The remaining space is RAID 5 at /dev/md2 and mounted at /home.

The story so far:

I noticed that there were new updates on Sept. 1.  I installed them, rebooted, and my system wouldn't boot.  It gave the error:

mdadm: no devices listed in conf file were found
kinit: name_to_devt(/dev/md1) = md1(9,1)
kinit: trying to resume from /dev/md1

and then it failed and hung.  I'm a fairly new Linux user, so I wasn't entirely sure what this meant.  I rebooted and went to see if one of the recovery or older kernels would boot.  The default was the 2.6.20-16-generic kernel, and that clearly didn't work.  The recovery mode of that kernel also didn't work.  However, 2.6.20-15-generic did boot.  I was happy, but I wanted to figure out what was wrong, so I came to the forums here.  It looked like other people were having problems along the same lines, and it was due to a changing UUID.  So, I looked in /dev/disk/by-uuid/, and the uuids that were listed were, in order,

1ea0e25d-af04-45fd-ae72-3a2101c77dc2
4edffc0a-8b0b-4ffd-a407-8eb6e7683690
f7904142-c378-4b14-9568-5c3885fee4f5

This matched the contents of my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md3
UUID=4edffc0a-8b0b-4ffd-a407-8eb6e7683690 /               ext3    defaults,errors=remount-ro 0       1
# /dev/md2
UUID=f7904142-c378-4b14-9568-5c3885fee4f5 /home           ext3    defaults        0       2
# /dev/md1
UUID=1ea0e25d-af04-45fd-ae72-3a2101c77dc2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

However, it didn't match the UUIDs in my mdadm.conf file:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md3 level=raid1 num-devices=4 UUID=33b790d8:9fc71f6c:afb8cfea:0559d799
ARRAY /dev/md1 level=raid0 num-devices=4 UUID=4bc70788:2120d41e:354c1e17:779ac6bc
ARRAY /dev/md2 level=raid5 num-devices=4 UUID=f6535af8:1b0fcafe:95e489b7:a428db60

# This file was auto-generated on Wed, 25 Jul 2007 22:54:42 +0000
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $
```

I figured this was the problem.  So, I made a backup of mdadm.conf and changed the UUIDs in the conf file to match the other two sources, although I changed the spacing to match how it was done in the mdadm.conf file:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md3 level=raid1 num-devices=4 UUID=4edffc0a:8b0b4ffd:a4078eb6:e7683690
ARRAY /dev/md1 level=raid0 num-devices=4 UUID=1ea0e25d:af0445fd:ae723a21:01c77dc2
ARRAY /dev/md2 level=raid5 num-devices=4 UUID=f7904142:c3784b14:95685c38:85fee4f5

# This file was auto-generated on Wed, 25 Jul 2007 22:54:42 +0000
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $
```

Well, something about that turned out to be a mistake.  Now could I not only not boot to the -16 kernel, I couldn't boot to the -15 kernel either.  So, I hatched a brilliant plan to boot to the live cd and copy the mdadm.conf.backup file I'd made over the top of the current, broken mdadm.conf file.  That's why we make backups, after all.  Well, naturally, the live cd didn't recognize any of the RAID stuff, but I could still mount and examine the contents of /dev/sda1, sdb1, sdc1, and sdd1, so I just restored the backup file on each of the drives individually.  This also turned out to be a mistake.  I did something like this earlier when a lab mate with an identically configured workstation had screwed up his xorg.conf file.  Ubuntu recognized that something wasn't quite right with the RAID 1 array, and it fixed it automatically.  Not so this time.  When I'd try to boot to the -15 kernel, Ubuntu thought something was quite wrong with the file system.  It actually got me to the log in screen, but I'd try to log in and it gave me an error about my home directory not existing.  It'd then log me out immediately, saying that I should maybe try a failsafe session.  Well, the failsafe session didn't work, either.  

So, here I sit typing in a post on the forums here having booted once again from the live CD.  Apparently I need more hand holding through this than I thought.  Any help you guys can offer to help me recover from my series of mistakes would be much appreciated.

---

