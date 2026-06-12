---
title: "Installing Ubuntu side by side to Windows 7 for an HP Pavillion Elite desktop"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by Nick42 on 2011-07-04
Hello,

I've just recently purchased an HP Pavillion Elite desktop. Product information is here: [http://tinyurl.com/5srv769](http://tinyurl.com/5srv769)

It comes with Windows 7 installed but no Windows Installation CDs/DVDs. You can create recovery DVDs or a recovery USB flash drive though.

I would like to install Ubuntu side by side to Windows 7.

The desktop has one 1 TB hard drive. It's partitioned into three parts, SYSTEM, OS and HP_RECOVERY. In Disk Management tool here are the information for the partitions:

SYSTEM - no drive letter assigned - 100 MB NTFS System, Active, Primary Partition)
OS - C: - 915.79 GB NTFS (Boot, Page File, Crash Dump, Primary Partition)
HP_RECOVERY - D: - 15.62 GB NTFS (Primary Partition)

What would be the best way to install Ubuntu on this desktop?

Thanks in advance!

---

### Post by xrhettx on 2011-07-04
Hi there. I've spent the last six months messing around with dual and triple ( OSX ) boots. It's great that windows is already installed; create some recovery discs. You're better off with them then without them. ; ), using windows free up a partition on your hard drive ( start, search for partition and go from there ); then use an ubuntu install disc and boot into it and install it to the partition you freed. Ubuntu will install grub (boot loader) over windows boot loader. It will work as long as you don't erase any important data!

Occasionally I've had to install windows after linux. It's a more difficult because when windows installs it overwrites the GRUB boot loader. One needs the GRUB boot loader to choose between operating systems after BIOS boot (usually, not always! ).
Good luck. Msg me with any questions.

---

### Post by Nick42 on 2011-07-04
Thanks dude for the fast reply!

Any tips on how to avoid GRUB screwing up Windows?

I suppose then I will shrink the OS partition and create a new partition there. Any restrictions there? I remember at some point Linux was requiring one certain partition should start at a certain MB/GB less than a value.

Also, I remember creating more than one partition for Linux before. Is one enough/good for Linux?

---

### Post by oldfred on 2011-07-04
Do not use windows to create any new partitions. I may convert to dynamic which is a problem. But using windows partition tools to shrink the windows partition is preferred.

I prefer smaller system partitions and separate data partitions. Even some Windows users suggest separating system from data and create a D: drive for all your data, so when you have to reinstall windows you do not have to reinstall all your data.

Make the recovery DVDs, but you may never use them. They are not windows install disks, but an image of your drive as purchased.  Make the repair CD as you may need that. If you have housecleaned a lot of the default cruft that Windows machines come with, added programs and changed things in general it may be best just to do a full system backup. 

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

If you create a extended partition, it can be a  container for many logical partitions. Windows will read data from a NTFS partition that is logical and Ubuntu will boot just fine from a logical partition.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by xrhettx on 2011-07-04
You don't have to create a partition, create free, empty space. Allocate the amount you want for the whole linux OS. Are you using it for data storage, games, music, videos, etc? The more media the more GB. It sounds like you'll be shrinking a windows partition; the remainder should be empty space.

---

### Post by Nick42 on 2011-07-04
Thanks guys!

Lots of info and I've been reading them.

So it seems, I need to shrink the 915.79 GB and leave space for an extended partition for Linux. Then I can create either two logical (/ and swap) or three logical (/, /home and swap) partitions. / could be ext4 (or ext3).

What is this NTFS shared partition for?

I have 8 GB RAM. Do I really need to have 8 GB swap space then?

After creating the recovery disks, I'll most likely could just remove the HP_RECOVERY partition as well. I don't have this HP_TOOLS partition others mentioned.

I also do not need the backups because it's a freshly bought new computer. I still have my old computer as well and I already copied the important stuff from the old computer to an external drive from which I copied to the new computer.

Now it's much clearer to me to how to proceed with the partitioning case. Actually usually I learn and forget how to handle this partitioning thingie every couple of years until I want to install Linux :)

In any case, I also found this, Windows Installer (old name was Wubi):
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Pretty interesting stuff, it does not require partitioning and it seems to be better than just virtualization. Though some people found out that it's slow in certain cases:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=2](http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=2)

---

### Post by oldfred on 2011-07-05
Wubi is intended for windows users who want an extended test of Ubuntu over what you can do with a liveCD. You do not have to reparition and can easily delete if you do not like Ubuntu. But if you do like Ubuntu changing to full partitions is expected even by the designer of wubi. It is not true dual boot as wubi is just a file inside the NTFS partition. As such you cannot easily boot it separately and any problem in windows NTFS partition will also prevent wubi from working.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

I was learning Ubuntu and all of our Firefox profile & Thunderbird profile data was in XP. Every time my wife wanted to check email or go on-line I had to reboot to XP. The shared with the profiles then let me have both with exactly the same info available in either sysem. Also for any other data you may want to see from both systems. Best not to write into your windows system partition (ok to read, so set read-only if you do mount it).

---

### Post by mastablasta on 2011-07-05
> **Nick42 said:**
>  
So it seems, I need to shrink the 915.79 GB and leave space for an extended partition for Linux. Then I can create either two logical (/ and swap) or three logical (/, /home and swap) partitions. / could be ext4 (or ext3).

 
yes and make sure you defragment 2 times first before shrinking (second time defrag will be fast). 
 
you don't have to crete anything. Ubuntu installer can/will create them for you. to test and use you will need 25-30 GB. 
 
> 
What is this NTFS shared partition for?

You don't need it. but it's ment to keep your data separate from both systems. for example you put windows on C, data on D and then linux on it's own parittions. if systems gets ruined you still have data intact.
 
> 
I have 8 GB RAM. Do I really need to have 8 GB swap space then?

 
probably at least that amount. again this can be done for you. just make sure you take it into account when creating linux space. swap space is kind of like pagefile in windows if you ever noticed that file. swap will also store RAM when computer goes into hibernate (which BTW is the awesome new function of Mac OS - really so new and cool one has to buy this OS to get this function).
 
> 
After creating the recovery disks, I'll most likely could just remove the HP_RECOVERY partition as well. I don't have this HP_TOOLS partition others mentioned.
 
I also do not need the backups because it's a freshly bought new computer. I still have my old computer as well and I already copied the important stuff from the old computer to an external drive from which I copied to the new computer.

 
well you should backup th eimportant things. such as OS, system drivers, personal data (usually in recovery parition)
 
> 
In any case, I also found this, Windows Installer (old name was Wubi):
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
 
Pretty interesting stuff, it does not require partitioning and it seems to be better than just virtualization. Though some people found out that it's slow in certain cases:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=2](http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=2)
 
well just like you found out. Wubi stores everything in a large virtual file within windows. if that file gets corrupt you loose everything you did in linux. it's a great way to try out the new system though and can later be easilly removed just like any other programme.

---

### Post by Nick42 on 2011-07-05
Hey guys!

Now I'm writing this my freshly installed Ubuntu 11.04 Natty Narwhal. It went very smooth. I first shrank the partition in Windows and then I created the recovery discs. Actually, as a matter of fact creating the discs took most of the time :)

Then I installed Ubuntu from the CD. When I selected an option like "Install alongside Windows 7", it didn't even bother to ask me about partitioning. Well, I would have preferred to see what it would have been but when I checked what it created, it's not that bad. So it created a swap partition of 8.6 GB (a little bit over my 8 GB RAM) so that I can hibernate (I should try that next). Then it created the rest of the partition for / using ext4. Ok, I was planning to create a /home partition as well but I can live with this :)

BTW, I was surprised by how new Ubuntu looks. I didn't like it too much and now switched to Ubuntu classic :) Maybe, I should give it a try some other time.

In any case, Windows also boots fine so mission accomplished. Thanks again!

---

