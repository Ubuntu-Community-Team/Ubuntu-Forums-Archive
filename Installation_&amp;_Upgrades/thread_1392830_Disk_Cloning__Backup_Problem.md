---
title: "Disk Cloning / Backup Problem"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by paxxus on 2010-01-28
[FONT=Courier New]Hi,

I'm trying to establish an automated backup strategy for my HDD. The goal is a fully scripted approach which is able to COMPLETELY restore my HDD on another disk, should the need arrive. Also, I want to copy only the data (not empty sectors) on a per partition basis.

For a start I did:

dd if=/dev/sda of=/def/sdb

It took forever but the target disk (/dev/sdb) booted just fine afterwards (both Ubuntu and Vista). So, it's possible but obviously not what I want. Instead I tried this approach (in that order):

Save commands:
dd if=/dev/sda of=sda.mbr count=1 bs=512
sfdisk -d /dev/sda > sda.pt
partimage -V 0 -z1 -o -d -b save /dev/sdaN sdaN.gz (for N in [1 2 4 6 7])

Restore commands:
dd if=sda.mbr of=/dev/sdb
sfdisk --no-reread -f /dev/sdb < sda.pt
partimage -b restore /dev/sdbN sdaN.gz (for N in [1 2 4 6 7])
mkswap /dev/sdb5

I've made a neat script which does all this for me and I can now backup my main HDD (/dev/sda) on a much smaller external USB disk. Nice!..... except, /dev/sdb wont boot :(

When I boot from /dev/sdb (which is actually now called /dev/sda, bacause I disconnected my main disk) it just displays "GRUB" followed by a blinking cursor.

So, I must conclude that my procedure does in fact not create a complete copy like a raw dd of the entire disk does.

/dev/sda and /dev/sdb are of identical brand and model.

What am I missing here?

fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37053704

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     1028159      514048+  83  Linux
/dev/sda2   *     1028160   410637464   204804652+   7  HPFS/NTFS
/dev/sda3       410637465   820230704   204796620    5  Extended
/dev/sda4       820232192   976769023    78268416    7  HPFS/NTFS
/dev/sda5       410637528   418830614     4096543+  82  Linux swap / Solaris
/dev/sda6       418830678   582677549    81923436   83  Linux
/dev/sda7       582677613   820230704   118776546   83  Linux


Thanks!

PS.: Just to see if I could get some life into the target disk i did:

grub-install --recheck /dev/sdb

This enabled the target disk to boot into the the GRUB menu and my Ubuntu worked fine, but my Vista (on /dev/sda2) didn't work - again an indication that my copy procedure is missing something (because the raw dd of the whole disk works just fine).

[/FONT]

---

### Post by paxxus on 2010-01-28
Anyone...?

---

### Post by paxxus on 2010-01-29
Isn't this sort of thing pretty standard stuff? Must be a simple error I've done, no...?
 
Do I need to repost in the Beginner Forum...?

---

### Post by paxxus on 2010-01-31
Tried clonezilla instead, but it terminated with a "syntax error" - clonezilla appears to be a complicated way of basically doing the steps I've outlined anyway.

---

### Post by paxxus on 2010-01-31
OK, I got my original plan working. After some study I found out that the 62 "unused" sectors after the MBR does in fact contain various hidden/secret stuff. If I copy the MBR **and** the following 62 sectors my clone works perfectly (both Vista and ubuntu).

Judging from the feedback I got in this sub-forum I guess I have posted this in the wrong forum. For the benefit of others I have made a post in the "General Help" sub-forum outlining my solution including the simple backup/clone script I made.

---

