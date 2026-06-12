---
title: "[please help me!!] lost partition info after (re-)installing Window 7"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by jeffshaw on 2010-11-12
Dear Forum,

Sorry for the title but I really need some help here.

Just now I reinstalled windows 7 on my notebook with a fairly tricky partition layout.
I lost my /home/ and disk D partition.

Before I give details of what I did, I would appreciate any help with any suggestions, since the data I lost is really important (with my several month's work and years' data from old computers).

Thank anybody who points to any directions since it's really important for me and I really do not want to lose the data.

Below are the details.
-------------------------

I've had enough with the slow Windows 7 and decided to install a brand new one.
Here's what I had for partition.
[ATTACH]175475[/ATTACH]
You and see that under extended partition /dev/sda4, I have 4GB swap (sda5), 50GB /home (sda6), an in-between gap of 1MB, and about 70GiB data for disk D under windows (sda7).
Besides, sda1 is for Windows (Win7 which to be replaced with the new installation), sda2 is a working Ubuntu 10.04.1 LTS, and sda3 is a working Fedora 14 (sda3 is mainly for testing new distros of linux)

After the installation of Win7 Professional 32-bit, the system reboots and there's no disk D under windows.
So I rebooted with a Ubuntu 10.10 USB live system, and found (to my astonishment) the following partition table.
[ATTACH]175476[/ATTACH]

The previous sda6, gap, and sda7 are merged into an unallocated partition with ALL the data buried in it.

My guess is the installation of Windows 7 erased MBR or something but I have no idea how to fix that / rebuild the MBR.

Please mentiion any suggestions you might have.
I'll try each of them in the desperate hope to get my data back.
In the meanwhile, I'm searching for possible solutions in the forum as well.
Thank you a million in advance.

A very anxious student.

---

### Post by hansdown on 2010-11-13
Welcome to the forum, jeffshaw.

Just curious, how you did your re-install.

dev/sda 1, 2, 3, and 4 seem to be intact, though a fresh install of windows wants to take the whole hard drive.

Do you have a live install disk?

---

### Post by jeffshaw on 2010-11-13
Dear Hansdown,

Thank you for the reply.
I had an old Windows 7 installation on sda1.
It was very slow so I decided to re-install it, using a installation CD.
I choose "Manual" when installing, and choose the 1st partition to be the destination, so that the new Windows 7 would not cover the whole hard disk. (that's when the nightmare begins)

From my search on website, TestDisk seems to be useful tool.
I'm following the instructions at [here]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") and already got some of my data back from a given partition.
I'm still trying to figure out how to rebuild a partition table so that everything can come back untouched.

Jeff

---

### Post by jeffshaw on 2010-11-13
Ok I've figured it out and get all my data back.
It's been an exhausting day.

There are 3 steps.
1. Use TestDisk to recover the partition table / MBR (?).
After that I have my partitions info correct.

In my case, with TestDisk trying to rebuild partition table, I chose to restore sda1 (boot primary), sda2 (primary), sda3 (primary), sda4 (logical), sda5 (logical). I discarded sda6 (delete).
Note that sda 4,5,6 are renumber'ed, and the previous extended partition does not appear in TestDisk's rebuild table.

Keep sda6 as logical would make TestDisk report the scheme to be 'bad'. Not sure whether that's the reason for following problem.

2. Then I got a "Can't have a partition outside the disk!" in GParted and cannot access the partitions in linux. Windows 7 works and can get the old disk D back.

Following instructions from [here]("http://ubuntuforums.org/showthread.php?t=1038943"), I was able to adjust the end of extended partition (which was built automatically by TestDisk after my choosing partitions to be restored).

3. Follow the instruction [here]("https://help.ubuntu.com/community/WindowsDualBoot") to get GRUB multi-boot working.

Below is the partitions restored.
Note the previous swap does not exist and there are more gaps.
[ATTACH]175561[/ATTACH]

Lessons learned:
1. ALWAYS BACKUP THE DATA before changes to partitions.
2. It could be tricky to reinstall OS on sda1 (with all the MBR stuff)
3. [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") can be used to rebuild MBR / partitions (available in [SystemRescueCd]("http://www.sysresccd.org/Main_Page"), which seems to be a good distro for system rescue.)

---

### Post by jeffshaw on 2010-11-13
Ok I've figured it out and get all my data back.
It's been an exhausting day.

There are 3 steps.
1. Use TestDisk to recover the partition table / MBR (?).
After that I have my partitions info correct.

In my case, with TestDisk trying to rebuild partition table, I chose to restore sda1 (boot primary), sda2 (primary), sda3 (primary), sda4 (logical), sda5 (logical). I discarded sda6 (delete).
Note that sda 4,5,6 are renumber'ed, and the previous extended partition does not appear in TestDisk's rebuild table.

Keep sda6 as logical would make TestDisk report the scheme to be 'bad'. Not sure whether that's the reason for following problem.

2. Then I got a "Can't have a partition outside the disk!" in GParted and cannot access the partitions in linux. Windows 7 works and can get the old disk D back.

Following instructions from [here]("http://ubuntuforums.org/showthread.php?t=1038943"), I was able to adjust the end of extended partition (which was built automatically by TestDisk after my choosing partitions to be restored).

3. Follow the instruction [here]("https://help.ubuntu.com/community/WindowsDualBoot") to get GRUB multi-boot working.

Below is the partitions restored.
Note the previous swap does not exist and there are more gaps.
[ATTACH]175561[/ATTACH]

Lessons learned:
1. ALWAYS BACKUP THE DATA before changes to partitions.
2. It could be tricky to reinstall OS on sda1 (with all the MBR stuff)
3. [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") can be used to rebuild MBR / partitions (available in [SystemRescueCd]("http://www.sysresccd.org/Main_Page"), which seems to be a good distro for system rescue.)

---

### Post by hansdown on 2010-11-14
Glad you fixed it,jeffshaw.

---

