---
title: "Resizing Error"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Kaphix on 2007-03-15
While trying to resize /dev/sda1 ntfs hard drive I get this error

```
GParted 0.2.5

Resize /dev/sda1 from 74.50 GiB to 9.77 GiB    ( ERROR )
     	
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 79990813184 bytes (79991 MB)
Current device size: 79990815744 bytes (79991 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 1848 MB (2.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3232 MB 0
Multi-Record : 1029 MB 7450
$MFTMirr : 39996 MB 1
Compressed : 1259 MB 8782
Ordinary : 39999 MB 10
You might resize at 3231305728 bytes or 3232 MB (freeing 76759 MB).
Please make a test run using both the -n and -s options before real resizing!
resize the filesystem    ( ERROR )
     	
run simulation    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1 -s 10477535232 --no-action
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 79990813184 bytes (79991 MB)
Current device size: 79990815744 bytes (79991 MB)
New volume size : 10477531648 bytes (10478 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 1848 MB (2.3%)
Collecting resizing constraints ...
Needed relocations : 45 (1 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
resize the filesystem    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1 -s 10477535232
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
ERROR(95): Opening '/dev/sda1' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 79990813184 bytes (79991 MB)
Current device size: 79990815744 bytes (79991 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 1848 MB (2.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3232 MB 0
Multi-Record : 1029 MB 7450
$MFTMirr : 39996 MB 1
Compressed : 1259 MB 8782
Ordinary : 39999 MB 10
You might resize at 3231305728 bytes or 3232 MB (freeing 76759 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition    ( ERROR )
     	
run simulation    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1 --no-action
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 79990813184 bytes (79991 MB)
Current device size: 79990815744 bytes (79991 MB)
New volume size : 79990809088 bytes (79991 MB)
Nothing to do: NTFS volume size is already OK.
grow filesystem to fill the partition    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
ERROR(95): Opening '/dev/sda1' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 79990813184 bytes (79991 MB)
Current device size: 79990815744 bytes (79991 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 1848 MB (2.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3232 MB 0
Multi-Record : 1029 MB 7450
$MFTMirr : 39996 MB 1
Compressed : 1259 MB 8782
Ordinary : 39999 MB 10
You might resize at 3231305728 bytes or 3232 MB (freeing 76759 MB).
Please make a test run using both the -n and -s options before real resizing!

========================================


```

---

### Post by Kateikyoushi on 2007-03-15
Did you run checkdisk and tried it again ?

---

### Post by Kaphix on 2007-03-15
No, whats that?

---

### Post by Kaphix on 2007-03-15
Ok I fixed it, but now it says:

"No root file system is defined. Please correct this from the partitioning menu."

---

### Post by Kateikyoushi on 2007-03-15
You can run it by right clicking on a drive in explorer, select properties then on the tools tab can start dick scan, or read this to run from terminal. [LINK]("http://support.microsoft.com/kb/315265")

---

### Post by nickd916 on 2007-03-15
I've been having the same problem...Did you follow those instructions ^ to fix the problem or did you do something else.

---

### Post by Kateikyoushi on 2007-03-15
You have to make a filesystem on the partition, I recommend ext3.
I would recommend to read this installation guide. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by nickd916 on 2007-03-15
how. you have to have space . i just have one huge partition that wont let me resize it. does it matter that its a dell laptop

---

### Post by Kateikyoushi on 2007-03-15
It won't let your resize the partitioneven after checkdisk ? Do you still ge the same error message ?

---

### Post by nickd916 on 2007-03-15
Now it says this after i have chkdsk


GParted 0.2.5
Resize /dev/hda1 from 74.53 GiB to 34.43 GiB    ( ERROR ) 
    	check filesystem on /dev/hda1 for errors and (if possible) fix them    ( ERROR ) 
    	ntfsresize -P -i -f -v /dev/hda1 
    	ntfsresize v1.12.1 (libntfs 8:1:0)Using locale 'en_US.UTF-8'.Device name : /dev/hda1NTFS volume version: 3.1Cluster size : 4096 bytesCurrent volume size: 80023716352 bytes (80024 MB)Current device size: 80023716864 bytes (80024 MB)Checking filesystem consistency ...Accounting clusters ...Space in use : 33395 MB (41.7%)Collecting resizing constraints ...WARNING: The disk has bad sector! This can cause reliability problems!Bad clusters: 3006611 - 3006611ERROR: The NTFS volume has at least 1 bad sector.***************************************************************************** WARNING: The disk has bad sector. This means physical damage on the disk ** surface caused by deterioration, manufacturing faults or other reason. ** The reliability of the disk may stay stable or degrade fast. We suggest ** making a full backup urgently by running 'ntfsclone --rescue ...' then ** run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize ** NTFS safely by additionally using the --bad-sectors option of ntfsresize.*****************************************************************************




========================================

---

### Post by Kateikyoushi on 2007-03-15
This looks bad, seem you have a bad sector. Getting a new hard drive is recommended, but you could try to proceed by following what the error message recommends.

> WARNING: The disk has bad sector. This means physical damage on the disk ** surface caused by deterioration, manufacturing faults or other reason. ** The reliability of the disk may stay stable or degrade fast. We suggest ** making a full backup urgently by running 'ntfsclone --rescue ...' then ** run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize ** NTFS safely by additionally using the --bad-sectors option of ntfsresize.

---

### Post by nickd916 on 2007-03-16
"by additionally using the --bad-sectors option of ntfsresize."

is that somewhere in Gparted?

---

### Post by Kateikyoushi on 2007-03-16
No it is a separate command ntfsresize, type it in terminal,the man "ntfsresize" and "ntfsresize --help" should give you some ideas how to use it.

But be careful and make a backup of important data, what you already should have done on that harddisk.

---

