---
title: "After 12.04 LTS -&gt; 14.04 LTS -&gt; 16.04.3 LTS  Root file system often mounts readonly"
date: 2018-01-18
forum: Installation &amp; Upgrades
---

### Post by cube1us on 2018-01-18
I recently upgraded a pair of Ubuntu systems from 12.04 LTS to 14.04 LTS and then immediately to 16.04.3 LTS (xenial).

One of the systems seems fine.  The other, however has the following issue.  MOST of the time (say 3/4 of the time) the root file system mounts readonly.  Once in a while, it mounts r/w, and everything is fine.  The file system always checks just fine.

It looks like there may be a race condition between systemd-remount-fs.service and local-fs-pre.target and local-fs.target  (note:  systemd is brand new to me).

Here are the messages from dmesg that seem to be relevant:

[    8.437943] EXT4-fs (sda3): mounting ext3 file system using the ext4 subsystem
[    8.450833] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   14.067811] systemd[1]: local-fs.target: Found dependency on systemd-remount-fs.service/start
[   14.067985] systemd[1]: local-fs.target: Found dependency on systemd-remount-fs.service/start
[   14.067998] systemd[1]: local-fs.target: Breaking ordering cycle by deleting job systemd-remount-fs.service/start   <<<<<< THE PROBLEM?
[   14.068001] systemd[1]: systemd-remount-fs.service: Job systemd-remount-fs.service/start deleted to break ordering cycle starting with local-fs.target/start
[   14.069203] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   30.466038] EXT4-fs (sda1): mounting ext3 file system using the ext4 subsystem
[   30.482607] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   40.129605] cgroup: new mount options do not match the existing superblock, will be ignored

The result is that the desktop does not start, etc. etc.    However, if I then log in via SSH and do:

# systemctl start systemd-remount-fs.service

Then the root file system mounts just fine.

My /etc/fstab is shown below (Note, the comments identifying the devices /dev/sdb3, /dev/sdb1 and /dev/sde2 are no longer relevant.  They date back to when this system had multiple disks.  In fact / is /dev/sda3 and /boot is /dev/sda1 and swap is /dev/sda2 .

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=f5e2f8ee-adac-48ad-8483-e04ae0da9580 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
#UUID=2f2eef15-17d3-4886-9ffa-6666dc8ad8d4 /boot           ext3    relatime        0       2
# /dev/sde2
UUID=d6054f01-2d94-4b27-8662-3ba22ab123c9 none            swap    sw              0       0
# /dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=2f2eef15-17d3-4886-9ffa-6666dc8ad8d4       /boot   ext3    defaults        0       2


[rants about systemd withheld for now.]

---

### Post by TheFu on 2018-01-19
Perhaps it is time for a fresh install?  Lots of things have changed since 2012.

---

### Post by cube1us on 2018-01-19
Perhaps.  But perhaps not.  This is, apparently, a race condition of some sort.  And in taking that path I might also go through hours and hours and hours of work to do that, only to have the problem still be there.  Also, this really ought to be diagnosable and fixed, given the messages.  And I have 3 other systems in the same state - so I might end up having to do multiple from-scratch installs, which isn't a very attractive option.

And, given all of this, it might well send me in a completely different direction if I do that - like a distro that doesn't use systemd at all.  ;)

I looked at the systemd config files related to local-fs* and systemd-remount-fs* on both systems and they are the same.  There also does not appear to be any hard dependency between them (just the soft dependencies of "wants" and "after").

Also, curiously, for the system that works, the kernel level it ended up with is 3.13.0-139, but the broken one went up to 4.4.0-104 .

---

### Post by TheFu on 2018-01-19
A fresh install would get ext4 by default.  Not many people use ext3 anymore so I wouldn't be surprised if the testing for interactions isn't as complete.  That's just one difference.

If you find a good non-systemd distro that meets the requirements and makes you happy, please let me know. I'm not a fan either and have a number of 14.04 servers here that I was planning to move to 16.04 this year. I haven't found any good alternatives.

For a desktop, I always do a fresh install and move my data over.  GUI stuff just complicates things too much and with 45,000+ packages, it is impossible to ensure all of those migrate forward cleanly.

---

### Post by cube1us on 2018-01-19
The other machine I have is ext3, and it works just fine.  It uses the same filesystem module (EXT4) - after all the differences from ext2 to ext4 are really a matter of details, like journaling, and the like... so much so that it really isn't hard to upgrade in place.  I very much doubt that has anything to do with it. These suggestions are all really just workarounds, and I would prefer not to go down that path.  This is a bug, I think (unless/until someone gives me a real answer otherwise).  What I'd really like is some suggestions on how to track down the real issue, even if it turns out it is in systemd itself.

You might visit [http://without-systemd.org/wiki/index.php/Main_Page](http://without-systemd.org/wiki/index.php/Main_Page) if you have not already done so.

None of this has anything to do with the GUI.  I generally don't fuss with the GUI much, and this startup issue is well before the GUI gets started (and, of course, when the filesystem doesn't mount rw, the GUI doesn't start at all).

---

