---
title: "*Urgent!* Trying to reinstall Ubuntu 11.04, but there's a potential problem."
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by SteveL1990 on 2013-03-30
Hi folks. To make a painfully long story real short, my old Ubuntu system screwed up and my attempts to fix it, despite my best attempts to follow instructions on sites that offered solutions, failed miserably. Now I have to reinstall my Natty.....


EDIT:it looks like I managed to successfully create a good partition, and my other data seems to be intact, but I got this error message: 
GParted 0.7.0 --enable-libparted-dmraid
 Libparted 2.3
 [TABLE]
[TR]
[TD="colspan: 2"] **Move /dev/sdb5 to the right and shrink it from 33.57 GiB to 29.61 GiB**  00:08:06    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] calibrate /dev/sdb5  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sdb5
start: 402870272
end: 473264127
size: 70393856 (33.57 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] check file system on /dev/sdb5 for errors and (if possible) fix them  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***ntfsresize -P -i -f -v /dev/sdb5***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 36041650688 bytes (36042 MB)
Current device size: 36041654272 bytes (36042 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 69 MB (0.2%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :         1 MB             0
$MFTMirr           :     18021 MB             1
Ordinary           :     18088 MB             2
You might resize at 68673536 bytes or 69 MB (freeing 35973 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] shrink file system  00:00:02    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] run simulation  00:00:02    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***ntfsresize -P --force /dev/sdb5 -s 31788630015 --no-action***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 36041650688 bytes (36042 MB)
Current device size: 36041654272 bytes (36042 MB)
New volume size    : 31788622336 bytes (31789 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 69 MB (0.2%)
Collecting resizing constraints ...
Needed relocations : 0 (0 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] real resize  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***ntfsresize -P --force /dev/sdb5 -s 31788630015***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 36041650688 bytes (36042 MB)
Current device size: 36041654272 bytes (36042 MB)
New volume size    : 31788622336 bytes (31789 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 69 MB (0.2%)
Collecting resizing constraints ...
Needed relocations : 0 (0 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/sdb5'.
You can go on to shrink the device for example with Linux fdisk.
IMPORTANT: When recreating the partition, make sure that you
  1)  create it at the same disk sector (use sector as the unit!)
  2)  create it with the same partition type (usually 7, HPFS/NTFS)
  3)  do not make it smaller than the new NTFS filesystem size
  4)  set the bootable flag for the partition if it existed before
Otherwise you won't be able to access NTFS or can't boot from the disk!
If you make a mistake and don't have a partition table backup then you
can recover the partition table by TestDisk or Parted's rescue mode.
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] shrink partition from 33.57 GiB to 29.61 GiB  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]old start: 402870272
old end: 473264127
old size: 70393856 (33.57 GiB)[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]new start: 402870272
new end: 464957439
new size: 62087168 (29.61 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] check file system on /dev/sdb5 for errors and (if possible) fix them  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***ntfsresize -P -i -f -v /dev/sdb5***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 31788622336 bytes (31789 MB)
Current device size: 31788630016 bytes (31789 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 69 MB (0.2%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :         1 MB             0
$MFTMirr           :     18021 MB             1
Ordinary           :     18088 MB             2
You might resize at 68542464 bytes or 69 MB (freeing 31720 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] grow file system to fill the partition  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] run simulation  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***ntfsresize -P --force /dev/sdb5 --no-action***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 31788622336 bytes (31789 MB)
Current device size: 31788630016 bytes (31789 MB)
New volume size    : 31788626432 bytes (31789 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 69 MB (0.2%)
Collecting resizing constraints ...
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] real resize  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***ntfsresize -P --force /dev/sdb5***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 31788622336 bytes (31789 MB)
Current device size: 31788630016 bytes (31789 MB)
New volume size    : 31788626432 bytes (31789 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 69 MB (0.2%)
Collecting resizing constraints ...
WARNING: Every sanity check passed and only the dangerous operations left.
Make sure that important data has been backed up! Power outage or computer
crash may result major data loss!
Are you sure you want to proceed (y/[n])? Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/sdb5'.
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] check file system on /dev/sdb5 for errors and (if possible) fix them  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***ntfsresize -P -i -f -v /dev/sdb5***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 31788626432 bytes (31789 MB)
Current device size: 31788630016 bytes (31789 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 69 MB (0.2%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :         1 MB             0
$MFTMirr           :     18021 MB             1
Ordinary           :     18088 MB             2
You might resize at 68542464 bytes or 69 MB (freeing 31720 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] grow partition from 29.61 GiB to 29.66 GiB  00:00:02    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]old start: 402870272
old end: 464957439
old size: 62087168 (29.61 GiB)[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]new start: 402870272
new end: 465072127
new size: 62201856 (29.66 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] move file system to the right  00:07:58    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] perform read-only test  00:07:58    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] using internal algorithm[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] read 29.61 GiB[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] finding optimal block size[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] read 16.00 MiB using a block size of 2.00 MiB  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *16.00 MiB of 16.00 MiB read*[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] *0.629986 seconds*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] read 16.00 MiB using a block size of 4.00 MiB  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *16.00 MiB of 16.00 MiB read*[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] *0.587879 seconds*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] read 16.00 MiB using a block size of 8.00 MiB  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *16.00 MiB of 16.00 MiB read*[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] *0.548198 seconds*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] read 16.00 MiB using a block size of 16.00 MiB  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *16.00 MiB of 16.00 MiB read*[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] *0.555102 seconds*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] optimal block size is 8.00 MiB[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] read 29.54 GiB using a block size of 8.00 MiB  00:07:56    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *15.30 GiB of 29.54 GiB read*[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] *Error while reading block at sector 432721920*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] 15.36 GiB (16496197632 B) read[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] rollback last change to the partition table  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] shrink partition from 29.66 GiB to 29.61 GiB  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]old start: 402870272
old end: 465072127
old size: 62201856 (29.66 GiB)[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]new start: 402870272
new end: 464957439
new size: 62087168 (29.61 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] libparted messages    ( INFO )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *Input/output error during read on /dev/sdb*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 ========================================

Anybody know what it means? Hope it isn't a major problem.

---

### Post by cortman on 2013-03-30
Let's take it one thing at a time.

a) You have data on the current Ubuntu installation that you want to save.
b) You've deleted the partition that contained the data?

If you have really deleted the partition, your data is gone. If you didn't, or if you're not sure, by all means check it from a LiveCd- just select "Try Ubuntu" and you'll get a complete Ubuntu desktop, from which you can browse your computer's hard drive with the file manager. Copy all your files over to an external HDD or a USB flash drive, and then you'll be safe. :)
As far as reinstalling, I'd recommend you go with Xubuntu or Lubuntu 12.04, if your computer is a bit older or if you prefer a classic desktop, or if you must run vanilla Ubuntu you should install 12.04 as well. Xubuntu and Ubuntu 12.04 are LTS releases, which means they'll get security updates and support for five years. Lubuntu unfortunately doesn't make the LTS status yet, so it's only supported for 18 months.

---

### Post by SteveL1990 on 2013-03-30
Thanks for the reply, It looks like my Windows partition is now okay, though I never could figure out how to copy my partitions to my external HDD. If you can show me some links for future references, I'd appreciate that. =)

---

