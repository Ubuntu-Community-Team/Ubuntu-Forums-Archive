---
title: "NTFS partition corrupt/destroyed?"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by Old Pink on 2006-09-24
Hi, 

As many of you will know from my previous threads, GRUB problems caused me to fresh install ubuntu. The fresh install involved simply formatting my current ubuntu partition along with the 500mb swap. 

All was fine, install went well, Ubuntu booted fine. (although XP wasn't listed in GRUB) - thought an update would fix that, so, I got wireless drivers off ubuntuuser and installed all available updates. 

Still no XP. I edited fstab and tried to mount the NTFS partition, but alas, huge problem. 

> matt@matt-desktop:~$ sudo mount -a
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or soI did "dmesg | tail" and:

> [17184281.032000] NTFS-fs warning (device hda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17184281.032000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17184281.032000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17184281.032000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
[17184287.308000] NTFS-fs warning (device hda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17184287.308000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17184287.308000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17184287.308000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume."Not an NTFS volume"?  Can it change during installation?  XP recovery disk claims that the partition is beyond repair and cannot be fixed, but XP is usually wrong, so I'm hoping theres some hope of retreiving any important files. 

GParted screenshot attached, seems to suggest hda1 is empty, whereas really it's around 20GB full. The "discs manager" screenshot attached gives me the option to enable the disk, but when I do so, the window just refreshes itself? 

I'd love to get the disk fixed up, but it's no *major* loss if it's lost.

---

### Post by Sef on 2006-09-24
Please do the following command and post the results here.  It will tell you (and us) what your partions are.

sudo fdisck -l

---

### Post by Old Pink on 2006-09-24
> 
matt@matt-desktop:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        8709    69955011    7  HPFS/NTFS
/dev/hda2            8710        9900     9566707+  83  Linux
/dev/hda3            9901        9964      514080   82  Linux swap / Solaris

Disk /dev/sda: 524 MB, 524288000 bytes
32 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1000      511983+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(998, 31, 32) logical=(999, 31, 31)
 

Also, attached the screenshots I forgot in post 1.

---

### Post by Old Pink on 2006-09-24
I'm on the verge of just deleting the NTFS partition... I see no way of retreiving it. Unless anyone has a good idea? :)

---

### Post by Old Pink on 2006-09-24
... anyone at all?

---

### Post by deeptingler on 2006-09-24
I would be real interested in the solution to this also Matt.H as I was in the same situation a few weeks ago - I ended up wiping the drive as I used a discrescue program which didnt appear to find anything on the partition - but only used Kubuntu for around a couple of months now so still fairly new myself (sigh)

---

### Post by Old Pink on 2006-09-24
So it's not *that* uncommon? Interesting...

---

### Post by halozero on 2006-10-03
Hi, my first post on an open-source forum!

I have the same problem right now, and I seem to have found a way into that blasted broken NTFS partition.

Go into System>Administration>Disks, select your hard disk in question, and under the Partitions tab, you'll see all the partitions in the disks, both visible and hidden, listed in the right pane. Check the location of the NTFS partition in the Linux filesystem (mine is in /tmp/disks-conf-sda5). You can access the partition when you use the file manager typing the local address into the location bar.

Do note that this will allow you to read-only access, even if you are logged in as root. You can't change permissions either, but as far as saving your data is concerned, this should be good enough. Now all I need is an external drive to backup about 15GB of data.

As I've said, this is my first post to any Linux forum, so bear with me if I sound a bit Windows-ish. And I hope I'm not too late to help; last post was a week ago...

---

### Post by wkulecz on 2006-10-03
Before doing anything radical or irreversable, get your hands on a Knoppix 5.0.1 DVD (CD might work, but I used the DVD version) and boot it.  It recognized Vista RC1 NTFS partition and I offloaded a few of the new *.wmv sample videos on a USB drive to see if they'd play on older systems (short answer, media player downloaded a codec but playback was unusable on old machines).

--wally.

---

### Post by GreenMarine on 2006-10-03
This is very useful for analyzing NTFS partition issues. I recommend reading the entire thing before making any changes to an NTFS partition:

[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)

Now some hints:

- I don't recommend you use the copy of GParted that comes with Ubuntu's current LiveCD. This might be iffy advice, but I've seen it make mistakes in resizing or adjusting NTFS partitions. In particular, I've seen it reduce the size of a partition, but not the NTFS, resulting in a windows that won't boot (because the NTFS is "longer" than the medium.)

- Instead, modify the partition manually using ntfsresize, which is available on the livecd. You can do this from the terminal, in root, by invoking 'sudo su' and then 'ntfsresize -h' for a menu. The link above has instructions on how to manually adjust the size of the NTFS, or how to test your file system for problems. This tool and site may also help you reveal what's wrong with your file system or the partition that hosts it.

- If you make changes to a partition size or create a new partition, I always recommend rebooting before formatting. Sometimes the kernel isn't properly notified of the change and you could accidentally format the wrong location on the drive as a result. If you reboot and everything looks good in fdisk or GParted, you should be safe to format and install.

- God save you if you're using a software RAID0. I'm in the process of adapting this method: [http://www.ubuntuforums.org/showthread.php?t=86219](http://www.ubuntuforums.org/showthread.php?t=86219) to Dapper Drake without losing my NTFS data. It's a little hairy.

---

