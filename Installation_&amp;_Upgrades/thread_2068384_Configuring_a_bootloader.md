---
title: "Configuring a bootloader"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by Messyhair42 on 2012-10-09
I have Ubuntu 12.04 installed in a RAID 1 array on two identical 3 TB drives. when I installed it it failed to install a bootloader. after troubleshooting that issue; see this thread [http://ubuntuforums.org/showthread.php?t=1998052]("http://ubuntuforums.org/showthread.php?t=1998052") I had a problem with my BIOS not recognizing all my HDD's. after migrating to a new case and a new PSU I believe I have this issue solved, I couldn't get access to one drive but right now it's nonessential so I disconnected it. 

I have Ubuntu on a RAID with an instance of GRUB 1.98 on the MBR of a 160GB drive currently as /dev/sdb but there's nothing in its config file. How do I configure a bootloader to point to my RAID? help is appreciated, I've been running from a flash drive since my hard drive crashed six months ago.

---

### Post by darkod on 2012-10-09
You need to use the alternate install cd for installing on fakeraid, it has better support for raid and installs the bootloder better.
With the standard live cd the bootloader often fails.

You can add it now from live mode if you want to.

What you will need to do is:
Boot into live mode, activate the array:
sudo dmraid -ay

Print the list of all devices and partitions:
sudo parted -l (small L)

Note the name of the raid device, something like /dev/mapper/blah_blah. Also be careful because the partitions will be called the same only with something like 'p1', 'p2', etc at the end.

You need to know EXACTLY what is the raid device, and what the partitions on it.

After that simply mount the root partition, lets say in this example it ends with 'p5' and install grub to the raid device (NOT any partition):
```
sudo mount /dev/mapper/blah_blah[COLOR="red"]p5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/blah_blah
```

That should do it.

---

### Post by Messyhair42 on 2012-10-14
Hrm, I have the alternate install CD and it doesn't have a live mode, at least not from the main menu. I do have a flash drive with 12.04 installed so I'm testing it out with that. when I booted I can absolutly confirm that all my attached drives were recognized, however when booting I again got a degraded RAID message (but not from my other flash drive, which recognized the RAID)

here is the part of ```
sudo parted -l
``````
Model: Linux Software RAID Array (md)
Disk /dev/md0: 3999MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  3999MB  3999MB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md1: 2997GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2997GB  2997GB  ext4


```
and terminal doesn't accept ```
sudo dmraid -ay
``` as a valid command


edit: tomorrow I think i'll attempt a new installation of the system on the RAID

---

### Post by webguy12 on 2012-10-15
I am having the same problem with the 12.04 server when I set the raid0 when it come to the grub part of the install It wont install it.    

I am lost on how to get this to work..  

Thanks..

---

