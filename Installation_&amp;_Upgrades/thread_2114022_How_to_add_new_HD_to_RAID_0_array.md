---
title: "How to add new HD to RAID 0 array"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by Chromatin on 2013-02-08
Hi,
I have a computer that I use as an Rsyn server to back up my NAS for the last year or two. I originally installed 4 hard drives into it, one on which I installed the Ubuntu 11.10 O/S and the other 3 for storing the backup data. The 3 drives for data I configured in RAID 0, and overlayed a single Logical Volume (using LVM) over top of it. Now I would like to add an additional hard drive and expand the RAID 0 and LVM to use all the space on the new drive, adding the space to the existing LVM. I've added the hard drive to the computer, and it is recognized by the 0/S as an empty drive, but am I not sure of the exact commands and their order to complete this task. I would rather not break the array, if possible. I'm basically a newbie to Linux, but can usually muddle my way through with written instructions and apply them fairly well.

---

### Post by MAFoElffen on 2013-02-09
Not positive as I avoid RAID0 and rather favor RAID5 and RAID50 instead. RAID0 has less "checks" in it than a single drive.

But 
> 
From 2.6.35, the Linux Kernel was able to convert a RAID0 in to a RAID4 or RAID5. mdadm used this functionality and the ability to add devices to a RAID4 to allow devices to be added to a RAID0. When requested to do this, mdadm will convert the RAID0 to a RAID4, add the necessary disks and make the reshape happen, and then convert the RAID4 back to RAID0.

Prior to linux 3.x.x the procedure to perform this --grow was as follows:

```
 mdadm --grow /dev/md0 --raid-devices=3 --add /dev/sdc2
```
After Linux 3.x.x, about a year ago, there was an upstream Linux Kernel Bug filed from Arch Linux that this had stopped working.

I know the current mdamd man page for Ubuuntu version 12.04 through versions 13.04 says:
> 
Grow   
Grow (or shrink) an array, or otherwise reshape it in some way. Currently supported growth options including changing the active size of component devices and changing the number of active devices in Linear and RAID levels 0/1/4/5/6, changing the RAID level between 0, 1, 5, and 6, and between 0 and 10, changing the chunk  size  and  layout  for RAID 0,4,5,6, as well as adding or removing a write-intent bitmap.
Which an example would be:
```

# mdadm [mode] <raiddevice> [options] <component-devices>
# Example:
mdadm --grow /dev/md0 --level=0 --raid-devices=3 --add /dev/sdc1
```
Note that when I look at Ubuntu versions 10.04 LTS and 11.10, those versions do not support RAID0 with the --grow mode.

So, at least it "looks" like it is working again for RAID0... but like I said, I don't use RAID0, so I haven't tried it personally.

---

### Post by darkod on 2013-02-09
Like Mike, I also don't use raid0, but a quick look in the man page seem to say it's not possible to reshare raid0 array.

Also, I hope you are aware that raid0 array doesn't provide any redundancy, so the more disks you have more chance of a single failure and in that case all the data is gone. Depending how important this machine is to you, and on your backup policy, you might be happy running raid0. I hope you know the consequences.

Anyway, from the man mdadm page:
> -n, --raid-devices=

Specify the number of active devices in the array. This, plus the number of spare devices (see below) must equal the number of component-devices (including "missing" devices) that are listed on the command line for --create. Setting a value of 1 is probably a mistake and so requires that --force be specified first. A value of 1 will then be allowed for linear, multipath, RAID0 and RAID1. It is never allowed for RAID4, RAID5 or RAID6.
[COLOR="Red"]This number can only be changed using --grow for RAID1, RAID4, RAID5 and RAID6 arrays[/COLOR], and only on kernels which provide the necessary support.

Anyway, the command that Mike posted should be little different I think. You already have 3 raid devices and you want to grow to 4, so it would be like:
```
sudo --manage /dev/md0 --add /dev/sdXY #(add the new disk to the array if not already added)
sudo mdadm --grow /dev/md0 --level=0 --raid-devices=4 --back-file=/path not on the raid/filename
```

But as mentioned above, I don't think this can work for raid0 according to the man page.

---

### Post by darkod on 2013-02-09
Since you have LVM, one thing you can do is create one single LVM type partition on the new disk, and add it as physical device to the existing LVM. That way you can grow the storage easily but that disk will not be part of the raid. Since it's raid0 I don't think it matters if it's in the raid or not anyway. If any disk fails, you lose all.

It will probably be little faster if it's in the raid0 array since it writes to all disks at the same time in parallel, but I don't think you can grow this array as mentioned above.

---

### Post by Chromatin on 2013-02-09
Thanks for the replies to my post.  It doesn't sound possible? or at least not easy to add a drive to RAID 0.  In retrospect, I don't think I should have chosen RAID 0 (or any RAID for that matter) to form the large volume spanning the 3 data drives.  I fully understand the disadvantages of RAID 0 on my server, but in my context of usage (all I'm using the linux server to do is back up a NAS that already uses RAID 5).  All the data exists in duplicate at all times, so I felt comfortable using RAID 0.  Currently my plan is to dispense with the data on the 3 data  drives, add the new drive, and then combine the 4 drives into one large volume.  I'll then regenerate my full backup from scratch.  Again, the risk exists of data loss with one drive failure, but at least adding additional drives won't be a hassle.:)

---

