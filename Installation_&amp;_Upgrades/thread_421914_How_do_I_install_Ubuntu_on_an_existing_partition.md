---
title: "How do I install Ubuntu on an existing partition?"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by charliep8 on 2007-04-24
How do I install Ubuntu on an existing partition? In preparation to install Ubuntu and finally migrate to Linux I partitioned my hard drive with the following partitions:

Windows XP NTFS 27 GB
Data NTFS 105 GB
Ubuntu Ext3 12GB
BackTrack Ext3 4 GB
Linux Swap 600MB (1G of RAM in the computer)

I installed Windows, then BackTrack, and all was okay. Then I went to go and install Ubuntu and when it gets to the part where it wants to detect the partition it wants to reformat my entire hard drive, which is not good. I treid deleting the partition for Ubuntu and leaving 12 GB of free space on the drive, this still doesn't work. Ubuntu would still not see the free space and wanted to format the entire drive. How do I get Ubuntu to install on a particular partition? Is there some way I can mount to that partition before I install so the Ubuntu installation procedure can recognize and install to the existing partition?

---

### Post by raja on 2007-04-24
You should choose to do the partitioning manually. Then you will be able to use the partition you want to install Ubuntu.

---

### Post by johnc4510 on 2007-04-24
raja gives sound advice, but also remember not to format the other partitions, or you will lose data. Only format ubuntu partition and the swap partition.

---

### Post by charliep8 on 2007-04-24
I did choose to do the partitioning manually, but when I press next Ubuntu does not recognize that the hard drive has already been partitioned, and it wants to format the entire drive, which is not good. That is why I am wondering if there is a way to mount the drive to be installed on first or whether I can install in a more command line fashion.

---

### Post by charliep8 on 2007-04-25
Is there a work-around for this???

---

### Post by pepsi_max2k on 2007-04-25
see [http://ubuntuforums.org/showthread.php?t=413745](http://ubuntuforums.org/showthread.php?t=413745)

---

### Post by charliep8 on 2007-04-26
Thanks a lot for that link. TestDisk is a DOS partitioning utility that is ... a little bit less user friendly than Linux. But at least it steered me in the right direction. If Ubuntu is not installing on your partitions it means that there is an ERROR in your partitions. In my case it was because I used Acronis Disk Manager to edit my hard drive partitions. Acronis actually allowed me to create 5 primary partitions, which is ... not allowed. 

So I deleted the primary partitions and created logical partitions and everything worked just fine. I actually downloaded and installed PartitionMagic to do this, but I think you could probably do it with Acronis as well.

Anyway, installation progressed fine until I got to the Prepare Partitions page. I already had all my partitions ready to go and it is asking me:

You need to specify a partition for the root file system (mount point "/") with a minimum file size of 2GB and a swap partition of at least 256MB. You may also set up other partitions if you wish.

So I clicked on the partition that I wanted to install Ubuntu on and for the "Mount Point" option I clicked on the dropdown arrow and selected "/". And then clicked OK. I checked the "Format" box for the partition I wanted to use and clicked on Forward. So Installation would progress

Ubuntu was giving me a hard time about my cluster size (16KB instead of 4KB). Finally I just deleted the partition I had created for Ubuntu using PartitionMagic and then let Ubuntu create its own partition with the same size. STILL I got this message, so I just clicked "ignore" and proceeded. It looks as though the installation will progress normally.

Hope this helps some people out there! If you find this useful leave a comment!

---

### Post by charliep8 on 2007-04-26
Thanks a lot for that link. TestDisk is a DOS partitioning utility that is ... a little bit LESS user friendly than Linux. But at least it steered me in the right direction. If Ubuntu is not installing on your partitions it means that there is an ERROR in your partitions. In my case it was because I used Acronis Disk Manager to edit my hard drive partitions. Acronis actually allowed me to create 5 primary partitions, which is ... not allowed. The maximum allows is 4.

So I deleted the primary partitions and created logical partitions and everything worked just fine. I actually downloaded and installed PartitionMagic to do this, but I think you could probably do it with Acronis as well.

Anyway, installation progressed fine until I got to the Prepare Partitions page. I already had all my partitions ready to go and it is asking me:

> You need to specify a partition for the root file system (mount point "/") with a minimum file size of 2GB and a swap partition of at least 256MB. You may also set up other partitions if you wish.

So I clicked on the partition that I wanted to install Ubuntu on and for the "Mount Point" option I clicked on the dropdown arrow and selected "/". And then clicked OK. I checked the "Format" box for the partition I wanted to use and clicked on Forward. So Installation would progress

Ubuntu was giving me a hard time about my cluster size (16KB instead of 4KB). Finally I just deleted the partition I had created for Ubuntu using PartitionMagic and then let Ubuntu create its own partition with the same size. STILL I got this message, so I just clicked "ignore" and proceeded. It looks as though the installation will progress normally.

Hope this helps some people out there! If you find this useful leave a comment!

---

### Post by dsilvia on 2007-04-26
> **charliep8 said:**
> Thanks a lot for that link. TestDisk is a DOS partitioning utility that is ... a little bit LESS user friendly than Linux. But at least it steered me in the right direction. If Ubuntu is not installing on your partitions it means that there is an ERROR in your partitions. In my case it was because I used Acronis Disk Manager to edit my hard drive partitions. Acronis actually allowed me to create 5 primary partitions, which is ... not allowed. The maximum allows is 4.

So I deleted the primary partitions and created logical partitions and everything worked just fine. I actually downloaded and installed PartitionMagic to do this, but I think you could probably do it with Acronis as well.

Anyway, installation progressed fine until I got to the Prepare Partitions page. I already had all my partitions ready to go and it is asking me:



So I clicked on the partition that I wanted to install Ubuntu on and for the "Mount Point" option I clicked on the dropdown arrow and selected "/". And then clicked OK. I checked the "Format" box for the partition I wanted to use and clicked on Forward. So Installation would progress

Ubuntu was giving me a hard time about my cluster size (16KB instead of 4KB). Finally I just deleted the partition I had created for Ubuntu using PartitionMagic and then let Ubuntu create its own partition with the same size. STILL I got this message, so I just clicked "ignore" and proceeded. It looks as though the installation will progress normally.

Hope this helps some people out there! If you find this useful leave a comment!

Well, my problem was a bit different, but this thread helped and I finally got 7.04 installed. Some comments I'd like to make for others:

My problem was that my Linux Swap partition was hosed (I think by Kubuntu). I stopped using Partition Magic because it's quality had gone downhill. Since Symantec bought out Peter Norton, they've been riding on his reputation, but not keeping up his level of quality. I found a much better product from Paragon Software in Germany (a lot of good products coming out of that country for Windows. TuneUp Utilities is another). It's called Partition Manager (I have the Partition Manager 8.0 Server Edition). It showed my Linux swap as an Invalid partition type. The above mentioned TestDisk similarly said it was unrecoverable. I ended up deleting this partition in Partition Manager then recreating it. Partition Manager only does Linux Swap2, but that was fine. Once this was done, the partition table came up fine in the install.

One other comment. Isn't it kind of brain dead that Gparted (or whatever utility the install uses to get the partition table) won't show anything unless everything is perfect? No other partition utility I know of does this: DiskPart (Windows), TestDisk, Partition Magic, Partition Manager, and others all show what is valid and just note that the one (however it's labeled) is screwy. Shouldn't the Ubuntu disk partitioner do the same?

thx,
Dave S.

---

