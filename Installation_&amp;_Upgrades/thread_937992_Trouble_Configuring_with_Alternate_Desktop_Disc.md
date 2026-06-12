---
title: "Trouble Configuring with Alternate Desktop Disc"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by madhartigan on 2008-10-04
I'm trying to set up RAID while installing a desktop. When I get to the Partition Disks section of the Alternate Desktop Disk I have some problems.

The first thing I do is go through and select all of my disk's sd* heading and say 'yes' to the "Create new empty partition table on this device?" question.  Once all of my disks show as 'FREE SPACE' I go to the first disk of my intended RAID 1 pair and I create a new partition.  They're both WD 320GB Caviars.  

1)I set the New partition size as '320.1 GB'
2)I set the "Type for the new partition:" to 'Primary'
3)I set "Use as:" to 'physical volume for RAID
4)I select "Done setting up the partition"

I do the exact same thing for the other WD 320GB Caviar.

Then I go to the "Configure software RAID" option.

I say 'yes' to the "Write changes to the storage devices and configure RAID?" question.

I then select "Create MD device".

I select RAID1 for the type.

At this point the install tells me:

> 
[center]No RAID partitions available[/center]
No unused partitions of the type "Linux RAID Autodetect" are available. Please create such a partition, or delete an already used multidisk device to free its partitions.

If you have such partitions, they might contain actual file systems, and are therefore not available for use by this configuration utility.


I don't know what to do.  I've used the gParted Live CD in an effort to set these drives as unformated and it does no good.  I tried doing this with the Server Install disk as well and I get the same result.

I'd love any help on this.

---

### Post by Herman on 2008-10-04
:D Hello madhartigan,
It looks to me as if you are doing everything correctly from reading your description of what you're doing. 
There's an excellent video available which takes you through the steps for setting up software RAID with the 'Alternate' CD, [*Installing Ubuntu Part 2* | *Ubuntu* Screencasts]("http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2"). Have you seen it?
Most likely the problem is something small and easy to miss. 
If you watch that video with totem movie player in Ubuntu you can of course pause it with your space key and advance it or go back with your arrow keys. (If you have Ubuntu in another computer I mean).
Maybe you will be able to pick any missing steps in the procedure that way.

Regards, Herman :D

---

### Post by cariboo on 2008-10-04
Also have a look at this howto:

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

Jim

---

### Post by madhartigan on 2008-10-04
Well, I've gone and installed the standard desktop installation and during that installation I formatted the RAID disks as regular ext3 disks that were not mounted.

I'm hoping that, by doing that I've removed any remnants of the previous configurations that those disks have possibly retained (ie: "they might contain actual file systems" from the RAID configure error I was getting) and allowed those disks to be configured appropriately.

I appreciate the suggestions both of you have provided and I hope that this new endeavor yields better results.


THX AGN

---

### Post by madhartigan on 2008-10-04
Sorry for the double post but . . . .

For starters, here's the config that I've been working with:

1x 74GB Raptor
2x 320 GB Caviars
2x 1000 GB WD?

Regardless, this time, after installing using the standard Ubuntu install disk and setting the 74GB Raptor as the system disk and the rest as unmounted ext3 disks everything was fine.

I went to the Alternate Desktop install disk and tried to configure the RAID and everything went fine.  The one thing (other than the "fake" install with ext3 unmounted drives) that I did differently was to configure the 74GB Raptor as the system drive FIRST before I tried to setup any of the drives for "physical volume for RAID".

I think that my "fake" install trying to "reset" the drives back to ext3 drives was irrelevant.  I think the main issue was that there was no root nor swap partition available and therefore the install couldn't reference any mdadm functions or whatever the "Alternate Ubuntu Install" disk needs to configure RAID.

Just a theory but, I have a feeling that it's accurate.

The fantastic benefit of this ability is I now have the following configuration:

2x 320GB drives in RAID1  for my /var directory, thereby creating redundancy for my 'MySQL' and 'WWW' directories.

2x 1.0TB drives in RAID0 for my /home directory, thereby creating high speed throughput for my remote users and massive storage for acceptably volatile information. (bi-weekly updates to another site)



Thank you again for the support!!

ADD: I had troubles using the Alternate CD (something about a bad image) so I'm now trying the server disk to see how that works.

ADD2: NM  I had the same troubles that I did initially with this attempt at using the server disk.

I followed the same process I detailed earlier as well as including the "establish /swap and /" first before trying the RAID.

I'm at a loss . . .

---

### Post by madhartigan on 2008-10-05
bump


Still having the same troubles.

I set the both of the drive's partitions to be "physical volume for RAID" but the they're not seen by the "Configure software RAID" section of Partition Disks.

I've tried everything I can imagine.

---

