---
title: "Computer reboots without error msgs after kernel upgrade"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by Marcin Kraszewski on 2011-02-20
I really could use your help. My 10.10 installation failed after a recent kernel upgrade. At this point I have two kernel options on the grub menu: 2.6.35-25 and 2.6.35-24. When I select the newer version, my computer reboots without giving any error messages. With the older kernel version, I get the kernel panic error message (Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0).

I can post whatever information you need in order to get to the bottom of the problem. I have a RAID 1 on two 1 TB WD drives. When I install 10.10 from scratch, everything works fine. Things break after a security upgrade for the kernel is installed. It happened before and I re-installed the OS, but this time I have too much important stuff on my computer to loose it. Here is some system info to start with:

```

root@ubuntu:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a416

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      120072   964471808   83  Linux
/dev/sda2          120072      121601    12285953    5  Extended
/dev/sda5          120072      121601    12285952   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfbcffbcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a416

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      120072   964471808   83  Linux
/dev/sdc2          120072      121601    12285953    5  Extended
/dev/sdc5          120072      121601    12285952   82  Linux swap / Solaris

Disk /dev/dm-0: 1000.2 GB, 1000202178560 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a416

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1      120072   964471808   83  Linux
/dev/dm-0p2          120072      121601    12285953    5  Extended
/dev/dm-0p5          120072      121601    12285952   82  Linux swap / Solaris

Disk /dev/dm-1: 987.6 GB, 987619131392 bytes
255 heads, 63 sectors/track, 120071 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 12.6 GB, 12580814848 bytes
255 heads, 63 sectors/track, 1529 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table
root@ubuntu:~# 

```Here is an output from os-prober:

```
root@ubuntu:~# os-prober
ERROR: isw: Could not find disk /dev/sdb in the metadata
ERROR: isw: Could not find disk /dev/sdb in the metadata
/dev/mapper/isw_cagifdjehe_Volume01:Ubuntu 10.10 (10.10):Ubuntu:linux
root@ubuntu:~# 

```Please help. Thanks.

---

### Post by Marcin Kraszewski on 2011-02-20
Could someone, please, point me to a doc describing a booting sequence for ubuntu 10.10? A detailed technical document, which would help me figure out what happened with my ubuntu. I have been researching booting problems and kernel panic problems, but I haven't found anything which applies to my situation. I would really appreciate some pointers. Thanks.

---

### Post by deconstrained on 2011-02-20
If it can't mount root at boot time, there's something wrong with the kernel image, a.k.a. the initial ramdisk (or initramfs). It's a somewhat common problem; sometimes dpkg doesn't build one properly when you upgrade. [It's not that difficult to fix manually, and without reinstalling.](http://ubuntuforums.org/showthread.php?t=1691463) Since you have more than one hard drive, the problem could also be udev not assigning the same kernel names to each of the drives, in which case you need to use UUID's to identify block devices in /etc/fstab, or if you're feeling ambitious, [write some udev rules to make custom symlinks.](http://ubuntuforums.org/showthread.php?t=1626172)

I've actually run into this problem in ArchLinux as well as in Ubuntu, but it was user error on my part (improperly configured fstab).

---

### Post by Bucky Ball on 2011-02-20
If the new kernel works without a hitch, if I understand you correctly, what exactly is the problem? Are you just curious as to why 2.6.35-24 is no longer booting correctly? For what reason are you wanting to use the older kernel?

---

### Post by Marcin Kraszewski on 2011-02-21
Thank you very much for your reply. I will look at the links you sent me when I get home. When I reboot with Live CD, I cannot see my Linux drive under /media. Is that a showstopper for fixing this problem?
 
As for the two hard drives, they are mirrored in BIOS, so Ubuntu should see just one drive, shouldn't it?
 
Thanks again.
 
> **deconstrained said:**
> If it can't mount root at boot time, there's something wrong with the kernel image, a.k.a. the initial ramdisk (or initramfs). It's a somewhat common problem; sometimes dpkg doesn't build one properly when you upgrade. [It's not that difficult to fix manually, and without reinstalling.]("http://ubuntuforums.org/showthread.php?t=1691463") Since you have more than one hard drive, the problem could also be udev not assigning the same kernel names to each of the drives, in which case you need to use UUID's to identify block devices in /etc/fstab, or if you're feeling ambitious, [write some udev rules to make custom symlinks.]("http://ubuntuforums.org/showthread.php?t=1626172")
 
I've actually run into this problem in ArchLinux as well as in Ubuntu, but it was user error on my part (improperly configured fstab).

---

### Post by Marcin Kraszewski on 2011-02-21
G'day mate
 
Thank you very much for your reply. I was not clear in my description. When I select the first menu item, the 2.6.35-25 kernel, my computer reboots right away, without displaying any error messages. I guess that would indicate kernel panic, but severe enough that the OS cannot even display what is killing it. So at this point, I can only boot my machine using Live CD, and then I cannot see my Linux drive under /media. I will investigate the links sent by deconstrained and post my progress. Thanks again.
 
> **Bucky Ball said:**
> If the new kernel works without a hitch, if I understand you correctly, what exactly is the problem? Are you just curious as to why 2.6.35-24 is no longer booting correctly? For what reason are you wanting to use the older kernel?

---

### Post by deconstrained on 2011-02-21
> **Marcin Kraszewski said:**
> Thank you very much for your reply. I will look at the links you sent me when I get home. When I reboot with Live CD, I cannot see my Linux drive under /media. Is that a showstopper for fixing this problem?
 
As for the two hard drives, they are mirrored in BIOS, so Ubuntu should see just one drive, shouldn't it?
 
Thanks again.
Your hard drive won't be in /media. It won't even be mounted by default.

It should be a block device in /dev, i.e. /dev/sda. You can check which is which by running the "blkid" command as root. Then, run fsck on the Linux partition (just to be on the safe side), mount it wherever you want with the "mount" command (in my example I used /mnt), and off you go.

Also, what do you mean by "mirrored in BIOS"? Are you running a hardware RAID?

---

### Post by Marcin Kraszewski on 2011-02-21
Here is my updated fdisk -l output (after turning off an external hard drive):

```

root@ubuntu:/# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a416

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      120072   964471808   83  Linux
/dev/sda2          120072      121601    12285953    5  Extended
/dev/sda5          120072      121601    12285952   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a416

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      120072   964471808   83  Linux
/dev/sdb2          120072      121601    12285953    5  Extended
/dev/sdb5          120072      121601    12285952   82  Linux swap / Solaris

Disk /dev/dm-0: 1000.2 GB, 1000202178560 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a416

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1      120072   964471808   83  Linux
/dev/dm-0p2          120072      121601    12285953    5  Extended
/dev/dm-0p5          120072      121601    12285952   82  Linux swap / Solaris

Disk /dev/dm-1: 987.6 GB, 987619131392 bytes
255 heads, 63 sectors/track, 120071 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 12.6 GB, 12580814848 bytes
255 heads, 63 sectors/track, 1529 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table
root@ubuntu:/# 

```Here is the output of blkid:

```
root@ubuntu:/# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="a6071eb5-6fc6-45b3-babb-c1a2156278d7" TYPE="ext4" 
/dev/sda5: UUID="1cb0edc5-e434-425e-9486-a49c9b915a7c" TYPE="swap" 
/dev/sdb1: UUID="a6071eb5-6fc6-45b3-babb-c1a2156278d7" TYPE="ext4" 
/dev/sdb5: UUID="1cb0edc5-e434-425e-9486-a49c9b915a7c" TYPE="swap" 
/dev/mapper/isw_cagifdjehe_Volume01: UUID="a6071eb5-6fc6-45b3-babb-c1a2156278d7" TYPE="ext4" 
/dev/mapper/isw_cagifdjehe_Volume05: UUID="1cb0edc5-e434-425e-9486-a49c9b915a7c" TYPE="swap" 
root@ubuntu:/# 

```There is no information for /dev/sda2 and /dev/sdb2 which are listed by the fdisk command. Is that a problem?

And yes, I have hardware RAID configured in BIOS. Two 1 TB WD drives. That configuration works fine when 10.10 is installed from scratch.

When I run the fsck command, I get the following:

```

root@ubuntu:/# fsck.ext4 /dev/sda1
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
root@ubuntu:/# 

```mount command gives me this:

```

root@ubuntu:/etc# mount -t ext4 /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
root@ubuntu:/etc# 

```That does not look very promising, does it?

---

### Post by Marcin Kraszewski on 2011-02-21
New development. In the Places menu I can see three entries called "988 GB Filesystem". Looks like the first two are /dev/sda1 and /dev/sdb1 and I get the following message when clicking on them:

"Unable to mount 988 GB Filesystem"
"Error mounting: mount: /dev/sda1 already mounted or /media/a6071eb5-6fc6-45b3-babb-c1a2156278d7_busy"

However, when I clicked on the third one, I got my Linux partition mounted on /media as a6071eb5-6fc6-45b3-babb-c1a2156278d7. So now I can access my files. Is there anything in there which would be useful in this investigation? Thank you very much.

---

### Post by Marcin Kraszewski on 2011-02-21
One more thing. I ran boot_info_script055.sh and its output is in the attached file.

---

### Post by deconstrained on 2011-02-21
**EDIT:** GOT IT: your array is getting mapped to /dev/dm-0. Your root filesystem appears to be on /dev/dm-0p1, so that is what you should mount and chroot into before rebuilding the initramfs.

[s]Ubuntu on the livedisk might have auto-mounted it without your asking it to...in which case you'll need to open up a Nautilus window and hit the eject button on the relevant filesystems over in the left panel.

This also might help:
```
df
```
That should tell you which block devices are mounted where, and how much free space they have left on them.

[color=red]Instinct tells me that the array should behave as a single hard drive/block device, as it's hardware RAID.[/color][/s]

---

### Post by Bucky Ball on 2011-02-21
I would suggest unmounting them:

```
sudo umount /dev/sda1
```

... or whatever they happen to be then rebooting. Doesn't look like it has shut down properly (thus the 'busy' at the end of the line). Might fix it.

---

### Post by deconstrained on 2011-02-21
> **Bucky Ball said:**
> I would suggest unmounting them:

```
sudo umount /dev/sda1
```
/dev/sda1 is a part of his hardware RAID, which is why the kernel keeps saying it's busy. I just figured this out :p

---

### Post by Marcin Kraszewski on 2011-02-21
> **deconstrained said:**
> **EDIT:** GOT IT: your array is getting mapped to /dev/dm-0. Your root filesystem appears to be on /dev/dm-0p1, so that is what you should mount and chroot into before rebuilding the initramfs.

[s]Ubuntu on the livedisk might have auto-mounted it without your asking it to...in which case you'll need to open up a Nautilus window and hit the eject button on the relevant filesystems over in the left panel.

This also might help:
```
df
```That should tell you which block devices are mounted where, and how much free space they have left on them.

[COLOR=red]Instinct tells me that the array should behave as a single hard drive/block device, as it's hardware RAID.[/COLOR][/s]

I umounted the Linux partition from /media and here is mount -l output:

```

root@ubuntu:~# mount -l
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime) [Ubuntu 10.10 i386]
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
root@ubuntu:~# 

```When I try to mount /dev/dm-0p1, it doesn't work:

```

root@ubuntu:/# mount /dev/dm-0p1 /mnt
mount: special device /dev/dm-0p1 does not exist
root@ubuntu:/#

```I then tried to use UUID with the mount command:
```

root@ubuntu:~# mount -U a6071eb5-6fc6-45b3-babb-c1a2156278d7 /mnt
root@ubuntu:~#

```That worked:

```

root@ubuntu:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   1547724    132072   1415652   9% /
none                   1541812       284   1541528   1% /dev
/dev/sr0                709792    709792         0 100% /cdrom
/dev/loop0              676480    676480         0 100% /rofs
none                   1547724       228   1547496   1% /dev/shm
tmpfs                  1547724       160   1547564   1% /tmp
none                   1547724       116   1547608   1% /var/run
none                   1547724         4   1547720   1% /var/lock
/dev/mapper/isw_cagifdjehe_Volume01
                     949337220  87179244 813934388  10% /mnt
root@ubuntu:~#

```There is that strange looking partition: /dev/mapper/isw_cagifdjehe_Volume01

Would you be so kind and tell me what commands from the "Ubuntu won't boot" post should I now use on my system before I chroot. There are several more mount commands I am not sure about. Thanks a lot, deconstrained.

---

### Post by deconstrained on 2011-02-21
> **Marcin Kraszewski]When I try to mount /dev/dm-0p1, it doesn't work:
```
root@ubuntu:/# mount /dev/dm-0p1 /mnt
mount: special device /dev/dm-0p1 does not exist
root@ubuntu:/#
```[/quote]
**Then what was this all about? ----**
[quote=Marcin Kraszewski]
```

Disk /dev/dm-0: 1000.2 GB, 1000202178560 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a416

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1      120072   964471808   83  Linux
/dev/dm-0p2          120072      121601    12285953    5  Extended
/dev/dm-0p5          120072      121601    12285952   82  Linux swap / Solaris

```[/quote]


[QUOTE=Marcin Kraszewski said:**
> There is that strange looking partition: /dev/mapper/isw_cagifdjehe_Volume01
Oh shiiiii-----
???
Your guess is as good as mine. Since I have no experience with hardware RAID (I prefer mdadm/software RAID), I have no idea what this could be the result of.

My next guess would be rebooting (to the live disk again), inserting the 'raid1' module into the kernel and killing mdadm if by some chance it's running.

Anyway, to get to repairing your initramfs you first need to figure out which block device is your root partition, and then mount it. Since you're using hardware RAID, the behavior of the array may actually be vendor-dependent, so it'll be up to you and the documentation on Linux compatability that the manufacturer supplies (if any) to determine how to get it working again in Linux (it may or may not require some special kernel module...)

I wish you luck!

---

