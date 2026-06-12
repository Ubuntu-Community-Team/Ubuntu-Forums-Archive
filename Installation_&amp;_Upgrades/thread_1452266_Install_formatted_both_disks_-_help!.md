---
title: "Install formatted both disks - help!"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by bobbryce on 2010-04-11
Can anyone give me a YES/NO - is my data trashed?

I'm reasonably computer friendly and wanted to set up a Linux machine to use in the house as a file server so that the family could all use it to back up theur data. After some study I decided to choose UBUNTU 8.04 LTS.

My computer was running Windows XP and was fitted with two IDE drives (C: and D:).

I decided to put all my important data on the second drive and give up the first one to a new install of Ubuntu - however and despite my best efforts to check what was going on - it looks like the partition and format decided to use both disks. THIS IS NOT USER-FRIENDLY.

After some learning, I discovered the command 'fdisk -l' - here's what I found....
--------------------------------------------------------------------
sudo fdisk -l

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc453c453

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       15017   100141177+   5  Extended
/dev/sda5            2551       14829    98631036   83  Linux
/dev/sda6           14830       15017     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12f712f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14767   118615896   83  Linux
/dev/sdb2           14768       14953     1494045    5  Extended
/dev/sdb5           14768       14953     1494013+  82  Linux swap / Solaris
---------------------------------------------------------------------

I guess it's /dev/sdb that is my second disk.
I haven't knowingly been using it - is it possible to unformat it such that a windows installation can recover the data???

Any help very gratefully received.
Thanks
Bob

---

### Post by phillw on 2010-04-11
while i do some checking, it looks to the information indicates your Win area is quite safe.

Let me just have a dig through the listing

Relax !! :-)

Phill.

---

### Post by phillw on 2010-04-11
Right,

you have about 20GB of windows left on sda (your C:) drive.

can you post the contents of

```
 sudo df -Th
```

sdb (your D:) drive has certainly been reformatted into 100% Linux. As to how you have managed to add a linux installation onto both your sda drive and sdb drive, I do not know. The results of df -Th for both drives will give me some idea of where to suggest you go next.

Regards,

Phill.

---

### Post by bobbryce on 2010-04-11
PhillW,
Many thanks for trying to help.

After my 'accident', I did re-install Windows XP onto my first drive and this is now running as a dual-boot with Ubuntu.  I did this to try and read from my second drive from Windows but it doesn't show in Explorer (I guess because it's no longer formatted as NFTS). So - yes, I know I have a 20GB partition on my first drive that's dedicated to Windows XP.

My problem is that the second drive looks like its formatted as ext3. Are there any tools that will 'undo' the format. If not, should I format as NFTS using Windows discs and then try and recover data using Windows tools?

Here's what you asked me to do....

---------------------------------------------------------
sudo df -Th
[sudo] password for bob:
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3     94G  1.7G   87G   2% /
varrun       tmpfs    252M  184K  252M   1% /var/run
varlock      tmpfs    252M     0  252M   0% /var/lock
udev         tmpfs    252M   68K  252M   1% /dev
devshm       tmpfs    252M     0  252M   0% /dev/shm
----------------------------------------------------------

PS - I don't know how to execute this command on the second drive. If I could tell if there were no directories mounted on the second drive that would be a start. If there are any then chances of recovering windows filess would be pretty slim - right?

Ta,
Bob

---

### Post by bobbryce on 2010-04-12
UPDATE
Great news - I'm fixed.

Recap - my 2nd hard drive was formatted during installation of Ubuntu server 8.04 LTS - I did not request this, and it was unclear that the installer was planning to do this. Sadly for me - my second disk was where all my back-ups were.

I found some great open source software called 'TESTDISK' and was able to use this to reclassify my 2nd disc as an NTFS disc rather than two Linux partitions of 'ext3' and 'swap'. It seems to have managed this by finding the backup boot record and copying this data back to the main boot record. I don't know if I have any data corruption, but looks like I have my files back and accessible under Windows.

Meanwhile, I'm enjoying all the new Linux functionality by using my old computer for lots of new things.

A GREAT BIG vote of thanks to TEST DISK from CGSecurity.
I loaded up TESTDISK from the server terminal using 'sudo apt-get install testdisk', and then ran through a guided option from the TESTDISK website - see below. 
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Recover_deleted_files](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Recover_deleted_files)

All that's left is for somebody to figure why the installer did what it did and make it less likely that a novice isn't allowed to do the same again.

Thanks all

---

