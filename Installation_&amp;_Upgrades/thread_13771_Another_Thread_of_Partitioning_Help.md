---
title: "Another Thread of Partitioning Help"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by schulermx on 2005-02-02
EDIT: I installed SuSe 9.2 in the unallocated space instead of Ubuntu  :?  but that worked fine. But feel free to put any ideas down here, it may help someone else with a similar problem.
---------------------------------------------------------------------------------------------------------------------------------

Hi, basically I'm trying to install Ubuntu along side Windows XP on my roommates computer  and I've searched the threads here and no one seems to have my particular problem.

Now right now I have Windows XP and Ubuntu both up and running however Partition Magic gives me some lovely errors whenever I try to load it up on Windows.

The errors look something like this:

```

PowerQuest PartionMagic has detect an error 116 on the partition starting at sector 666573360 on disk 1.

The starting LBA value is 66573360 and the CHS Value is 16435502.
The LBA and CHS values must be equal.
PowerQuest PartionMagic has verified that the LBA value is correct can can fix the CHS value.

Would you like PowerQuest PartionMagic to fix this error?

Yes No

```

And I click Yes...and it claims it fixes it. And several more errors of the same type come up. As well as a slightly different one

```

PQPM has detected and error 110 on the partition starting at sector 66573360 on disk .

The length of the partition int he table is incorrect.
THe CHS length is 11551743 and the LBA length is 11566800
PQPM has detemined that the length can be changed to the correct value of 11566800

```

To which I "fix" and then PM gives me the error
Init failed: Error 117

Partition's drive letter cannot be identified

Now I know that I've managed to get both operating systems running, but I don't like the idea of these errors on my Parition Table.

Now I've tried several different Partioning in the system (which is a 40GB harddrive).

I have a initial partition of about 32GB of NTFS for Windows. (primary)
I then have about a 4.9GB ext3 partition for Ubuntu (primary)
and then i have a 1GB swap (logical), The computer also has 512MB Ram.

Now i've tried multiple configurations of the Linux partitions, using  automatic settings from Ubuntu, having the swap before the ext3 etc etc, all of which, anger Partition Magic and give me similar errors.

Also, Partition Magic becomes happy when I go into computer management, Storage, and delete the ext3 and swap partitions which it thinks are healthy.

Now basically I'm looking for some way to Install Ubuntu, keeping the Windows installed, and keep my partition table errorless. I'm pretty much out of ideas.

I've installed SuSe 9.2 on my own computer with the following configuration that keeps everything happy:
A 20gig primary NTFS partition.
A 25gig extended partition thats labeled primary.
     With an NTFS in the extended partition, labeled logical.
A 1 gig swap space, primary
And  a 10gig ext2 (or ext3, I'm not sure) primary partition.

I think that about covers it. Also to note, the hard disk is in LBA mode. Thanks.

---

### Post by rudi on 2005-02-02
So if i understand you correctly Partition magic thinks that your windows partition is bad, but the ext3 and swap partition are good? Have you resized your windows partition or did you create a lay-out from scratch? It could be that there is a conflict with the actual used clusters for the NTFS partition and the clusters listed in the partition table resulting from resizing.

---

### Post by schulermx on 2005-02-02
I'm not sure what exactly Partition magic thinks is bad. From what I gather when I wrte the swap/ext3 partitions, something gets slightly screwy with the partition table giving me those errors.

What I had originally done before installing any Linux distrubution is flat out install Windows on all 40gigs (well more like 37.9) of the drive. Once that was done, I resized the Windows partition to approximately 32gigs and left the rest of the drive, 5.9 gigs unallocated. I then went from there.

Basically whenever I installed Ubuntu in that unallocated space, I would get the PM errors. When I deleted the partitions in which it was installed on, the error went away.

---

### Post by Xian on 2005-02-02
I've seen those PM errors before. To the best of my knowledge they can not be repaired without actually removing the offending partition(s). My suggestion since you have SuSE installed is to use the partitioner in YaST to manage your HD instead of PM. Both Ubuntu and SuSE use parted for this purpose and you will never get any disk errors like you are seeing from that particular application. 

It is impossible to surmise an exact reason without further information, but often those errors in PM are caused by a conflict between how the bios reads the disk geometry and the method that PM is using when writing to the HD. If you use only parted this will not be a problem, and since it will work on both windows and linux partitions you can use it for practically any purpose.

If you would prefer another GUI for parted instead of YaST then use qtparted.

---

