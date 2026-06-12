---
title: "ntfs with no filesystem defined?"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by Drewreka on 2009-12-07
First off, I'd like to ask you all to pardon my terrible lingo, I don't know what some things are called, but I'll do my best to explain.

I'm not terribly advanced at partitioning, but from what I can tell, it seems like the filesystem type of my ntfs partition (win7) has been erased from the mbr somehow.

Its really strange, as if the filesystem was intact, but it wasn't labeled correctly.

Heres fdisk -l  :
 
root@cblaptop:~# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1979       38652   294583905    7  HPFS/NTFS
/dev/sda2   *           1        1978    15888253+  83  Linux
/dev/sda4           38653       38913     2096482+  82  Linux swap / Solaris

/dev/sda1 is my windows 7, and it shows up fine and dandy here, but when I go to mount it, I get this:

root@cblaptop:~# ntfs-3g /dev/sda1 /home/rdw/C 
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

From what I can tell, the partition (and hopefully the data) is still intact, so I'd really like to avoid reformatting that partition.

When I use the exact same command to mount a removable disk I have (also ntfs) it works fine, so im fairly confident that's not the issue.

If I try to use -f on the command to force it to mount, or -o recover, i get the same output.

--Thanks in advance; I've looked all over and can't find a solution for this.

---

