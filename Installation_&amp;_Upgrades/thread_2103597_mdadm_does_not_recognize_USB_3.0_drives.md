---
title: "mdadm does not recognize USB 3.0 drives"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by ltburch2000 on 2013-01-10
I have a probox HD enclosure connected to my PC via USB 3.0.  I can see the drives in the enclosure and I have put a gpt partition table on them (there are 4 3TB drives) and partitioned them.  I even tried formatting one and putting files on it. which worked fine so I expect the drives are working.

However when I try and create an array on them

sudo mdadm --create --verbose --verbose /dev/md1 ––level=6  ––raid-devices=4 /dev/sdj1 /dev/sdk1 /dev/sdl1 /dev/sdn1

it says 

mdadm: no raid-devices specified.

Are the devices I am specifing not appropriate for some reason?  I would assume that since I could partition and format them they would be alright but perhaps there some subltey I am missing here.

I have spent several hours trying to puzzle this out and made little headway.

---

### Post by darkod on 2013-01-10
Are the partition types Linux Raid?

Can you post the output for example of:
sudo parted /dev/sdj print

---

### Post by ltburch2000 on 2013-01-10
Here it is

Model: WDC WD30 EFRX-68AX9N0 (scsi)
Disk /dev/sdj: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB


all four are the same with the exception of the last drive where I formatted ext4 just to see if it would work (it did).  I figured that would get overwritten once I made the array and put a file system on it.

> **darkod said:**
> Are the partition types Linux Raid?

Can you post the output for example of:
sudo parted /dev/sdj print

---

### Post by darkod on 2013-01-10
This partition #1 is not marked as raid. You see, the flags are empty.

Try this:
sudo parted /dev/sdj
set 1 raid on
quit

That will set it as raid partition. After you do this on all four partitions/disks, try the mdadm --create again.

But note that I am not sure mdadm will work on usb disks. How do you know the disks don't change places on each reboot? Are you sure they will be ordered in the same order?

I remember another thread here with this same situation but it was a while ago and don't remember whether he got it working. I think not, not in a stable way anyway.

Personally I wouldn't even think about software raid with usb disks. Not to mention the low transfer on usb, even on usb 3.0.

---

### Post by ltburch2000 on 2013-01-10
usb 3.0 is supposedly faster than ESATA, also the drives show up with USB and not with ESATA, I guess my ESATA port multiplier doesn't work.

Well I set the raid flag on all four partitions I can see it with parted.  But when I run the mdadm to create the array I get exactly the same result as before.


> **darkod said:**
> This partition #1 is not marked as raid. You see, the flags are empty.

Try this:
sudo parted /dev/sdj
set 1 raid on
quit

That will set it as raid partition. After you do this on all four partitions/disks, try the mdadm --create again.

But note that I am not sure mdadm will work on usb disks. How do you know the disks don't change places on each reboot? Are you sure they will be ordered in the same order?

I remember another thread here with this same situation but it was a while ago and don't remember whether he got it working. I think not, not in a stable way anyway.

Personally I wouldn't even think about software raid with usb disks. Not to mention the low transfer on usb, even on usb 3.0.

---

### Post by darkod on 2013-01-11
Well, if that didn't work, I guess you can't count on it working. I have no more ideas.

As for usb3 speeds, or any usb external disk in general, theoretical speed is one thing, reality another.

usb2 has speed of 480Mb/s which is 60MB/s. Have you ever seen a usb2 disk doing 60MB/s? I haven't.

---

