---
title: "Solved: Gutsy and Hardy kernels do not boot with my RAID setup"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Vermind on 2008-04-26
Hello,
When I upgraded my desktop to Gutsy, the kernel did not boot. I had the old kernel as a backup, so I didn't care much. Now, when I installed Hardy and that kernel did not boot, I was sure something was wrong. I looked through a few bug reports on the kernel not booting, such as [Boot failure: hard disk does not exist (Hardy beta)]("http://https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/208222"). They didn't help me.

I am using Hardy for amd64, with two SATA hard drives, set up as two software RAID (dmraid) arrays, one mirrored for boot, one mirrored for root. 
My /etc/raidtab looks like this:

```
# / (reiserfs)
raiddev                 /dev/md1
raid-level              1
nr-raid-disks           2
nr-spare-disks          0
chunk-size              32
persistent-superblock   1
device                  /dev/sda6
raid-disk             0
device                  /dev/sdb6
raid-disk               1

# /boot
raiddev                 /dev/md0
raid-level              1
nr-raid-disks           2
nr-spare-disks          0
chunk-size              32
persistent-superblock   1
device                  /dev/sda1
raid-disk             0
device                  /dev/sdb1
raid-disk               1

```

And my /etc/mdadm/mdadm.conf
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
#ARRAY /dev/md0 level=raid1 num-devices=2 UUID=173419ac:2bbdf72a:e368bf24:bd0fce41
#ARRAY /dev/md1 level=raid1 num-devices=2 UUID=78d58fad:27e40269:e368bf24:bd0fce41

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=173419ac:2bbdf72a:e368bf24:bd0fce41
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=78d58fad:27e40269:e368bf24:bd0fce41

```

Solution: after I uncommented the ARRAY lines in mdadm.conf, Hardy boots. Apparently it either does not use raidtab for detecting my RAID arrays, or does not scan the partitions for MD superblocks properly.

If Your > feisty kernel does not boot, and You don't have ARRAY lines in mdadm.conf:
obtain the information for creating the lines with
```
sudo mdadm -D /dev/md0
```.
Then the format of the array line is
```
ARRAY /dev/mdx level=raidy num-devices=z UUID=w
```.
Where x is Your /dev/md number, y is the raid level as given by the command above, z is the number of disks in the array, and w is the UUID as given by the command above.

I did not find help for this problem, and tried this on a hunch. I hope it helps someone.

Additional keywords: waiting for root filesystem, /dev/md0: no such file or directory, dropping to a shell (initramfs), kernel 2.6.22-16, 2.6.24-16.

---

