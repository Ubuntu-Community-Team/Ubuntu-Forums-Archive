---
title: "Ubuntu 12.10 Server - creating a LVM on a disk already in use"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by RedShoeRider on 2013-03-31
Good Evening, all:

I've searched high and low, but I just can't find an answer that makes sense to me. 

The system: Ubuntu server 12.10, x64, on a generic white box server running an HP P800 SATA RAID controller. The array is 2.7TB.
The current system drive situation: Ubuntu is installed and running on /dev/cciss/c0d0p1, which is a 250gb partition, formatted MBR/ext4. The rest of the array is unformatted. 

What I would like to do is create an LVM out of the 2.4TB that is currently unformatted. Ideally, it would be /dev/cciss/c0d0p2. I can find lots of instructions on how to create the Logistical volume on a new, unformatted drive, but I can't find a way to do this on just part of a drive. Booting a live CD and running GParted does not allow for this, and if it's at all possible, I don't want to format the entire system and start over. Being that I can't find instructions on how to do this, I don't know if it's even possible. 

Any thoughts/suggestions would be very appreciated! 
I'm a decent hardware monkey, but I'm a very green software monkey!

-Red

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by darkod on 2013-04-01
The physical device used for LVM is usually a partition, not a whole disk. Which means, most tutorials are talking about exactly what you want to do, using a partition (part of a disk) for LVM.

To start with, post the output of:
```
sudo parted -l (small L)
```

That should show us your disk.

I'm surprised the array would show as /dev/cciss/.... I would expect it to be /dev/sda because if it's HW raid, the controller will make up the array and it presents it to the OS as a single disk, in other words /dev/sda. It might be that this controller is actually using fakeraid.

---

### Post by RedShoeRider on 2013-04-01
Between the two of you, the lightbulb went on in my head! 
What I wanted to do was easy enough; I just needed to create the LVM a little differently than my brain had originally wrapped my head around what an LVM was about. 

It works a charm now; it's a 2.5TB volume now. I'm load testing as we speak, but it looks good so far. 

Darkod: While the card is branded as an HP SmartArray P800 controller, I think it's an LSI underneath the HP branding. IIRC, the odd /dev/cciss has to do with the driver model that the HP card uses for this generation of RAID cards, or so says HP. The P800 was the last to use this driver set, which was originally for SCSI cards. It's a HW raid card; battery backup modules, heatsinks, and all. Of course, I could be wrong, too! :)


Model: Compaq Smart Array (cpqarray)
Disk /dev/cciss/c0d0: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  270GB   270GB   primary  ext4         boot
 2      270GB   1684GB  1414GB  primary               lvm
 3      1684GB  3001GB  1316GB  primary               lvm


 LV Status              available
  # open                 1
  LV Size                2.48 TiB

---

### Post by darkod on 2013-04-01
OK. For future reference, I see you made a msdos partition table on a 3TB device. To support partitions larger than 2.2TB you need to use gpt table.

I don't know whether you created two LVM partitions because you couldn't create one of 2.7TB, or you simply wanted two LVM partitions.

On disks larger than 2TB use gpt tables.

---

