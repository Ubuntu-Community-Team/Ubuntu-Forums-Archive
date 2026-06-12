---
title: "Wiped disks on upgrading"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by Barrasmara on 2010-01-07
I need some help.

My computer has two large media disks, connected in a RAID1 arrangement.  I have just upgraded from 9.04 to 9.10 and the disks have been wiped.  I thought it would be a safe thing to do - I have moved from 8.04 to 8.10 to 9.04 with no problems.
Is there any way to recover the data that was on the disks?  I had hundreds of gigs worth of pictures on there including my wedding!  Money is not an issue, a paid solution would be fine.

Any advice is appreciated!

---

### Post by drrakken on 2010-01-07
Try getDataBack. I've had reasonable success with this software. That's of course if you have asccess to another computer

---

### Post by theDaveTheRave on 2010-01-07
Barrasmara,

That seems like a very strange occurance? 

What have you done to check the integrity of the disks and confirm that everything has gone south?

Are the disks still being correctly recognised? if not could it be their UUID's have mysteriously changed (it's happened to me previously on a multiple disk pc).

I'm guessing that you didn't receive any 'warning' messages when you where upgrading? - as you would obviously have aborted the process. This seems even more worrying.

Lesson for all of us here I think. remove important disks before upgrading. Obviously if you had them in RAID format, you would expect to have "failsafe" built in.

I don't understand how this could occur. It suggests that everyone with a separate home directory is at risk of loosing thier personal data - which in my mind was the whole point of having a separate home directory!

I hope someone out there can help you out to get the data back.

If the system actually "re-formated" the disks then I fear you may be out of luck however.

Maybe it has only formated one of the 2? try connecting just one at a time. could there be an integrity error between the 2 sets of data and hence nothing is showing up?

David

---

### Post by Barrasmara on 2010-01-07
It still shows that the disks are there, just that there is nothing on them.  I tried going through Nautilus, then used the disk usage analyzer.   

The upgrade did say something about removing unnecessary packages (which I assumed was completely normal) but nothing about wiping anything else.

I'll try looking at them one at a time and let you know if I have any success.  Thanks for your help.

---

### Post by Barrasmara on 2010-01-07
I've looked at the disks using Palimpsest disk utility - it is still seeing the disks there but says that they are not partitioned?!  I also took one of them out to see if that would change anything but, predictably it did not.

What is the next step?  Is there a neat way to recover the partition?  It was formatted in ext3 if that makes any difference.

---

### Post by kansasnoob on 2010-01-07
Put all the drives back in as they were, then DO NOT boot again from the hard drive but rather boot an Ubuntu Live CD (9.04 or prior hopefully) and begin to look at things.

I'd start just by looking in Gparted (aka: partition editor just to see what it shows as far as amount of disc/partition used, amount free, etc. DO NOT format or change anything!

If there appears to be space "used" on those drives/partitions the problem may not be as extreme as you suspect. Still using the Live CD you may be able to just navigate to Places > Removable Media or Places > Computer and see what's actually there or not there.

If things appear to truly be wiped then look into PhotoRec and TestDisk:

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by Barrasmara on 2010-01-08
I had a look at in in Gparted.  It said that the disk was completely unallocated.

I then did the following.

sudo lshw -C disk
  *-disk
     descrpition: ATA Disk
     product: SAMSUNG HD103UJ
     physical id: 0.0.0
     bus info: scsi@1:0.0.0
     logical name: /dev/sda
     version: 1AA0
     serial: S13PJ1BQ807868
     size: 931GiB (1TB)
     configuration: ansiversion=5

sudo swapoff -a
sudo parted /dev/sda
(parted) rescue
   Error: /dev/sda: unrecognised disk label
(parted) print
    Error: /dev/sda: unrecognised disk label



Is the data gone?  How could the disk have lost its label or partition?  Is my next step Photorec or TestDisk, or am I missing something obvious that I should do first?

Thanks, Matt

---

### Post by Barrasmara on 2010-01-09
I burned of the Ubuntu-rescue-remix cd and had a go with testdisk.  It said that *"Partition sector* doesn't *have the endmark* 0xAA55".  I am really out of my element here - what do I do next?  The disk is one partition, not a boot disk and was in ext3 format.  What has gone wrong, what do I do next?  

Any help would be greatly appreciated.

Thanks,

Matt

---

### Post by theDaveTheRave on 2010-01-19
Barrasmara

Have you been able to get any further with this issue??

I assume that you have been able to examine things with the "recovery" cd as you said.

With regards to the disk label problem.

If you hunt down the /etc/fstab file on the main partition (when booting into the "main" system.

this should tell you what the disk labels are for the disks that you have. I am wondering if you have an issue with the raid controller (are the disks in "mirror" or "stripe" format?)

If they are stripped, and the data on one has gone then you ay have lost the lot (sorry), unless the reason that the second disk is "failing" is due to some raid controller problem.

Have you investigated the RAID controller that you are using (is it a "software" raid ?).

sorry your problem seems to be a bit "specialist", and it all depends on the type of RAID array that you had implemented. Currently I am assuming that you had a RAID 0 (disk striping) setup, hence the loss of data integrity. 

Unless you had specific requirements for a RAID 0 (access speed), it may have been more advisable to have had a RAID 1 (mirroring) setup - it gives a kind of backup also, and a slight performance advantage.

Sorry I'm not really of much use here.

David

---

### Post by viper250 on 2010-01-19
If you had specified raid 0 and a drive failed to initialize your data would have been severely corrupted and unreadable.
with the speed of todays computers there is no need to set raid 0 ( raid 0 allows faster access to the data because it is spanning the data to multiple drives) raid 1 is mirroring the data on another drive or drives This results in slightly slower access but much better file integrity as errors are automatically corrected for you.
If a mirrored drive fails you can still access the data from the good drives:P
It sounds like the partitioner wiped the drives on you 

also you can try puppy linux I have had good results recovering files with it

---

### Post by Barrasmara on 2010-01-20
It was a mirrored RAID 1 set up, not a software RAID either.  I've sent one of the drives off to a data recovery centre.  I think it will be a 2 second job for them that will cost me £150, but there you go.  If I knew what I was doing then I'd be a bit more bold about trying stuff with the remaining disk but I really don't have much of a clue about this kind of thing.

Thanks for the help, I appreciate it.

Matt

---

