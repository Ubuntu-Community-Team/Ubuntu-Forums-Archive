---
title: "Raid Drive Replacement"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by tltemple on 2012-05-25
I would like to start a serious discussion on repairing RAID drives on Ubuntu systems.

I have spent quite a bit of time over the last several weeks trying to install and prove out RAID drives on a new Ubuntu 12.04 Server installation.  I am becoming frustrated and disappointed at the lack of definitive knowledge and answers to RAID issues on Ubuntu and Linux in general.

My situation seems very simple to me:  I want to load up a simple Ubuntu file server with RAID 1 configured hard disks.  **I want to fail a drive on purpose, then replace that drive, and get the system back to the exact same state as it was prior to the drive failing.**  If I can't do this, and record the exact steps required to do so, I don't want to waste any more time with RAID drives, because why use them if one can't prove them to be (easily) recoverable?

With that said, I have come very close to my goal, but I have run in to small, but almost impossible issues trying to get this done.  I will review what I have done:

1) Configure system with 4 physical hard drives.  2 drives for the OS, 2 drives for data.  The OS drives are Raid 1, 4 partitions, 4 raid devices (md0 through md3).  The data drives are one large partition, 1 raid device (md4).  The data drive may get more complicated later, once I prove I can recover it, but for now one large partition, one raid array.

2) md4 (data drive) is mounted as /media/data.
3) configure Samba with a share of /media/data
4) connect windows client, copy some data to the /media/data share.

Now for the trial run of the drive replacement:

5) fail /dev/sdc1 on the md4 device
  (sudo mdadm --manage /dev/md4 --fail /dev/sdc1
This effectively puts md4 into a failed hard drive state.
6) Remove /dev/sdc1 from the array
  (sudo mdadm --manage /dev/md4 --remove /dev/sdc1
7) Shut down the system, take out sdc, replace it with another drive.
8 ) Partition the new drive
  (sudo sfdisk -d /dev/sdd | sfdisk /dev/sdc)
  **** This is a solution proposed a number of places for copying the partition from one drive to another.  It doesn't seem to work on Ubuntu.
8 ) Partition the new drive
  (sudo fdisk /dev/sdc)
  (c)
  (u)
  (n) - new partition
  (p) - primary partition
  enter - accept default start location
  enter - accept default end location
  (w) - write partition table

**************************************
At this point, I have some questions
Q1) is it necessary or desirable to format the new drive here?
Q2) should the partition be marked as something other than a plain old linux partition?  If so, How?
**************************************

9) Format the drive?

10) Add the drive back to the array
  (sudo mdadm --manage /dev/md4 --add /dev/sdc1

11) check the status of the raid devices
  (sudo cat /proc/mdstat)

This shows the raid device rebuilding.

This process (at least in this case) went on and rebuilt the raid array, **BUT**, **it marked the new drive as a spare drive in the array.**

**This proved to be virtually impossible for me to change.  Maybe I shouldn't be concerned with the new drive being marked a spare, but it bothers me.  I was basically not able to overcome this issue.**  Everything was functioning, and I didn't lose any data, but I was not back where I started.  I found a number of posts where this specific issue was discussed, but no definitive answer as to how to fix it.


I have tried this several more times with other little problems:

In some cases, the rebuild goes very slowly, and I get all kinds of errors reported during the process.  I am associating this with whether or not I format (create a file system) on the new drive before adding it to the array.  I am still not sure (Q1 above) whether the drive needs to be formatted prior to adding it to the raid array.

In other cases, the system seems to grab the drive as soon as it sees the partition created.  It adds it to the raid array and starts rebuilding it before I have the chance of stopping it.

In other cases, the system hangs on to the drive and says the drive is busy, and it won't let me partition it.

In other cases, I can't remove a partition from an array.

If you have lasted this long, maybe you can help.

I would really like to work through this issue, and move forward with confidence configuring this server with raid arrays.  I am planning on adding another server to this installation when this one is done.

I am not after guesses to these issues.  If you don't have definitive information, please don't offer it.  I have scoured many forum posts that are full of suggestions and guesses.  If I have to, I will get the source code for the raid software and dig through it myself to find the answers, but I would rather not spend that kind of effort.

If there is a better place to have this discussion, please point me that direction.

Thanks,

Tom

---

### Post by darkod on 2012-05-25
I have never tried this, but because I am interested in raid too I have this link:
[http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

Basically, you are following the correct steps. I would comment something about step 8 with my limited knowledge:

Don't use fdisk for any partition creation. It seems it's buggy. I have seen fdisk creating partition with end sector outside the disk, which made real problem in the array later.
If working with msdos table, try using cfdisk. cfdisk can also help you about the partition type which should be Linux RAID Autodetect, I believe it's code 'fd'. You can change types even on existing partitions with cfdisk, not only while creating them.

If the copy of the partition table with sfdisk failed (which it shouldn't), I would say you need to mark the partition as fd manually since you created it manually.
I wouldn't expect you need to create a FS because the raid sync should take care of that. After all, it's the /dev/mdX device that carries the FS, not the /dev/sdXY,

---

### Post by tltemple on 2012-05-25
That link is a good starting point.  I think there are some small details missing.

I am not aware of cfdisk, I will do some research on it.

Can someone explain the significance of the partition type?  Is it important to be set to raid autodetect?  What are the implications of a partition marked raid autodetect.

You believe that sfdisk should work.  I will study that to see what might be wrong.  I have tried it many times without success.  It would be good if it worked, because it would be more error free than manually partitioning the replacement drive.

---

### Post by tltemple on 2012-05-30
The issue with sfdisk is the need for sudo on both sides of the |.

sudo sfdisk -d /dev/sdc | sudo sfdisk /dev/sdd

This works.  Probably obvious to more experienced users, but it eluded me until now.

---

### Post by tltemple on 2012-05-30
Another useful piece of information is to boot with a live disk and switch to the command prompt and do some of the drive maintenance there.  the raid stuff is not running, so it doesn't get in the way of some operations.

Boot from live CD
CTRL-ALT-F1 to shut down the gui
do anything you want from the command prompt.

---

### Post by tltemple on 2012-06-01
I have found that much of my trouble comes from stray information on the hard drives.  I have been replacing drives with other drives that have been taken out of the system during earlier experiments.  Apparently there is superblock information somewhere on the drives that gets detected once the drive is partitioned.  In many cases, when I partition the replacement drive, mdstat will show that the drive has been picked up as a spare, or some part of an array.

The way around this is to "shred" the drive:
sudo shred -v -n1 /dev/sd*

This takes quite a while on large drives, but it cures a lot of ills when trying to add the drive into a system as a replacement.

When starting with a totally clean drive, I experience much less confusion.

For whatever reason, if the drive is not cleared off, re-partitioning the drive does not always get rid of information that is detected by the raid software.  This has caused me much frustration.

---

### Post by darkod on 2012-06-01
If you are only after the mdadm superblock, a much faster way is:
sudo mdadm --zero-superblock /dev/sdX

On the other hand, a fakeraid / hardware raid meta data is cleared with:
sudo dmraid -E -r /dev/sdX

---

### Post by tltemple on 2012-06-01
Some more experimenting.

1) Assembled the array and put some files on it, mounted, and used as samba share to windows clients.

2) Shut down, removed one drive.
3) Restart - array reports as inactive.
4) Shut down, replace drive, remove other drive.
5) restart - array reports as inactive.
6) shut down, put both drives back in.
7) restart - all OK.
8) add array info to /etc/mdadm/mdadm.conf
    sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
9) edit mdadm.conf to comment out old versions of the array(s).
10) remove a drive, restart the system.
11) array fails to assemble and start again.  Inactive.
12) try "sudo mdadm --assemble /dev/md4".  Complains about metadata format 00.90 not recognized, ignored.
13) try "sudo mdadm --assemble /dev/md4 /dev/sdc1".  Array builds, but says can't start without all drives, try --run to force.
14) try "sudo mdadm --assemble --run /dev/md4 /dev/sdc1"  This assembles the array and runs it.  Clients are able to see the data from the one drive that is running.
15) Edit /etc/mdadm/mdadm.conf and change "metadata=00.90" to "metadata=0.90"
16) shut down
17) restart.  Now the array builds and starts.  One drive is not there, system emails me that the array is degraded.


So, the points here are:

1) An array will build without being in the mdadm.conf file, so long as all drives are present and good.
2) An array will come up as inactive if it is not in the mdadm.conf file, and one of the drives is missing.
3) The array can be forced to assemble and run, even if not in the mdadm.conf file, if you know how to assemble it, and use --run.
4) "sudo mdadm --detail --scan" shows "metadata=00.90", which is a problem when saved in the mdadm.conf file.  It must be changed to "0.90" for the metadata format to be recognized on startup.
5) a 2 drive raid1 array will assemble and run from the information in the mdadm.conf file, even if 1 drive is missing.
6) metadata=00.90 is not the same to the parser as metadata=0.90

---

### Post by tltemple on 2012-06-01
Noticed a setting in mdadm.conf:

#by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

I want to experiment with this to see if changing it helps reduce confusion when replacing drives.

---

### Post by tltemple on 2012-06-01
> **darkod said:**
> If you are only after the mdadm superblock, a much faster way is:
sudo mdadm --zero-superblock /dev/sdX

On the other hand, a fakeraid / hardware raid meta data is cleared with:
sudo dmraid -E -r /dev/sdX

I'm not sure what really causes the drive to automatically go back  to an array, but usually there is no mdadm superblock there.  I presume that some information is in some backup copy of the superblock that causes the problem.

I found that starting with a known "shreded" drive seems to clear up a lot of issues.  I wish I could determine absolutely what needs to be cleared, and how to clear it.

My raid is software, so I assume that the dmraid stuff is not needed.

---

