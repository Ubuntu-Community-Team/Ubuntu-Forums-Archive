---
title: "Something wrong with partitioning my disk!"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by mrcoffee09 on 2007-02-12
GParted 0.2.5

Resize /dev/sda1 from 144.88 GiB to 138.80 GiB    ( ERROR )
     	
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 155564720640 bytes (155565 MB)
Current device size: 155564720640 bytes (155565 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 129699 MB (83.4%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 154919 MB 0
Multi-Record : 155565 MB 13187
$MFTMirr : 77783 MB 1
Compressed : 155499 MB 303262
Sparse : 155560 MB 155640
Ordinary : 155565 MB 157902
You might resize at 129698316288 bytes or 129699 MB (freeing 25866 MB).
Please make a test run using both the -n and -s options before real resizing!
resize the filesystem    ( ERROR )
     	
run simulation    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1 -s 149022736384 --no-action
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 155564720640 bytes (155565 MB)
Current device size: 155564720640 bytes (155565 MB)
New volume size : 149022732800 bytes (149023 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 129699 MB (83.4%)
Collecting resizing constraints ...
Needed relocations : 1102052 (4515 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1032 > 1024), not yet supported!
Please try to free less space.
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 155564720640 bytes (155565 MB)
Current device size: 155564720640 bytes (155565 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 129699 MB (83.4%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 154919 MB 0
Multi-Record : 155565 MB 13187
$MFTMirr : 77783 MB 1
Compressed : 155499 MB 303262
Sparse : 155560 MB 155640
Ordinary : 155565 MB 157902
You might resize at 129698316288 bytes or 129699 MB (freeing 25866 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition    ( SUCCES )
     	
run simulation    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1 --no-action
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 155564720640 bytes (155565 MB)
Current device size: 155564720640 bytes (155565 MB)
New volume size : 155564716544 bytes (155565 MB)
Nothing to do: NTFS volume size is already OK.
grow filesystem to fill the partition    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 155564720640 bytes (155565 MB)
Current device size: 155564720640 bytes (155565 MB)
New volume size : 155564716544 bytes (155565 MB)
Nothing to do: NTFS volume size is already OK.
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 155564720640 bytes (155565 MB)
Current device size: 155564720640 bytes (155565 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 129699 MB (83.4%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 154919 MB 0
Multi-Record : 155565 MB 13187
$MFTMirr : 77783 MB 1
Compressed : 155499 MB 303262
Sparse : 155560 MB 155640
Ordinary : 155565 MB 157902
You might resize at 129698316288 bytes or 129699 MB (freeing 25866 MB).
Please make a test run using both the -n and -s options before real resizing!

========================================






Im not sure what any of this means, but i doubt it's good.  Any help would be appreciated.  My Hard Drive might be bad, my computer randomly shuts down :( 

Thanks
Mrcoffee

---

### Post by pixeldotz on 2007-04-04
just wanted to know if you got this situation sorted. reason i ask is because i'm having the exact same problem on my 40GB seagate. my hdd is fine and aside from replacing the power supply i've not had a serious problem on my pc.

---

