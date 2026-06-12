---
title: "Another NTFS Disappearance"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by slick_nick on 2008-04-25
Fixed the problem: Ran testdisk and had it write new MBR code. Simple!


Upgraded to Hardy yesterday with ALMOST no problems, except...my 80gb NTFS drive has disappeared. I haven't gotten around to reformatting it to ext3, it's basically just got a bunch of music on it. Under 7.10 I would have to go into Computer, click it, and it would ask for my admin password to mount it.  
Now after updating, it has completely disappeared. There is no listing for it in fstab or mtab. The couple of attempts at mounting it from the terminal resulted in errors about it not existing. :confused:
Gparted sees it, at /dev/sdb1, and gives the following warning:

[I]The device /dev/sdb1 doesn't exist.
ntfsresize v1.1.3.1 (libntfs 9:0:0)
ERROR(2): Failed to check '/dev/sdb1' mount state: No such file or directory.
Probably /etc/mtab is missing. It's too risky to continue.
You might try an another Linux Distro.
Unable to read the contents of this filesystem!
Because of this, some operations may be unavailable.[/I]

Is there some command/app to run to fix this, or am I just going to have to manually edit my fstab/mtab?
As an aside, yes, Gparted actually said "try *an* another"

---

### Post by Pumalite on 2008-04-25
Try TestDisk on the partition: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by tormod on 2008-04-25
Try **ls /dev/sd*** to see if the partition name is correct and it is detected by the kernel. It might be that it is not mounted because it is "dirty" - not cleanly unmounted and marked as needing a file system check. If you still have windows, try file system checking from there.

**sudo fdisk -l /deb/sdb** should also list the partition as seen from the partition table.

---

### Post by slick_nick on 2008-04-25
Thanks guys, here's the results:
Testdisk found the partition, doesn't seem to be anything wrong with it.

slick@slick-desktop:~$ ls /dev/sdb
/dev/sdb
slick@slick-desktop:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2475803b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10011    80413326    7  HPFS/NTFS


So it's there...guess I'll just have to figure out what to put into fstab to fix it.  Like I said, there is absolutely no entry in fstab or mtab for the drive..thought it was odd that it completely disappeared.  I haven't had windows for quite some time now..and the drive as far as I know should be "clean" since I was just listening to music off it yesterday before I upgraded.

---

### Post by Pumalite on 2008-04-25
You might be missing ntfs-3g

---

### Post by slick_nick on 2008-04-25
Checked...I think I read someplace that ntfs-3g comes with Hardy, but anyways I did try apt-get, and: "ntfs-3g is already the newest version."  Oh, and my 250gig external USB drive that is still NTFS works just fine...

Time to shoot some people in the face on Halo 3, I'll check back later :)

---

### Post by mrsteveman1 on 2008-04-25
Sounds like something wrote over your fstab file 

Try mounting it manually and make sure that works:

```
sudo ntfs-3g /dev/sdb1 /windows
``` etc

---

### Post by slick_nick on 2008-04-25
Yeah, that something that overwrote my fstab would be the Hardy Heron Upgrade! 
I tried as you suggested, both /dev/sdb1 and /dev/sdb:
[I]slick@slick-desktop:~$ sudo ntfs-3g /dev/sdb1 /Storage
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type 'ntfs-3g --help' for more information.
slick@slick-desktop:~$ sudo ntfs-3g /dev/sdb /Storage
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?[/I]

---

### Post by Pumalite on 2008-04-25
Post:
sudo fdisk -l

---

### Post by slick_nick on 2008-04-25
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24862485

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5433    43640541   83  Linux
/dev/sda2            5434        7970    20378452+   f  W95 Ext'd (LBA)
/dev/sda3   *        7971        9729    14129167+  83  Linux
/dev/sda5            7940        7970      249007+  82  Linux swap / Solaris
/dev/sda6            5435        7939    20121381   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2475803b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10011    80413326    7  HPFS/NTFS



I don't know what /dev/sda2 is, haven't seen that before...but that's besides the point, I'm worried about sdb1 :)

---

### Post by Pumalite on 2008-04-25
Well, sdb1 is there and seems intact.

---

### Post by slick_nick on 2008-04-25
Yeah... I was hoping there was a command or app I could run to make ubuntu straighten it out without having to manually edit the fstab but I guess that's why I'm going to have to do?

---

### Post by mrsteveman1 on 2008-04-25
Fstab is just a file that specifies which filesystems on the system you want to be mounted at certain times, and the permissions and options for those filesystems. If ntfs-3g can't mount /dev/sdb1, which obviously exists, something weird is going on, and fstab isn't the real problem.

Try mounting it read only with the in-kernel ntfs driver instead:

```
sudo mount -t ntfs -o ro /dev/sdb1 /windows

```

---

### Post by Pumalite on 2008-04-25
Make the directory first:
sudo mkdir /windows

---

### Post by slick_nick on 2008-04-25
I was trying to mount it in the directory I created /media/storage, which if I recall correctly is where it used to mount in Gutsy. I did a mkdir for just /storage as well; same result on both:

[I]slick@slick-desktop:~$ sudo mount -t ntfs -o ro /dev/sdb1 /storage
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.[/I]

/sbin/mount.ntfs --help just displays the help/options for ntfs-3g.

---

### Post by mrsteveman1 on 2008-04-25
So even forcing the mount command to use ntfs doesn't use it. I wonder if they have removed that ntfs driver from the kernel in hardy to make ntfs-3g the default.

Ok, its hard to tell why its giving that error but because it said VOLUME not found and not device not found, perhaps it means the filesystem.

Have you connected this drive to a windows machine?

Have you tried running the linux ntfs check on the volume? i can't remember what its called, maybe fsck.ntfs or ntfschk or something, its part of ntfsprogs package.

---

### Post by slick_nick on 2008-04-25
I think you're referring to 'ntfsfix' and yes, tried it, doesn't work because it can't find the volume! :(  As per my first post, gparted SEES the volume/partition, but says *The device /dev/sdb1 doesn't exist*... I haven't connected it to a Windows machine, I'm 100% ubuntu and my roommate is a Mac guy; I do have friends with Windows so I can do that sometime.  Odd thing is, the drive was working fine under Gutsy and hasn't been touched by Windows in months...

[I]Failed to determine whether /dev/sdb1 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.[/I]

---

### Post by mrsteveman1 on 2008-04-25
Ok, remove Hardy from the equation, boot a gutsy cd and see if you can mount it there.

Also, OS X can mount NTFS drives read only by default, and there is a nice NTFS-3G package for OS X as well so you could also do that if you really need to.

---

### Post by slick_nick on 2008-04-26
The Gutsy live cd worked just fine, I was able to go into Computer, open it right up and access eveyrthing on the drive, no having to manually mount it or anything

---

### Post by artships on 2008-04-26
> **slick_nick said:**
> [I]slick@slick-desktop:~$ sudo mount -t ntfs -o ro /dev/sdb1 /storage
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.[/I]

/sbin/mount.ntfs --help just displays the help/options for ntfs-3g.

You're lucky.  I execute  "/sbin/mount.ntfs --help" and get:

/sbin/mount.ntfs: /usr/local/lib/libfuse.so.2: version `FUSE_2.7' not found (required by /sbin/mount.ntfs)

Which, coincidentaly, is the same error I get executing "sudo mount -a" with a /etc/fstab built under Gutsy (I've updated to Hardy). 

/sbin/mount.ntfs-3g: /usr/local/lib/libfuse.so.2: version `FUSE_2.7' not found (required by /sbin/mount.ntfs-3g)

"sudo apt-get install ntfs-3g" displayed:
ntfs-3g is already the newest version.

---

### Post by Pumalite on 2008-04-26
Uninstall ntfs-3g (Complete Removal) and reinstall it.

---

### Post by slick_nick on 2008-04-26
Did the complete removal, reinstall; still gives the same error upon trying to mount: 
[I]slick@slick-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/storage
[sudo] password for slick: 
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory[/I]

---

### Post by tormod on 2008-04-26
Well, your /dev/sdb1 does not exist. fdisk shows there is a partition on the disk (in the disk partition table at least) which it guesses would be called sdb1 but the kernel has not detected it and set up a device entry /dev/sdb1. All other tools (like ntfs-3g) would use this device entry so they're out of luck.

So there is something in the partition detection in your Hardy kernel that fails. Can you attach /var/log/dmesg please?

---

### Post by mrsteveman1 on 2008-04-26
You can easily check what the kernel sees on attached disks like this:

```
sudo cat /proc/partitions
```

---

### Post by slick_nick on 2008-04-26
dmesg is attached. Am I right that the below means the volume itself is being seen but not the partition?

[I]slick@slick-desktop:~$ sudo cat /proc/partitions
major minor  #blocks  name

   8     0   78150744 sda
   8     1   43640541 sda1
   8     3   14129167 sda3
   8     5     249007 sda5
   8     6   20121381 sda6
   8    16   80418240 sdb[/I]

I don't really have a problem with hooking the drive up to another computer, getting my files off it, and reformatting to ext3 (like I should've done a while ago!), but if this is a weird Hardy bug, I'd like to figure out what it is so it can be fixed in an update or we can at least help other people who have this happen to them in the future. :)

---

### Post by mrsteveman1 on 2008-04-26
The kernel isn't reading the partition table correctly, hence the lack of an sdb1 in the partitions list in proc, and because it isn't, it's not creating a block device for that partition, meaning no /dev/sdb1 to operate on. I suppose you could make the node yourself but that's not a solution and shouldn't be necessary.

The partition table itself is probably fine because fdisk can read it.

The filesystem isn't going to matter here, the kernel makes those device nodes based on the sector information in the MBR. If it's not making a device for an NTFS partition, changing its partition ID or making it EXT3 shouldn't change anything, even if you get your stuff off the drive first.

You could also ignore the partition table entirely and mount the device as an offset. I believe you can find out what offset the partition is located at with fdisk, then you can use that with the mount command like this:

```
sudo mount -o offset=<number here> /dev/sdb /windows
```

Note however thats an incredibly complex solution to a problem that shouldn't exist. It's obviously a kernel problem, but I'm not sure what's so special about this particular drive, since its on the same controller the other drive is on, and that drive works fine.

---

### Post by mrsteveman1 on 2008-04-26
Sorry, got distracted stepping through that kernel log. For some reason i find it fun to try and guess whats in a system by looking at the little clues in the log :D 

Heres the real problem:

```

[   28.182601] Buffer I/O error on device sdb, logical block 0
[   28.584247] ldm_validate_partition_table(): Disk read failed.
[   28.584256] Dev sdb: unable to read RDB block 0
[   28.584461]  unable to read partition table

```

logical block 0 is the MBR on the disk, and the kernel can't read it for some reason. Is this an old disk?

There are a bunch of bus errors in the log as well.

---

### Post by slick_nick on 2008-04-26
Thanks to Newegg's order history, I can say confidently I installed the drive in April of '05.  I still find it really odd that it was working fine in Gutsy, still works fine with the Gutsy live cd, and not at all in Hardy.  Also, this drive is IDE and my main drive is SATA, aren't those different controllers?
I noticed those bus errors too but don't yet have the experience to know what they mean or how to go about fixing them :)

Just noticed that testdisk has an option to write new MBR code...maybe it's time to pop the drive out and back it up then try that. Also I didn't see any way in fdisk to find the offset.

---

### Post by mrsteveman1 on 2008-04-26
Yea don't worry about the offset thing i was just thinking out loud and wrote it down :D

If the 2 drives are IDE and SATA then yea its a different controller. It could be the drive, or it could be the kernel, its hard to say. If there aren't any such bus errors in the kernel log when running gutsy it could mean there isn't anything wrong with the drive, or it could mean it just isn't logging the errors.

Definitely backup anything important on that drive, even if you have to remove the drive from the system to get stuff off of it. It could be nothing wrong but if its important stuff you don't want to lose it.

I really wish the ubuntu devs would provide packages for the newest kernel though (2.6.25), because my next suggestion would be to keep hardy and grab the newest kernel from kernel.org, compile and install it. I wish that weren't necessary just to use the newest kernel but it is for the moment. If its a kernel bug thats already been fixed, that would fix things, but its hard to say.

---

### Post by artships on 2008-04-27
> **Pumalite said:**
> Uninstall ntfs-3g (Complete Removal) and reinstall it.

Did that.  Now I'm "...not priveleged to mount the volume '<ntfs partiiton'>". And, "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.".

Sucker worked Just Fine under Gutsy.

---

### Post by tormod on 2008-04-27
artships, please don't hijack the thread. Open a new thread unless you can show that you have the exact same problem as slick_nick.

---

### Post by tormod on 2008-04-27
> **slick_nick said:**
> dmesg is attached. Am I right that the below means the volume itself is being seen but not the partition?
Yes, and your dmesg output shows that the kernel gives up trying to look at the disk.
> 
I don't really have a problem with hooking the drive up to another computer, getting my files off it, and reformatting to ext3 (like I should've done a while ago!),
That won't help since the kernel doesn't even get to look at the filesystem.
> 
 but if this is a weird Hardy bug, I'd like to figure out what it is so it can be fixed in an update or we can at least help other people who have this happen to them in the future. :)
Excellent attitude! Please file a bug on launchpad (package "linux") and attach the dmesg output (uncompressed). Can you please also attach the dmesg output from Gutsy. I would wildly guess that the Hardy kernel sets up the wrong ATA/DMA parameters for the disk.

---

### Post by slick_nick on 2008-04-27
artships, I'm glad I'm not the only one to have a ntfs partition that worked just fine under Gutsy and disappeared in Hardy.  My condolences that yours seems to be worse off than mine!
I assume you did "sudo xxx" with whatever command resulted in "not privileged..." ?

---

