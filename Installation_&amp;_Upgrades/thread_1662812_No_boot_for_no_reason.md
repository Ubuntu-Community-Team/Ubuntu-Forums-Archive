---
title: "No boot for no reason"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by dargaud on 2011-01-08
Hello all,
I installed Kubuntu 10.10 on an oldish laptop last month with no issue, and coming back from vacation I find out that it won't boot:
```

...End trace...
Killed
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init=bootarg

```
Then I get dumped to a BusyBox shell in iniramfs. I don't know what to do from there, but I booted from the liveCD and tried to mount /dev/sda1 to no avail (it just hangs and doesn't show in /proc/mounts). Then I tried an fsck:
```
# dmesg | grep sda
[    4.934210] sd 0:0:0:0: [sda] 123731968 512-byte logical blocks: (63.3 GB/59.0 GiB)
[    4.934266] sd 0:0:0:0: [sda] Write Protect is off
[    4.934270] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.934293] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.934483]  sda: sda1 sda2 < sda5 >
[    4.936532] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.620911] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    6.620918] EXT4-fs (sda1): write access will be enabled during recovery
[    6.628506] EXT4-fs warning (device sda1): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[    6.628514] EXT4-fs warning (device sda1): ext4_clear_journal_err: Marking fs in need of filesystem check.
[  124.918525] Adding 2569212k swap on /dev/sda5.  Priority:-1 extents:1 across:2569212k SS
[ 1591.635951] sda2: rw=0, want=4, limit=2
[ 1591.635959] EXT2-fs (sda2): error: unable to read superblock

# fdisk -l
Disk /dev/sda: 63.4 GB, 63350767616 bytes
255 heads, 63 sectors/track, 7701 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007eec4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7382    59293696   83  Linux
/dev/sda2            7382        7702     2569217    5  Extended
/dev/sda5            7382        7702     2569216   82  Linux swap / Solaris

# blkid 
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="dd00ea4d-5c75-4997-bd3e-3fbdd959deba" TYPE="ext4" 
/dev/sda5: UUID="e5565f6c-19d9-49d5-abf0-d3c23f4bee5f" TYPE="swap" 

# tune2fs -l /dev/sda1
tune2fs 1.41.12 (17-May-2010)
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          dd00ea4d-5c75-4997-bd3e-3fbdd959deba
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              3710976
Block count:              14823424
Reserved block count:     741171
Free blocks:              9053648
Free inodes:              3496903
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1020
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Thu Dec 23 18:40:09 2010
Last mount time:          Wed Jan  5 19:58:30 2011
Last write time:          Thu Dec 23 19:17:49 2010
Mount count:              14
Maximum mount count:      22
Last checked:             Thu Dec 23 18:40:09 2010
Check interval:           15552000 (6 months)
Next check after:         Tue Jun 21 18:40:09 2011
Lifetime writes:          26 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       1048613
Default directory hash:   half_md4
Directory Hash Seed:      ba897aff-68cb-46cb-bffd-4c4886c3c3c7
Journal backup:           inode blocks

# lsof | grep sda
jbd2/sda1  356       root  cwd       DIR       0,17      260          2 /
jbd2/sda1  356       root  rtd       DIR       0,17      260          2 /
jbd2/sda1  356       root  txt   unknown                                /proc/356/exe

```
fsck claims the partition is busy, but it's not even mounted ! Any idea what the fsck is going on and how to fix it ? Why can't I mount nor fsck ?!?

---

### Post by dargaud on 2011-01-09
Well, I ssh'ed the entire sda1 partition to another system, via "dd | ssh", then mounted it as loopback, fsck'ed it, and "ssh | dd" back. It worked even if it took a few hours. I couldn't easily remove the disk, so I did it this way.

---

