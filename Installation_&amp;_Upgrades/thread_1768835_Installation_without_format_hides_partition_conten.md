---
title: "Installation without format hides partition contents"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by tchaithonov on 2011-05-27
Hi All,

I have been using a kubuntu 10.10 till last week when it could not complete do-release-upgrade, so I downloaded kubuntu 11.04, specifying that I did not want my /home partition to be formatted, and went ahead with the installation.  I used ext4 under 10.10 and selected ext4 again for 11.04, yet when I first rebooted after the completion of the installation, I could not find any of my files in that partition (except a newly created user home folder with the same user name as the old one).  But when I looked at du -h, it's 92% full. I know I have set the mount point correctly, so it shouldn't be a fstab problem.  Does anyone know what I should do to recover the files?  Would you please let me know?  Many thanks!

Tchaithonov

---

### Post by ajgreeny on 2011-05-27
> **tchaithonov said:**
> Hi All,

I have been using a kubuntu 10.10 till last week when it could not complete do-release-upgrade, so I downloaded kubuntu 11.04, specifying that I did not want my /home partition to be formatted, and went ahead with the installation.  I used ext4 under 10.10 and selected ext4 again for 11.04, yet when I first rebooted after the completion of the installation, I could not find any of my files in that partition (except a newly created user home folder with the same user name as the old one).  But when I looked at du -h, it's 92% full. I know I have set the mount point correctly, so it shouldn't be a fstab problem.  Does anyone know what I should do to recover the files?  Would you please let me know?  Many thanks!

Tchaithonov
I am a bit unsure exactly what you did, but please run the command ```
sudo fdisk -l
``` and it might be a bit clearer.

---

### Post by tchaithonov on 2011-05-31
Hi,

Sorry for the late reply.  Here's the information you are looking for.

```
$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008de9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9764864   83  Linux
/dev/sda2            1216       39148   304686081    5  Extended
/dev/sda3   *       39148       39161      102400    7  HPFS/NTFS
/dev/sda4           39161       60802   173830144    7  HPFS/NTFS
/dev/sda5            1216       37689   292967424   83  Linux
/dev/sda6           37689       39148    11717632   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00009de3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38244   307194898+   5  Extended
/dev/sdb2           38245       76490   307200000    7  HPFS/NTFS
/dev/sdb3           76491      121600   362346075    7  HPFS/NTFS
/dev/sdb5               1       38244   307194867   83  Linux

Disk /dev/dm-0: 12.0 GB, 11998855168 bytes
255 heads, 63 sectors/track, 1458 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaaef6884

Disk /dev/dm-0 doesn't contain a valid partition table

```

My problem is with /dev/sdb5.  I am not quite sure why I couldn't access the files originally stored in this partition.  Would you please let me know?  Thanks.

---

### Post by SeijiSensei on 2011-05-31
Have you tried mounting it manually from the command line?  If so, what errors are reported?

Have you run fsck against the filesystem to correct any errors that might be causing the OS not to mount that partition?

---

### Post by srs5694 on 2011-05-31
I have insufficient information to be sure, but my suspicion is that /dev/sdb5 is not mounted to /home. Therefore, you wouldn't see the partition's contents in /home, where you'd expect them to be. To test my hypothesis, do this:

```

df -h

```

If I'm wrong, the result will include a line specifying that /dev/sdb5 is mounted at /home, like this:

```

/dev/sdb5      100G   80G   21G  80% /home

```

If my hypothesis is correct, then no such line will be present. If so, you can fix it by adding a suitable entry to /etc/fstab:

```

/dev/sdb5      /home    ext4         noatime        0 2

```

If the partition uses something other than ext4fs, you'll need to adjust the filesystem type code. You can also tweak various details as you see fit. Changing "/dev/sdb5" to a UUID reference is probably desirable, for instance. Once you make this change, reboot and it will reappear; however, once you reboot you'll lose access to anything you've stored in /home since the upgrade. (There are ways to get it back if necessary; I've just specified the quick way to do this on the assumption that you have no new files.)

---

### Post by tchaithonov on 2011-05-31
I tried to mount the drive manually, and this is what happens:

```
/dev/sdb5             289G  251G   24G  92% /home/xyz/test

```

I just discovered that it might be because the partition was encrypted ... silly me, now I only need to find out how to mount that partition correctly.  Thanks everyone!

---

### Post by srs5694 on 2011-05-31
If I was right and the partition was not mounted after you installed, then that does not mean that it was encrypted; it just means that you didn't tell the installer where to mount it when you did your installation. (Or if you *did* provide this information to the installer, the installer has a bug.)

If you can read and write the files in the partition after you've mounted it manually, then creating an /etc/fstab entry, as I noted in my earlier post, will fix the problem, with the caveats I specified in my earlier post.

---

