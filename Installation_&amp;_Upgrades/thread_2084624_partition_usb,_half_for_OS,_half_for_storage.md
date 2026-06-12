---
title: "partition usb, half for OS, half for storage"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by x34460 on 2012-11-16
Greetings.

A couple of years ago I found a great online tutorial on how to partition a usb drive so that *buntu is installed on one half and the other partition is reserved for storage... in cases where it's necessary for Windows to access the contents of the "storage" partition. I followed the instructions and it has worked perfectly for well over a year- probably close to 2 years now. Unfortunately, the drive has seen better days and needs to be retired. I have a new drive but can not find the tutorial I originally used and am having difficulty finding a tutorial that fits my scenario as bookmarks tend to get lost or misplaced over time.

Any help with this would be very much appreciated.

I'm currently using a Windows computer (first time in YEARS) because my Ubuntu computer died. I have partitioned the new drive to match the scheme of the old one:

partition 1 (10gb) for storage: primary drive(not logical). partition appears in my computer with drive letter assigned.

partition 2 (20gb) for OS: primary drive(not logical). 
drive *does not* show in my computer (but neither does the other, old drive).

I'd like to install the OS on the second partition so I can use the first half interchangeably between OS environments for storage but that second partition is not showing up using Windows Disk Imager in order to install the OS.

I can't recall how I made it work the first time and at this point, I'm stuck.  
Please help if you can.

Thanks.

---

### Post by Mr_JMM on 2012-11-16
Windows can't see ext3/4 partitions. I believe you can download something that will enable it to read and hopefully write to ext3/4 partitions.

Alternatively, you could burn an Ubuntu DVD and do everything from that.

---

### Post by x34460 on 2012-11-16
It does seem likely that I originally did all of this on my Ubuntu laptop that recently took a turn for the worse. It's been years since I've used Windows and I don't recall having this much trouble.. must have been done using Ubuntu.

Will try that.
Thanks.

---

### Post by x34460 on 2012-11-16
Still wrestling with this one.

Both partitions on the new USB drive are FAT32. 
When I plug the drive into Windows, only the first partition shows up so that is the one I'll need to keep where it is... which is how the old USB is partitioned. The "storage" partition is first so Windows machines can see it and read/write. The problem seems to be with the second partition. Ubuntu can see it just fine but the "Startup Disk Creator" failed to install to the specified partition.

I attempted this using an old live-cd.

Suggestions?

Thanks.

---

### Post by oldfred on 2012-11-16
Is this USB drive a flash drive? Windows only sees the first partition which must be FAT or NTFS.

Did you do a full install or the liveCD version with persistence to save some data on the second partition? 

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

---

