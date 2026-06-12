---
title: "Ubuntu 6.06 Install buggy?"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by finalzero on 2006-10-11
Hi,

Seemed to have encountered an annoying feature in the Ubuntu graphical install process.

I am installing Ubuntu on to an existing system on which I have allocated two primary partitions for Ubuntu, my disk structure is as follows:

[hda]
   - hda1  -  Primary NTFS  (Windows XP)
   - hda2  -  Primary NTFS
   - hda5  -  Logical NTFS
           hda5  -  NTFS
           hda6  -  NTFS
           hda7  -  NTFS
   - hda3  -  Primary EXT3 (Ubuntu - unallocated)
   - hda4  -  Primary Swap (ubuntu - unallocated)

During the setup when prompted, I selected HDA and then selected the option to use all of the available free space for Ubuntu.

However I found the setup decided to create a swap parition in the Logical  partition and then a primary ext3 for the / root installation.  Obviously this is wrong so I restarted the setup and this time selected Manual Partition Table edit option.

I created two primary partitions as per above and set the type as ext3 and Linux-Swap respectively.  This caused some problems hoewever as the screen that follows would not let me assign the two partitions reporting that I could not have two / root partitions.

I was not able to deselect the format option and I think this is why the installer gets confused and fails to continue.

To remedy this I had to recreate the two partitions but this time unallocate them so the installer is then able to continue correctly.

I think this area of the installer needs some work as its obviously not working as it should be i.e. recognising that the user has selected a partition type and then going with that option.

Thanks,

Fz

---

