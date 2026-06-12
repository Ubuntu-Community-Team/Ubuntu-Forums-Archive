---
title: "Has Ubuntu installer fried my SSD?"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by Mr.Mincepie on 2011-05-14
Hi everyone, I really hope you can help.

I have an Aspire One ZG5, with a solid state drive, one of the first Aspire Ones to come out.  I have been happily running linux on this for several years including Ubuntu until one version stopped recognising my wifi.  I have recently been using Mandriva.

Anyhow, today I thought I would install 11.04 and booted into Mandriva 2010 to copy some files to a USB.   On my main desktop I downloaded the .iso and installed it onto another USB drive.  I booted my aspire one and decided to try Ubuntu first without installing.   After playing around a little and checking that my wifi worked, which it did, I decided to install.

Half way through copying the files the installer crashed.  When I rebooted and pressed F12 to choose the USB there was no SSD listed.  I continued nevertheless but found when installing that it couldn't find the SSD. Where the installer checks for internet connection and power supply, the drive option was greyed out with a cross next to it.

I thought I'd try my Mandrake USB and when I ran the partitioning tool it listed the SSD.  Great I thought except that when I tried to format the SSD it said it could not mount sda1.

Has Ubuntu fried my SSD?  I should point out I am not a technical user.

---

### Post by insane_alien on 2011-05-14
it is unlikely that ubuntu was the cause. 

it could have been hardware failure(solid state components CAN fail) which is what it sounds like.

the only thing ubuntu could have done to break your SSD would be to cause excessive writing. but this would cause a slow degradation of capacity rather than a up and stop working failure.

although saying that it may still be a software thing, try using super grub disk

---

### Post by dabl on 2011-05-14
I'm running Linux on 3 computers that have a total of 4 SSDs in them, for several years.  It is very unlikely that Ubuntu itself did anything to the SSD.  If it has indeed failed, it was inevitable that something would be the "last event before it died".  Just because the Ubuntu installer was last running on it doesn't make Ubuntu any more destructive than Windows or OS/X or MS-DOS.

The recent generation of SSDs (one million write cycles) are considerably more durable than the earlier models.  Previously, it was a good idea to minimize the writes in the areas where the logs and filesystem journals are updated multiple times per minute.  I still do that, although according to the specs, the new SSDs will last well beyond their technological desirability (new ones becoming available will be far larger and faster, before the old ones wear out).  So, you can do things in /etc/fstab like:

none                                          /tmp                 tmpfs        defaults,noatime,mode=1777 0 0
none                                          /var/tmp             tmpfs        defaults,noatime 0 0
none                                          /var/log             tmpfs        defaults,noatime 0 0 
none                                          /var/spool           tmpfs        defaults,noatime 0 0 

and also set the "commit=" option on ext4 to something like 300 (5 minutes) or 600 (10 minutes), depending on your taste for risking data loss.

In your case, I would attempt to "dd" that drive, and make a new partition table and filesystem, and try a new installation on it.

---

### Post by Mr.Mincepie on 2011-05-15
Thanks for the advice.

I have got some way.  My bios now detects the SSD and using the llive USB, gparted now sees it.  I have deleted all the partitions on the drive and created two new ones, a primary partition and a small swap.

I cannot however create an ext4 filesystem on partition 1.  This is the readout from Gparted.


                                 [I]"GParted 0.7.0 --enable-libparted-dmraid
 
 Libparted 2.3
 Format /dev/sda1 as ext4  00:00:37    ( ERROR )

 calibrate /dev/sda1  00:00:00    ( SUCCESS )[/I]           [I]

 path: /dev/sda1[/I]           [I]
 start: 2048
 end: 29450239
 size: 29448192 (14.04 GiB)
 set partition type on /dev/sda1  00:00:01    ( SUCCESS )

 new partition type: ext4[/I]           [I]
 create new ext4 file system  00:00:36    ( ERROR )

 mkfs.ext4 -j -O extent -L "" /dev/sda1[/I]           [I]

 Filesystem label=[/I]           [I]
 OS type: Linux
 Block size=4096 (log=2)
 Fragment size=4096 (log=2)
 Stride=0 blocks, Stripe width=0 blocks
 920272 inodes, 3681024 blocks
 184051 blocks (5.00%) reserved for the super user
 First data block=0
 Maximum filesystem blocks=3770679296
 113 block groups
 32768 blocks per group, 32768 fragments per group
 8144 inodes per group
 Superblock backups stored on blocks:
 32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208


 Writing inode tables: done[/I]   [I]
 Creating journal (32768 blocks): done
 Writing superblocks and filesystem accounting information: done


 This filesystem will be automatically checked every 27 mounts or[/I]   [I]
 180 days, whichever comes first. Use tune2fs -c or -i to override.
 sh: getcwd() failed: No such file or directory
 mke2fs 1.41.14 (22-Dec-2010)


 Warning, had trouble writing out superblocks.[/I]   *"*
 
Unfortunately not being a technical user I don't really understand what I'm looking at. Hopefully it will give some pointers to what, if anything, can be done.  I some so as I really can't afford a new laptop just now.

Any pointers?

---

### Post by dabl on 2011-05-15
Boot a Live CD. Open a terminal.

```
sudo fdisk -l
```

be sure you know the ID of the SSD.  Let's say for the purpose of this discussion it is /dev/sda.  In your terminal window:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```

Now your SSD has no partition table and no filesystems.  Boot your Live CD and use gparted to go to Device > New Partition Table and make a new MS-DOS partition table.

Then use the partitioner to make a new ext4 partition, and a swap partition.

---

