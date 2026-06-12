---
title: "Data on other partitions disappears after 8.04 installation"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by cius on 2008-04-27
I have two hard drives in my system.  One has three partitions on it (windows, ubuntu, swap) and the other has one ext3 partition for backup purposes.

Before installing 8.04, I booted into my installation of 7.10, downloaded the .torrent file, downloaded the iso using it, burned the cd, then promptly backed up my entire home directory to my backup hard drive.

During the 8.04 installation, I chose to do a manual partition of the hard drive. I had windows installed on sda1, ubuntu on sda2, and sda3 was swap.  sdb1 was my backup drive. I edited the sda1 entry and changed it from 'Do not use this drive' to 'ntfs' and told it to mount as /media/windowsxp. I changed the entry for sdb1 from 'Do not use this drive' to 'ext3' and told it to mount as /media/keep. I then deleted the sda2 partition and recreated it, telling it to format as ext3 and to mount as /.

After the 8.04 installation, I opened sdb1, my backup drive in order to restore my home directory and found it to be empty! I turned on View->Hidden files and found that the only thing in the directory was a .Trash directory.  This directory contained the .torrent file I used under 7.10 to download the iso, but nothing else. I checked the modified timestamp on the file and saw that it was for yesterday when I downloaded the .torrent file.  I did not burn the iso and install until this afternoon.  

I can't see any of my backup files.  Nor can I see any files on my windows ntfs partition.  I also do not have an entry in menu.lst for my windows installation.

Has anyone had this problem or any advice how to troubleshoot it?  Is all of my data gone?  I DID NOT tell the installer to format these drives.  If I had, why would the .torrent file show up in the .Trash directory on my backup drive? 

I did not have a separate /home partition so my backup drive was the only copy of data I've created in the last few months. I'll certainly be going back to a separate /home partition model as soon as possible though.  I just want to try everything I can to salvage my data before resolving myself to the loss and reinstalling/repartitioning.

Any help would be appreciated.

---

### Post by martrn on 2008-04-27
I recommend you download and look at [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/") to look at and find what partitions you currently have.  

Personally in the past when installing I have found it best to partition the drives separately, and then install a distribution (such as ubuntu) to the partition I have created for it.

Changeing "Do not use this drive" to "ntfs" in the ubuntu installer means changing the partition table of the drive from its default so even though you might say "I DID NOT tell the installer to format these drives", you have told the installer to change the partition tables.

This is not the most recommended thing to do is to tell the drives you do not want it to touch to >> Do not use this drive <<, and install ubuntu to the one you do not mind it reading / writing to.

Any partition tables you have changed can be changes back, any read/write access to the the disk after you have changed the partition tables then you can wave goodbye to the data or look for data recovery software.

---

### Post by cius on 2008-04-28
Thanks for the reply martrn.  I chose my actions based upon prior experience with the ubuntu 7.10 installation.  In that installation I could tell the installer how I wanted my other partitions mounted and as long as I didn't tell it to format it would merely put an entry in fstab so that my drives were available to me upon first boot.  The Gutsy installation also detected my windows installation and put an entry in the grub menu.lst file for me automatically.

After installing Hardy, I had to manually add an entry for windows xp and now it won't boot windows because of an 'NTLDR missing' error.

It looks like the installer may have deleted everything on the partitions I told it to mount even though I DID NOT tell it to format them!  My only problem with this conclusion is the existence of the .torrent file inside the .Trash directory on my backup drive.  Why would this directory and file from my 7.10 installation remain while everything else was deleted?

More importantly, why would the installer's default behavior be to delete all data on partitions that it is given permission to use?  What sense does it make to assume that the user wants everything deleted?  I specifically DID NOT delete and recreate those partitions, NOR did I tell it to format those partitions, only my root partition, and I told it exactly where I wanted those other partitions mounted!  Why would the installer's behavior change so drastically between releases?

If it did indeed erase my data then I would file this as a critical usability bug!  I plan to look more into this tonight.  If anyone has any further recommendations, please feel free to chime in.

---

### Post by cius on 2008-04-28
I'm considering this topic closed.  It doesn't seem like anyone else had this problem, so I assume its some sort of anomaly.  I'm gonna take the hit and start over from scratch.  I'll just be very cautious about upgrading in the future.  And I'll be absolutely sure to have two or three backups of everything from now on.

---

### Post by damis648 on 2008-04-28
This does not seem to be an anomality, from the symptoms you describe:
[http://ubuntuforums.org/showthread.php?t=773235](http://ubuntuforums.org/showthread.php?t=773235) however i have not reviewed this throughly...

---

### Post by cius on 2008-04-29
Thanks for the link Damis648.  That guy only seems to have one part of my problem though (XP not booting).  He hasn't said anything about looking at the partition and finding all of his data disappeared.

I'll keep an eye out for possible solutions, but I'm not hopeful at this point.  I reinstalled last night and blew away my former windows xp partition, but I left my backup drive as it was.  I left the 'Do not use this drive' option as it was this time, so if by some miracle my data is still there, maybe I can recover it.  I'll try the super grub disk tonight.

---

