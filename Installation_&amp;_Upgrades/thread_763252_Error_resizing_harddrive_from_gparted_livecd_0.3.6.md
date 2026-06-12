---
title: "Error resizing harddrive from gparted livecd 0.3.6"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by ihavenoidea on 2008-04-22
im resizing my 80 gig hard drive for ubuntu. Going to start by resizing the spare 15 gig i have for ubuntu, then move my files, then wipe the other partition then resize the whole thing for ubuntu. Anyway this is the error i got trying, running gparted live cd, i cant log on to their forums. 


```
GParted 0.3.6

Libparted 1.7.1

Move /dev/hda1 to the left and shrink it from 74.53 GiB to 58.13 GiB  01:22    ( ERROR )
     	
calibrate /dev/hda1  00:00    ( SUCCESS )
     	
path: /dev/hda1
start: 63
end: 156296384
size: 156296322 (74.53 GiB)
calculate new size and position of /dev/hda1  00:00    ( SUCCESS )
     	
requested start: 0
requested end: 121917284
requested size: 121917285 (58.13 GiB)
new start: 63
new end: 121917284
new size: 121917222 (58.13 GiB)
check filesystem on /dev/hda1 for errors and (if possible) fix them  00:09    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/hda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 80023716352 bytes (80024 MB)
Current device size: 80023716864 bytes (80024 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 61706 MB (77.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 79675 MB 0
Multi-Record : 80024 MB 56263
$MFTMirr : 3147 MB 1
Compressed : 79951 MB 100043
Ordinary : 80024 MB 135531
You might resize at 61705375744 bytes or 61706 MB (freeing 18318 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem  01:04    ( ERROR )
     	
run simulation  01:04    ( ERROR )
     	
ntfsresize -P --force --force /dev/hda1 -s 62421617663 --no-action
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 80023716352 bytes (80024 MB)
Current device size: 80023716864 bytes (80024 MB)
New volume size : 62421611008 bytes (62422 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 61706 MB (77.1%)
Collecting resizing constraints ...
Needed relocations : 2565936 (10511 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1224 > 1024), not yet supported!
Please try to free less space.
check filesystem on /dev/hda1 for errors and (if possible) fix them  00:09    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/hda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 80023716352 bytes (80024 MB)
Current device size: 80023716864 bytes (80024 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 61706 MB (77.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 79675 MB 0
Multi-Record : 80024 MB 56263
$MFTMirr : 3147 MB 1
Compressed : 79951 MB 100043
Ordinary : 80024 MB 135531
You might resize at 61705375744 bytes or 61706 MB (freeing 18318 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:00    ( SUCCESS )
     	
run simulation  00:00    ( SUCCESS )
     	
ntfsresize -P --force --force /dev/hda1 --no-action
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 80023716352 bytes (80024 MB)
Current device size: 80023716864 bytes (80024 MB)
New volume size : 80023712256 bytes (80024 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00    ( SUCCESS )
     	
ntfsresize -P --force --force /dev/hda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 80023716352 bytes (80024 MB)
Current device size: 80023716864 bytes (80024 MB)
New volume size : 80023712256 bytes (80024 MB)
Nothing to do: NTFS volume size is already OK.
```

---

### Post by Herman on 2008-04-22
I found that when trying out the installer in a test computer it sometimes would refuse to resize and NTFS partition at first.

My solution is to put in a Windows Installation CD and run 'CHKDSK /R' on the file system concerned and then try again with GParted, (in the Ubuntu installer). So far it has worked every time for me, once the NTFS file system has been checked and fixed, GParted will resize it without any trouble at all.

There are Linux file system checkers these days that may be as good or even better than Windows CHKDSK, you would need to install ntfsprogs and run ntfsfix if you have no Windows Installation disc.  I'm not sure whether ntfsfix is as good as CHKDSK yet or not, I would like to see an expert's debate.  I think Linux support for NTFS is very good nowadays though.

Regards, Herman :)

---

