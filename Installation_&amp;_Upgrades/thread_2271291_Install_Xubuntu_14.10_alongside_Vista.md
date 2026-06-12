---
title: "Install Xubuntu 14.10 alongside Vista"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by Bernie_Marquardt on 2015-03-28
Am trying to install Xubuntu 14.10 alongside Vista. My situation is this: Have a Windows partition, an allocated space which I would like Xubuntu to use, and a recovery partition for Vista. So when I click ' Install alongside Windows' , it reports that it will use partitions sda4/sda5; how can I be sure it will not destroy my recovery partition? If I click 'something else', it goes back automatically to 'Install alongside windows', without allowing me that choice. How can I proceed? Thanks in advance for your help.

---

### Post by fantab on 2015-03-29
Lets look at your partitions, boot from Ubuntu DVD/USB and Try Ubuntu.
Open Terminal and run the following one after another:
```
sudo fdisk -l
sudo parted -l
```

... and post the output of the commands.

---

### Post by Bernie_Marquardt on 2015-03-29
Thanks, fantab. 


Here is the results:

                       Boot           Size          ID       Type
/dev/sda1            *           197.7G        7        HPFS/NTFS/exFAT
/dev/sda2                          450MB       27       Hidden/NTFS/WinRE
/dev/sda4                           11.1G       7         HPFS/NTFS/exFAT

Parted:
1   212GB   primary    ntfs     boot
2   472MB   primary    ntfs    diag
3   12GB     primary    ntfs

Hope that gives enough to work with. Did write down the starting sector/ending sector.

---

### Post by Bashing-om on 2015-03-29
Bernie_Marquardt; Hello;

Here's the deal. in the legacy - MBR - partitioning scheme there is a 4 PRIMARY partition limit. Windows is presently using 3 of those 4 possible partitions. ubuntu requires 2 partitions as a minimum to install. a partition for the 'root' filesystem and a 'swap' partition.
The way around this 4 primary partition limit is to make up one of those primary partitions as an 'extended' partition. This 'extended' partition is a container to hold addition 'logical' partitions. ubuntu is happy to install to these logical partitions.

I suspect that if you had of let the install wizard take control of setting up the partitions, it would have made up the 'logical' partition, and installed "along side of" Windows. As is now - and better in the long run - you have decided for yourself how you want ubuntu to install, and must make the provisions to utilize the "something else" install option.

At this time to aid us in further guidance, please provide a screen shot of what the ubuntu partitioner sees;
From the liveDVD in try ubuntu mode, activate 'GParted' from the dash. We can then see what the state of the hard drive is space wise. Is there "unallocated space" sufficient to install ubunto onto ?

[INDENT]ain't no step for a stepper
[/INDENT]

---

### Post by Mark Phelps on 2015-03-29
> an allocated space which I would like Xubuntu to use,

You can't use that space.  Allocated means already assigned to a filesystem, and looking at the command results, ALL your partitions are Windows filesystem -- which Xubuntu can't use for installation.

You're going to have additional problems if you start messing around with the partition sizes and spaces on your drive.  One problem is that the last partition is most likely your recovery partition.  IF you move or shrink that, you most likely will not be able to use the built-in recovery option anymore.  

The only partition that you could actually shrink (presuming there is room to spare) is sda1 -- but that is your Vista OS partition, and if that gets corrupted in any way, you will not be able to reboot into Vista -- making it very hard to fix.

So ... the very first thing you would need to do is do a full image backup of your partitions to an external drive. If you are willing to do that, then do the following:
1) Download and install Macrium Reflect to Vista
2) Connect your external drive
3) Run MR to do a complete backup of all your partitions to the external drive
4) Use the MR option to create and burn a Boot CD.  You will need this later if you need to do a restore from the external drive.

If you're not prepared or willing to do that backup, then my advice is to go no further.  Any OS installation and partition manipulation comes with the risk of overwriting and/or corrupting existing filesystems and data.  Without a backup, you would have no way of recovering if anything goes wrong.

---

### Post by Bernie_Marquardt on 2015-03-29
Thanks, bashing-om and Mark Phelps.
Here is the latest, as bashing-om suggested. When I click on 'install Ubuntu alongside Windows', here is what comes up:
The partition tables of the following devices are changed:
SCSI3(0,0,0) (sda)
The following partitions are going to be formatted:
partition #5 of SCSI3 (0,0,0) (sda) as ext4
partition #6 of SCSI3 (0,0,0) (sda) as swap

When I chose 'Something else', then it gives me these choices:

                               size              used
/dev/sda1   ntfs    212310 MB        65572 MB    Windows Vista loader
free space            25305 MB
/dev/sda2   ntfs       471 MB             235 MB
/dev/sda3   ntfs     11967 MB           8676 MB    Windows Vista loader

Device for boot loading:
/dev/sda       ATA ST3250310AS (250.1 GB).

Hope that gives some more ideas.

---

### Post by Bashing-om on 2015-03-29
Bernie_Marquardt; Hey ....

Like Mark advises, make a backup of Windows now. We do not know the state of the partitions and any time partitions are "changed" there is always that risk of data loss.
Before we make any additional advise, will behoove us to see what the hard drive situation is.
post back the screen shot from GParted depicting all the drives on the system.

Sorta as an aside; As you are a new user to ubuntu, I would expect the default set up that the install wizard (install along side) sets to be just fine good and dandy. But again, we do not know what might have been done that alters these Windows' partitions ! Once you are familiar with ubuntu if desired you can then re-partition more to your use case.

It is your system
[INDENT][INDENT]it is all up to you what you want to do
[/INDENT][/INDENT]

---

### Post by Bernie_Marquardt on 2015-03-30
Did the backup. Then I installed Xubuntu by using the freespace and partitioning it myself. Everything worked fine. I am able to get into Windows and into Xubuntu. 
Thank you all for your input.

---

### Post by Bashing-om on 2015-03-30
Bernie_Marquardt; Outstanding !

You do good work .

[INDENT][INDENT][INDENT]Welcome to our world
[/INDENT][/INDENT][/INDENT]

---

### Post by Bernie_Marquardt on 2015-03-30
Well, if it hadn't been for the tips of you guys, I would have been quite unsure on how to proceed.
Thanks also, bashing-om for the link on Help documentation.

---

