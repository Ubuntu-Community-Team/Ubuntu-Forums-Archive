---
title: "problems with partitioner/install with sata"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by shinsplints on 2006-06-07
Since I found some spare time, I decided to install Dapper.  Everything was going smoothly, I was especially impressed with the move to a live CD for an installer, but when I get to stage 5 the problems start.  I searched the forums and stickies for my problem but didn't find anything.

important background:
I'm trying to install to a sata drive- sda.  There's only 1 drive, no raid (I know people were having trouble if multiple drives were installed).  I have 2 ntfs partitions installed.  Windows is installed on hda1, and the other is hda5 on a logical partition (that's what Windows did when I installed it).  I had installed archlinux but just wasn't feeling it, so I then made a 2gb partition for swap on sda3 and a root partition on sda4.  For whatever reason, sda2 was unavailable to me.

So now the problem:
I didn't want to just blow away the entire partition, so I chose to edit the partition table manually.  The installer, however, does not recognize the partition table and instead presents the entire hard drive as unallocated space.

Trying to get around the problem, I simply chose forward to go to "Prepare mount points."  At this point the installer did in fact recognize the partitions, so I set sda3 to be swap and sda4 to be / and chose to reformat both.  Expecting this to work I hit forward and then install.  After very little time I am presented with a dialogue box with a big error sign telling me "no root file system."

So... is there some way to get the partitioner to see the partition table so that I can set things up correctly?  Failing that, is there any way I can force ubuntu to see sda4 as my root filesystem?

Thanks

---

