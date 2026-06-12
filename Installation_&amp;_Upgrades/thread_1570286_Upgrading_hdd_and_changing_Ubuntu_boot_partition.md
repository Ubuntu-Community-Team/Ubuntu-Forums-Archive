---
title: "Upgrading hdd and changing Ubuntu boot partition"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by GROwen on 2010-09-07
Hi all,

I'm looking for some advice on how best to reconfigure my Ubuntu machine.

Currently I have a 1TB drive that has Ubuntu installed and is used for all of my storage, vids music etc.

After speaking with a friend he suggested I change the operating system to a smaller drive and use the 1TB for storage only. His reasoning for this is that the disc with the OS on it receives much heavier use so storage should be kept separate.

If that's true I have a 250GB drive that I could use as the boot/OS drive.

What I was considering doing was to make the 250GB drive the boot disc in BIOS, then install Ubuntu from the Live CD onto the 250GB.

After doing that my plan was to use gparted to wipe the Ubuntu OS partition off the TB drive to leave it as a storage only drive.

Am I right in thinking this will work, or is there a better practice method (I think I know the answer to that already)?

Thanks in advance for any help you can give me with this.

---

### Post by oldfred on 2010-09-08
I very much agree with keeping system partitions separate from data partitions.  I have several system partitions of about 20-25GB with 6GB used and all my data in /data and /shared which is NTFS to share with my XP install. My systems are 9.10 - previous,10.04 - current & 10.10 - testing, so I do not lose old settings until my new if fully configured, and I have the next to test & eventually configure.

But some like an operating system on every drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

I do have my operating systems on separate drives. I have 3 drives and 4 systems with data and systems on each drive.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by GROwen on 2010-09-08
Thanks for the response oldfred.

Just to clarify when you say

 > I have several system partitions of about 20-25GB with 6GB used and all  my data in /data and /shared which is NTFS to share with my XP install.

Does that mean you have several system partitions and data on the single drive? And if so, is this sufficient to keep data safe from HDD failure that  could have been avoided if it had been on a separate drive that didn't  run an OS?

When doing a fresh install of Ubuntu can you create a system partition and have the rest of the drive as a separate partition, adjusting partition size using the installer? 

If that's the case then maybe I don't need to worry about swapping the boot partition for the OS to a smaller drive, I could just reduce the partition that it's sitting on to 20GB and have all the data on a separate partition. But is this good enough protection?

The way I'm imagining it to work is I have two harddrives in the machine but one's just storage and the others the OS and less important files, the OS could also back up to the TB. Or is all of that a bit of overkill?


Thanks again,

---

### Post by oldfred on 2010-09-08
When I got my new 640GB drive a year or so ago I realized I wanted more than one system. I originally set it up with 3 25GB root (one still not used) partitions, a 100GB /home and some unallocated initially until I decided what I wanted to do with it. So I split off /home with all its data into a new partition and did a new system install on that drive. I kept the old install on one of my two other smaller drives (that now has Maverick for testing). But I then decided to have a separate /data partition so I could use all the data in every system partition without any issues whereas /home may have issues. You can use the same /home on an upgrade but not for different systems and I was not sure about both old and new systems at the same time. After I moved all my data out of /home it was only about 1GB of mostly hidden files & folders. I now have moved /home back into my newest system partition as it is easy to backup and copy to a new system.

Backup is important but if I have a major crash I am not worried about system partition. I back up /home, installed program list & some system settings from /etc. I will just reinstall a new system and restore data and settings. I can boot any of my three drives, two USB installs, one full install & another ISO boot of several Ubuntu & recovery systems and liveCDs. 

I backup my most important data to DVD's. Most data that I can recover by reripping or redownloading I only backup occasionally. Some data is on different drives or backup partition on different drive and/or flash drives.  I assume every 2 or 3 years I will buy a new drive and the older one(s) then is on line backup (although probably less reliable).

---

