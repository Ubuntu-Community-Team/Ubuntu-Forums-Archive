---
title: "S30checkfs.sh fails on jfs filesystems on Feisty"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by mrxdimension on 2007-04-22
After upgrading my laptop from Edgy to Feisty /etc/init.d/rcS.d/S30checkfs.sh fails to check jfs filesystems, and drops to a prompt.  Typing exit at the prompt allows the bootup to continue normally.  This only happens with the Feisty GA 2.6.20-15 kernel, not when booting the same system with the previous Edgy 2.6.17-11 kernel.

I've seen the posts about fstab and UUID's and hdX changing to sdX, I believe this is a different issue.

I also have another system I upgraded from Edgy to Feisty.  It has none of these boot issues, it does run jfs filesystems for everything except / and /boot, it uses scsi disks.


mrx@spotty:~$ cat /root/checkfs 
Log of fsck -C -R -A -a 
Sun Apr 22 13:31:50 2007

fsck 1.40-WIP (14-Nov-2006)
/boot: clean, 37/49152 files, 54216/98280 blocks
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 4/22/2007 13.31.51
The current device is:  /dev/sda13
Block size in bytes:  4096
Filesystem size in blocks:  5138902
**Phase 0 - Replay Journal Log
Filesystem is clean.
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 4/22/2007 13.31.51

Error: Cannot open device UUID=f6d32f70-6401-455a-add3-2b37a935b87b

Usage:  fsck.jfs [-afnpvV] [-j journal_device] [--omit_journal_replay] [--replay_journal_only] device

Emergency help:
 -a                 Automatic repair.
 -f                 Force check even if file system is marked clean.
 -j journal_device  Specify external journal device.
 -n                 Check read only, make no changes to the file system.
 -p                 Automatic repair.
 -v                 Be verbose.
 -V                 Print version information only.
 --omit_journal_replay    Omit transaction log replay.
 --replay_journal_only    Only replay the transaction log.
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 4/22/2007 13.31.51

Error: Cannot open device UUID=d7992995-fa20-4227-bfc4-50b98f20af55

Usage:  fsck.jfs [-afnpvV] [-j journal_device] [--omit_journal_replay] [--replay_journal_only] device

Emergency help:
 -a                 Automatic repair.
 -f                 Force check even if file system is marked clean.
 -j journal_device  Specify external journal device.
 -n                 Check read only, make no changes to the file system.
 -p                 Automatic repair.
 -v                 Be verbose.
 -V                 Print version information only.
 --omit_journal_replay    Omit transaction log replay.
 --replay_journal_only    Only replay the transaction log.
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 4/22/2007 13.31.51

Error: Cannot open device UUID=b77c5ddd-9f27-49ad-b1f6-d32ab7f53497

Usage:  fsck.jfs [-afnpvV] [-j journal_device] [--omit_journal_replay] [--replay_journal_only] device

Emergency help:
 -a                 Automatic repair.
 -f                 Force check even if file system is marked clean.
 -j journal_device  Specify external journal device.
 -n                 Check read only, make no changes to the file system.
 -p                 Automatic repair.
 -v                 Be verbose.
 -V                 Print version information only.
 --omit_journal_replay    Omit transaction log replay.
 --replay_journal_only    Only replay the transaction log.
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 4/22/2007 13.31.51

Error: Cannot open device UUID=408c5b1f-e69a-44bd-b7ae-7741178f44a6

Usage:  fsck.jfs [-afnpvV] [-j journal_device] [--omit_journal_replay] [--replay_journal_only] device

Emergency help:
 -a                 Automatic repair.
 -f                 Force check even if file system is marked clean.
 -j journal_device  Specify external journal device.
 -n                 Check read only, make no changes to the file system.
 -p                 Automatic repair.
 -v                 Be verbose.
 -V                 Print version information only.
 --omit_journal_replay    Omit transaction log replay.
 --replay_journal_only    Only replay the transaction log.
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 4/22/2007 13.31.51

Error: Cannot open device UUID=fd2f2ca5-1a7d-4e75-ae37-59babba28751

Usage:  fsck.jfs [-afnpvV] [-j journal_device] [--omit_journal_replay] [--replay_journal_only] device

Emergency help:
 -a                 Automatic repair.
 -f                 Force check even if file system is marked clean.
 -j journal_device  Specify external journal device.
 -n                 Check read only, make no changes to the file system.
 -p                 Automatic repair.
 -v                 Be verbose.
 -V                 Print version information only.
 --omit_journal_replay    Omit transaction log replay.
 --replay_journal_only    Only replay the transaction log.
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 4/22/2007 13.31.51

Error: Cannot open device UUID=1b653196-ece8-43e1-9773-5fa308f89a7a

Usage:  fsck.jfs [-afnpvV] [-j journal_device] [--omit_journal_replay] [--replay_journal_only] device

Emergency help:
 -a                 Automatic repair.
 -f                 Force check even if file system is marked clean.
 -j journal_device  Specify external journal device.
 -n                 Check read only, make no changes to the file system.
 -p                 Automatic repair.
 -v                 Be verbose.
 -V                 Print version information only.
 --omit_journal_replay    Omit transaction log replay.
 --replay_journal_only    Only replay the transaction log.
fsck died with exit status 16

Sun Apr 22 13:31:51 2007


mrx@spotty:~$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5 -- converted during upgrade to edgy
UUID=d4799fa4-688d-47f2-825c-7724a9f62cc0 / ext3 noatime,errors=remount-ro 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=b6d658a2-173c-4048-8fb4-0f1ce35b66a0 /boot ext3 noatime 0 2
# /dev/hda13 -- converted during upgrade to edgy
UUID=716a05ef-0b5a-4d33-9efc-a5641c6f22a4 /home jfs noatime 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=785CC0E45CC09DEE /media/hda1 ntfs defaults 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=F7D9-61A1 /media/hda2 vfat defaults 0 0
# /dev/hda12 -- converted during upgrade to edgy
UUID=f6d32f70-6401-455a-add3-2b37a935b87b /srv jfs noatime 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=d7992995-fa20-4227-bfc4-50b98f20af55 /tmp jfs noatime 0 2
# /dev/hda8 -- converted during upgrade to edgy
UUID=b77c5ddd-9f27-49ad-b1f6-d32ab7f53497 /usr jfs noatime 0 2
# /dev/hda11 -- converted during upgrade to edgy
UUID=408c5b1f-e69a-44bd-b7ae-7741178f44a6 /usr/local jfs noatime 0 2
# /dev/hda9 -- converted during upgrade to edgy
UUID=fd2f2ca5-1a7d-4e75-ae37-59babba28751 /var jfs noatime 0 2
# /dev/hda10 -- converted during upgrade to edgy
UUID=1b653196-ece8-43e1-9773-5fa308f89a7a /var/log jfs noatime 0 2
# /dev/hda7 -- converted during upgrade to edgy
UUID=d5ee16d4-f4eb-49c6-8d85-b7c9604c2d76 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
tmpfs           /dev/shm        tmpfs   defaults,ro     0       0
mrx@spotty:~$

---

