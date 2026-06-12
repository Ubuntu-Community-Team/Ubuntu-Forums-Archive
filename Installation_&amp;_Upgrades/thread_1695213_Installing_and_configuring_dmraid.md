---
title: "Installing and configuring dmraid"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by ssarkar on 2011-02-25
I have a fresh install of ubuntu 10.10 64-bit on a SSD drive.  I have an array of 4 2TB drives that I would like to set up as a RAID 10.  I enabled RAID in my BIOS and created the RAID 10, so I have the firmware side of things configured.  

I've been reading on how to configure dmraid and looking through the forums, and it seems like something isn't working as expected, or I'm not understanding what the results of dmraid should look like.

When I run dmraid -r here is my output 

> /dev/sdd: pdc, "pdc_cifgjhgjdd-1", stripe, ok, 1758766336 sectors, data@ 0
/dev/sde: pdc, "pdc_cifgjhgjdd-1", stripe, ok, 1758766336 sectors, data@ 0
/dev/sdc: pdc, "pdc_cifgjhgjdd-0", stripe, ok, 1758766336 sectors, data@ 0
/dev/sdb: pdc, "pdc_cifgjhgjdd-0", stripe, ok, 1758766336 sectors, data@ 0That seems to be reasonable.  When I run dmraid -ay, it creates 3 new mappings in my /dev/mapper directory

pdc_cifgjhgjdd 
pdc_cifgjhgjdd-0
pdc_cifgjhgjdd-1

And finally when I run dmraid -s -s pdc_cifgjhgjdd I get
> 
*** Active Superset
name   : pdc_cifgjhgjdd
size   : 3517532672
stride : 128
type   : raid10
status : ok
subsets: 2
devs   : 4
spares : 0
--> Active Subset
name   : pdc_cifgjhgjdd-0
size   : 3517532672
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
--> Active Subset
name   : pdc_cifgjhgjdd-1
size   : 3517532672
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
So each of the 2 active subsets has the same size, but the superset has the same size as well.  And when I got to the disk utility, there are now 3 new peripheral devices that show up as 3 1.8 TB disks in addition to the 4 2TB disks that are installed in the machine.

So I would have assumed if I had set the RAID 10 up properly, I should be seeing 1 4 TB partition which I could then initialize with fdisk and use.  However, it's looking like  I have 3 1.8TB disks but dmraid has 2 of them labeled as subsets and one active superset.  Is this how a RAID 10 should look?  or is there a configuration step that I'm missing?

Any help would be appreciated.

---

### Post by ronparent on 2011-02-25
I'm not sure what your question is but if all you did is set the array of four disk up in raid bios as a raid array, you would not see anything in your file system until you created one or more partitions. 

A raid 10 is a combination of a mirrored and striped array. As such it would have total raw capacity of two of the four disks. With dmraid properly installed, in other words, the four drives should normally show up as one unallocated space equal to the capacity of two of your 2Tb disks.

Beyond this it gets complicated. I believe that because of the size of this space you may not want to use normal bios based formating to handle it but will have to use GPT (GUID Partition Tables). I don't yet have firsthand experience with GPT so I can't advise you. This is a starting point: [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

In any case once you actually create partitions on your array the partitions themselves will define the usable space on that array.

---

### Post by ssarkar on 2011-02-25
I guess I missed describing a few steps in the previous post.  My fault.

After I ran dmraid -ay and the drives showed up in the /dev/mapper, that should have set up the fakeraid side of the raid configuration.

The next step I did after that was to create the partition on the drive.   So I ran fdisk on pdc_cifgjhgjdd and created an ext3 partition.  However, that partition is only 1.8TB.  I would think that if that was the active raid device it would be closer to 4 TB instead of 2TB.  

At least that is what it seems like according to other documentation that i have been reading.

---

### Post by YesWeCan on 2011-02-25
It is unusual to use fakeraid with linux. It exists to enable Windows to do software raid.
Linux doesn't need it. Linux uses mdadm, which would be simpler.
Are you aware of this? :)

---

### Post by ronparent on 2011-02-26
YesWeCan - That is augmentative, none of it is simple!:lolflag:

But in principle I agree with you. Unless the user intends to use windows in their system at some point - then the fakeraid is necessary.

---

### Post by YesWeCan on 2011-02-26
> **ronparent said:**
> YesWeCan - That is augmentative, none of it is simple!:lolflag:

But in principle I agree with you. Unless the user intends to use windows in their system at some point - then the fakeraid is necessary.
That's true! :)
Are there any advantages to using fakeraid with Ubuntu? I read a couple of scornful articles about it...perhaps because of the deceptive marketing of it...that claimed that md raid is just as fast, and more flexible because your array is not tied to a particular mobo.

---

### Post by ronparent on 2011-02-26
There are advantages and disadvantage for each approach. Both fakeRAID and software raid are basically software raids. I don't feel you can either scorn or praise either one without it applying to the other. Either are very workable if you know what you are doing. :D

---

### Post by ssarkar on 2011-02-27
I've seen comments both ways regarding dmraid and mdadm.  Anyways, I've been trying mdadm since I haven't had much success with dmraid, and I will be staying only in linux.

Anyways, I managed to format each of my drives with ext4 and set the type to Linux RAID autodetect.  I then created the RAID using this command

> mdadm --create /dev/md0 --chunk=128 --level=5 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

The raid array builds, and I let it run till the whole rebuild is done, which takes 7 hours.  After that I can format the new raid array with this command

> mkfs.ext4 /dev/md0

I can then add /dev/md0 to my fstab and when I type mount -a it all mounts fine

However, when I reboot, the raid array doesn't seem to be mounted.  There is no /dev/md0 so I can't run mdadm --examine against it.  When I open up Disk Utility, it says that the RAID array is Not running and only partially assembled.  Is there something that needs to be done so that the raid array will stay up and running between reboots?

---

### Post by ssarkar on 2011-02-27
After I reboot, this is what is in my /proc/mdstat file.  before the reboot, everything looked great in this file

> 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdc1[1](S)
      1953511936 blocks
       
unused devices: <none>


---

### Post by ssarkar on 2011-02-27
Ok, after some more digging around, and messing around with things, here is where I'm at.

If I run this command after a reboot

mdadm -A --scan

It will allow me to mount the raid array, however it is in a degraded state

When looking at the /proc/mdstat, here is what i see

> 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sde1[3] sdd1[2]
      5860535808 blocks level 5, 128k chunk, algorithm 2 [4/3] [U_UU]
      
md_d0 : inactive sdc1[1](S)
      1953511936 blocks
       
unused devices: <none>


3 of the drives I originally added to the raid array, were added back in.  However, sdc1 was assigned to md_d0 and is inactive for some reason.  Not sure what is going on at this point

---

### Post by psusi on 2011-02-27
Fakeraid is mainly for dual boot compatibility with windows.  If you aren't dual booting with windows, mdadm is much more robust and better supported.  If you want to install using mdadm software raid, you should use the server or alternate install images instead of the desktop image.  The text mode installer provides a menu driven interface to configure the raid array.

Also you said that you originally wanted to do raid10, but then you created  raid5 array?  If you initially set up the disks in a fakeraid array and want to switch, you need to remove them and destroy the array either with the bios utility or by running sudo dmraid -E /dev/sdX to erase the raid signatures from the drive.  Simply disabling the raid option in the bios will not do.

---

### Post by ronparent on 2011-02-28
> Simply disabling the raid option in the bios will not do.

You are absolutely correct. To rid yourself of fakeraid disk signatures I advise all. First remove the raid in the raid bios, erase the signatures with dmraid and then unistall dmraid altogether - it won't be needed.

---

### Post by YesWeCan on 2011-02-28
> **ssarkar said:**
> However, when I reboot, the raid array doesn't seem to be mounted.  There is no /dev/md0 so I can't run mdadm --examine against it.  When I open up Disk Utility, it says that the RAID array is Not running and only partially assembled.  Is there something that needs to be done so that the raid array will stay up and running between reboots?

Have you put the ARRAY directive in your /etc/mdadm/mdadm.conf file?

If not, you need to. There is a problem with mdadm assembling after a reboot with some systems if you don't specify the mdadm UUIDs of the member disks. mdadm loses the plot and mis-assembles the disks and invents new device names like md_d0.

You need to stop all the raid devices. mdadm --stop /dev/md...
and then reassemble the raid properly again
mdadm --assemble --scan /dev/md0

Then generate the ARRAY directive
mdadm --examine --scan
and add it to the end of the mdadm.conf file.

Then it may assemble correctly on the next reboot.
For good measure would you post the output of mdadm.conf when you have done this?

---

### Post by ssarkar on 2011-02-28
I had originally wanted to do a raid5, however dmraid didn't support raid5 with the fakeraid controller on my motherboard which is why I switched to raid10.

WIth mdadm, I could do raid5, so I switched to that.

I just ended up reformatting and redoing the raid5 array with mdadm, and then I took the output from 

mdadm --examine --scan and put it into my mdadm.conf file.

The file now looks like this

> 
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Fri, 25 Feb 2011 21:30:20 -0500
# by mkconf $Id$

ARRAY /dev/md0 level=raid5 num-devices=4 UUID=9e31647c:811173be:ce441835:a5a621c9


Since I just started over from scratch, it is rebuilding the array.  However, when I reboot, the raid array is still there using all 4 drives, and showing up correctly.  I think putting the explicit definition of the array into my mdadm.conf fixed it.  I had assumed from the things I read that the mdadm.conf wasn't necessary anymore, but I guess that isn't the case. 

Hopefully once it rebuilds, I'll be able to format it and mount it and it'll survive reboots.
Thanks for everyones help.

---

### Post by YesWeCan on 2011-02-28
Glad it appears to be working now. :)

I must say I find it unintuitive that mdadm needs this ARRAY directive. Each disk that is a RAID member has a superblock that has all the info needed as well as the UUID. So why mdadm can't, or won't, just scan the disks and work out which is in which array escapes me. The documentation is rather light.

Anyhow, once you've got it set up it should do its thing well.

BTW, RAID5 is not especially reliable, much less so than RAID 10, so make sure you back up your data too.

---

### Post by ssarkar on 2011-02-28
RAID5 isn't reliable?  I thought with RAID5 if one drive dies, I can replace that drive and rebuild the system without any data loss.  Am I misinterpreting how RAID5 works?

I agree it is less reliable than RAID10, but it can still handle 1 drive failure, right?

---

### Post by YesWeCan on 2011-02-28
Yes, it is capable of recovering a single disk failure. That doesn't mean it will. Because of its distributed parity system (which makes it capacity-efficient) recovering the failed disk requires that all the other disks read fully and perfectly. So this means that the more disks you have in the array the less likely it is to be able to recover. Unlike RAID 1+0 where there is only ever reliance on one disk. There are other risks with distributed parity systems such as undetected corruptions of parity blocks during power failures.

I am trying to scare you just a little bit :). I have noticed a general tendency for folks to assume RAID 5 is 100% likely to recover from a disk failure. It isn't. You'll probably be fine but I just don't want anyone to lose important data due to over-optimism. Do your own research.
Some experienced members I have come across here recommend backing up your data and using a UPS.

---

### Post by psusi on 2011-02-28
> **YesWeCan said:**
> Yes, it is capable of recovering a single disk failure. That doesn't mean it will. Because of its distributed parity system (which makes it capacity-efficient) recovering the failed disk requires that all the other disks read fully and perfectly. So this means that the more disks you have in the array the less likely it is to be able to recover. Unlike RAID 1+0 where there is only ever reliance on one disk. There are other risks with distributed parity systems such as undetected corruptions of parity blocks during power failures.


Now you are talking about a two disk failure, even if the second disk is only a partial failure.  A raid 1+0 may or may not be able to recover from that, depending on which disks failed.  That doesn't really make it ( appreciably ) more reliable.

And you should ALWAYS have backups, or it is not a question of if, but when you will loose data.  Raid is no substitute for backups.

---

