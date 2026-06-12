---
title: "Installation trouble--missing partition table?"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by teasum on 2006-07-27
I'm running XP and Ubuntu 6.06 on a Dell Inspiron 8600, and am now trying to add another flavor of Ubuntu to the mix.  When I partitioned my drive initially, I left 15gb for Windows, 7.5gb for Ubuntu, 7.5gb unpartitioned space (for future OS experimentation), and the rest as an extended partition (swap, /home, etc.).  

Now, for some reason, when trying to install either Edubuntu or Kubuntu, when I get to the partitioning part of the installation, my partitions do not show up.  All that is listed is my hard drive -- one 100gb chunk.  When I select 'manually edit partition table', there's my 100gb drive.  I don't want to proceed any further, of course, for fear that the installer might reformat everything.  

I can also verify this problem from an earlier attempt to restore grub to my MBR (long story short, I initially had a Windows Vista Beta installed on the 15gb partition, but decided to dump it since it didn't seem to 'play nice' with Ubuntu, and required a FAT32 to share data).  Since I installed XP, I had to restore grub, which I tried to do using the install cd.  This didn't work for the same reason mentioned above--no partition table showed up in the installer.  I ended up fixing grub through the terminal, but I'm now stuck with a system that works perfectly well, but I cannot install anything in my empty space (as I had planned to do). 

Edit: I tried running GParted from the live CD, and it shows the entire drive as 'unallocated space'. <!??!>  Also, under 'Harddisk Information:' it says 'DiskLabelType: unrecognized'.

Any ideas? Thanks.

---

### Post by teasum on 2006-07-27
Here is another post dealing with the same problem: [http://www.ubuntuforums.org/showthread.php?t=188532&page=3&highlight=Disklabel](http://www.ubuntuforums.org/showthread.php?t=188532&page=3&highlight=Disklabel).
It seems as though reinstalling XP may have screwed up my partition table.    I'm a bit of a newb here, so I'm not sure if this is the case or not, and I'm not 100% sure how to fix this.  Here's my fdisk output, in case anyone can help me out here: 

>    Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/hda2            1959        2937     7863817+  83  Linux
/dev/hda3            3917       12161    66227962+   5  Extended
/dev/hda4           10857       12161    10482381   83  Linux
/dev/hda5            3917        4133     1742989+  82  Linux swap / Solaris
/dev/hda6            4134        9355    41945683+  83  Linux

Thanks!

---

### Post by teasum on 2006-07-27
I've done some digging, but no luck thus far.  I do have some information I'd like to post on the off-chance someone out there has a solution that doesn't involve backing up my data, repartitioning and reinstalling evrything.

First, here is my output from 'mount', which shows that Ubuntu has no problem seeing and mounting my partitions:
> $ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-686/volatile type tmpfs (rw)
/dev/hda6 on /home type ext3 (rw,nosuid,nodev)
/dev/hda1 on /windows type ntfs (rw,nls=utf8,umask=0222)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda4 on /media/hda4 type ext3 (rw)

The disk management console in Windows XP reports my partitions incorrectly, however.  In the creenshot below, the last four partitions should all be part of an extended partition, and the 21.5gb free space is actually 11.5gb, which leads me to believe that the final 10gb partition is somehow overlapping the extended partition.

[IMG]https://mywebspace.wisc.edu/easum/web/XP-pro_partitions.jpg[/IMG]

This is confirmed by the error I get by running 'parted':
> $ sudo parted
Password:
GNU Parted 1.6.25.1
Copyright (C) 1998 - 2005 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

Using /dev/hda
(parted) print
Error: Can't have overlapping partitions.

And, finally, I installed and ran 'testdisk' (following the lead from this thread [http://www.ubuntuforums.org/showthread.php?t=209318&)](http://www.ubuntuforums.org/showthread.php?t=209318&)).  Here's what it told me after a thorough scan of my HD:
> Disk /dev/hda - 95396 MB - CHS 193821 16 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 31205  15 63   31455585
D Linux                31205  10  1 46808  15 63   15728202
D Linux                31387   2  1 46989  15 63   15727698
D Linux Swap           46808   8  1 49406  15 63    2619288
D FAT32 LBA            49406   5  1 111817  15 63   62910981 [DOCUMENTS]
L HPFS - NTFS          152203   2  1 193815  15 63   41945778



Structure: Ok.  Use arrow keys to change partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     ENTER: to continue

The next sceen suggested the following partition table:
> Disk /dev/hda - 95396 MB - CHS 193821 16 63

     Partition                  Start        End    Size in sectors
 1 E extended LBA         152203   1  1 193815  15 63   41945841
 5 L HPFS - NTFS          152203   2  1 193815  15 63   41945778

I didn't do anything at this point, since I was afraid I might lose access to everything.  

Now, I'm hoping that with all this information, someone out there might be able to help.  Is there a way to use testdisk to repair my partition table, or perhaps another tool might help?  Any help is appreciated.

---

