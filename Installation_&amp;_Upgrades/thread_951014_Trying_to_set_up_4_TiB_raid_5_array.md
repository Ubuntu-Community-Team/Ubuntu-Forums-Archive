---
title: "Trying to set up 4 TiB raid 5 array"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by jgold on 2008-10-17
I'm stumped.  I was able to get a 4 TiB array drive working in June and was happy with it.  Then last week, my system crashed while performing a large copy and when I rebooted, the array status gave me an error message that there was no valid superblock.

I was still able to read the data so I backed everything up onto a bunch of removable drives.  Now I just want to rebuild the array but can't seem to get it to work.

I've found various instructions.  First, I stopped the existing array;

[FONT="Courier New"]sudo mdadm --stop /dev/md0[/FONT]

Next, I zeroed out the superblocks of the member drives;

[FONT="Courier New"]
sudo mdadm --zero-superblock /dev/sdb1
sudo mdadm --zero-superblock /dev/sdc1
sudo mdadm --zero-superblock /dev/sdd1
sudo mdadm --zero-superblock /dev/sdf1
sudo mdadm --zero-superblock /dev/sdg1
sudo mdadm --zero-superblock /dev/sdh1
sudo mdadm --zero-superblock /dev/sdi1
[/FONT]

Next, using gparted, I formatted each device with the ext2 file system and set the flags to raid.

Finally, I tried to recreate the array;

[FONT="Courier New"]sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=7 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1 --auto-md[/FONT]

That appears to work and the array initializes but when you reboot, the array is broken again with the same invalid superblock error message.

I deleted the partitions off the array again and wrote a new msdos disk label.  Now when I try to re-create the partion, in gparted, it shows all the proper information on the creation screen but the partion that's actually created is only 95.8 GiB.

I've spent two days trying everything I could find in the Internet to no avail.  Does anyone have any idea what I need to do to get this working?

Ubuntu 8.04 64 bit.  2gb ram, quad core CPU and non-functioning set of sata drives.

---

### Post by jgold on 2008-10-21
Well, I've spent a lot more time trying to figure out the problem with very little progress.  I now think that the main problem is in gparted. I don't think it understands software raid devices.

I first tried everything I could try or think of to get rid of all remains of the old array.  I even pulled the drives out of the Ubuntu box and plugged them into a Windows machine so that I could wipe the disks clean.  )You could probably do that under Linux but I don't know how).  I then deleted all files and items that I could find that related to the disk array.  That includes the /dev/md0 device and other things.  When I was done, I could finally boot the system without /dev/md0 starting up.

After all that, I used gparted to partition each of the devices with an ext2 file system and set the flags to raid.  I had to reboot multiple times checking the drives partition status and re-creating the partion on some drives because the first time just didn't take.

After I got all the partitions working, I was able to create the raid array again using the mdadm --create command.

There are still some strange things going on.  When you create the array, gparted shows it as having a single partition which it names /dev/md0p1.  That partition shows that it has an ext3 file system but it as the exclamation symbol next to it.   If you right click and pull up the information, it says this;

[FONT="Courier New"]e2lable: No such file or directory while trying to open /dev/md0p1
Couldn't find valid file system superblock
Couldn't find valid file system superblock.

dumpe2fs 1.40.8 (13-Mar-2008)
dumpe2fs: No such file or directory while trying to open /dev/md0p1

Unable to read the contents of this filesystem!
Because of this some operations my be unavailable.[/FONT]


I am unable to mount the /dev/md0p1 partition but I can mount /dev/md0.  

This is the opposite of the normal device/partition relationship. If I have a SATA drive at /dev/sdb, I can't mount it directly.  I have to create partition /dev/sdb1 and mount that.  It's confusing!

Now that the raid array is created and mounted, I can see the drive in Nautilus where I mounted it.  If I right-click and choose properties, it shows that it has 4 TB of disk space available.  In gparted, all of the member drives show and unknown file system on the partition which I would expect.

So, to summarize, I seem to have a working file system on /dev/md0 that I mounted.  gparted shows a partition on /dev/md0 called /dev/md0p1 with a file system of ext3 but with an error on it.

I think that Linux really needs some work on the software raid subsystem.  Either that or gparted needs some work so that it understands mdadm structures.

I wish the ZFS-FUSE project was farther along.  I was able to install it and get an array configured and even copied some large files to it.  After rebooting however, the data got corrupted.  It's on version .5 so I can't really complain about that.

I'd switch to Solaris or BSD but neither of them seem to have any support for my specific hardware.  Sigh, I guess I'll have to revisit the issue in a year or so.

---

### Post by neondiet on 2008-10-21
> **jgold said:**
> Next, using gparted, I formatted each device with the ext2 file system and set the flags to raid..
Hi. 

You're attacking this the wrong way round.  You don't create lots of individual filesystems (one per disk) and then raid them afterwards.   You raid the devices first to create a single big blank raid device and _then_ you create a filesystem on top of that:

  dIsk1, disk2 , etc --> MD RAID --> Filesystem --> Mount Point

I don't know why you're using the --auto=md flag either.  I'm pretty sure this is where your /dev/md0p1 device is coming from, and really you don't need it.   /dev/md0 is the correct device file to be using for your first single large non-partitioned raid device.   I have a few servers here each with multiple md raid devices: md0, md1, md2, etc.

In fact forget what I said about creating MD raid devices with multiple partitions.    If you do decide you need to chop this space up into smaller units then use LVM instead.  It's much more flexible.  e.g.

```

disk1, disk2, etc --> MD RAID --> LVM VG0 --> LVM LV1 --> Filesystem --> Mount Point 1
                                        \ --> LVM LV2 --> Filesystem --> Mount Point 2
                                        \ --> LVM LV3 --> Filesystem --> Mount Point 3

```

---

### Post by neondiet on 2008-10-22
> I think that Linux really needs some work on the software raid subsystem. Either that or gparted needs some work so that it understands mdadm structures.
No, honestly it works fine.  Like I said before, you have it back to front.  Starting from scratch with a bunch of blank disks, you use gparted (or parted, or sfdisk, etc) to create a single partition on each disk that encompasses all the available space.  Then you forget about gparted because you're finished with it.   THEN you create your MD raid device using those disk partitions, which gives you one new big blank raid disk to play around with, create a filesystem with, or use to create an LVM Volume Group (or add to an existing VG) or whatever you want.

---

### Post by jgold on 2008-10-22
Thanks so much for the reply neondiet.  I'm sure I have it back to front as you say.  The problem is, I'm coming to the problem as a Windows guy since Windows 3.1.

On Windows, you use the same program to partition and format the disks - the disk manager.  It's also where you create a software raid. If the raid gets broken, it's also where you go to repair it.  This all makes a certain amount of logical sense.  You're dealing with disks so you use the disk manager.

On Linux, it starts off fairly similar.  You can partition the disks with gparted and there are some flags that you can set to tell the system that these are members of a raid array.  Then you go to the command line to actually create the array.  Now gparted shows the new device /dev/md0 but does not show the file system status information correctly the way it does for the other devices.

This can be pretty confusing for a new user.  It might even cause some new users to notice for the first time that there's an exclamation point on his raid file system that's telling him it's messed up somehow.  Even though as it turns out, there was probably nothing actually wrong with the real /dev/md0 file system, said person might have gone to all the trouble of purchasing three 1 TB drives and spend a week backing up all the data and rebuilding the array. #-o.

To top it off, the tutorials on setting up raid arrays are often very out of date and don't really explain why they're doing what their doing.  I thought the --auto=md option just set the drive to automatically mount when you start it up.  Several tutorials used it and it sounded like something I wanted the raid to do.

So, I think it would be a good idea if gparted understood the raid arrays a little better.  I understand that Linux is a voluntary project and there are lots of areas that need addressing.  I'm a developer so I could in theory do it myself.  As a middle aged father of four, I just don't have the time right now.  That's one of the reasons I appreciate all the work the Linux community has done.  I know what's involved and I appreciate it.

On the bright side, the resulting raid array is many times faster than the Windows array I originally created.  I first built the system with Windows 2008.  When I tried using the array, the fastest write I could get was around 3-7 mb/sec.  As I copy the data back right now, I'm getting 32.4 mb/sec.

---

### Post by jgold on 2008-10-22
While I've got you, I have a few quick questions.

I think that mdadm -D /dev/md0 gives me the current status and cat /proc/mdstatus tells me how the rebuild is going but how do you force Ubuntu to verify/rebuild the array?  

Also how do you check the file system without risking breaking it further?  I tried fsck.ext3 /dev/md0 but it gives ms a scary warning that running it on a mounted file system may cause SEVERE filesystem damage.  In other words, what option tells it to check only without actually trying to do any repair?

Is there a way to move the ext3 log file to a different device?  It seems like during my reading, I came across and article about it but I haven't been able to find it again.

Finally, I plugged an external eSATA device into the computer and when I booted, the device letters moved around.  Instead of starting at /dev/sdb1, the new drive when to /dev/sda1 and moved everything else down one letter.  This caused the raid array to break.  I managed to get it working again by removing the eSATA drive and typing "sudo mdadm --A /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1"  It told me "/dev./md0 assembled from 5 drives and 1 spare - not enough to start the array.   Then I did "sudo mdadm -E /dev/sdi1"  That started rebuilding it.

The question is, is there any way in Ubuntu to lock the device letters down so they don't move around like that?

Thanks again for your help.

---

