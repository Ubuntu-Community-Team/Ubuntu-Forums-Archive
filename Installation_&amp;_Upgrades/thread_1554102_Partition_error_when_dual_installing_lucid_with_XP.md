---
title: "Partition error when dual installing lucid with XP"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by Tripwire32 on 2010-08-16
I got this error when trying to partition with gparted before installing ubuntu onto the created partition. I running a fairly old pc (2005) with 40 GB hard drive and XP installed. Please can you help? I've also tried installing dual-boot from ubuntu installer prior to this. 

GParted 0.5.1
 Libparted 2.2
    **Shrink /dev/sda1 from 37.27 GiB to 26.91 GiB**  00:06:43    ( ERROR )             calibrate /dev/sda1  00:00:00    ( SUCCESS )             [I]path: /dev/sda1
start: 63
end: 78156224
size: 78156162 (37.27 GiB)[/I]          check file system on /dev/sda1 for errors and (if possible) fix them  00:02:10    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sda1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 40015954432 bytes (40016 MB)
Current device size: 40015954944 bytes (40016 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 26875 MB (67.2%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :     35461 MB             0
Multi-Record       :     40015 MB          1467
$MFTMirr           :     20013 MB             1
Compressed         :     40016 MB         85369
Sparse             :     39925 MB          9977
Ordinary           :     40016 MB         82848
You might resize at 26874449920 bytes or 26875 MB (freeing 13141 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             shrink file system  00:02:32    ( ERROR )             run simulation  00:02:32    ( ERROR )             ***ntfsresize -P --force /dev/sda1 -s 28895376383 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 40015954432 bytes (40016 MB)
Current device size: 40015954944 bytes (40016 MB)
New volume size    : 28895371776 bytes (28896 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 26875 MB (67.2%)
Collecting resizing constraints ...
Needed relocations : 1647210 (6747 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1072 > 1024), not yet supported!
Please try to free less space.
[/I]                check file system on /dev/sda1 for errors and (if possible) fix them  00:01:56    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sda1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 40015954432 bytes (40016 MB)
Current device size: 40015954944 bytes (40016 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 26875 MB (67.2%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :     35461 MB             0
Multi-Record       :     40015 MB          1467
$MFTMirr           :     20013 MB             1
Compressed         :     40016 MB         85369
Sparse             :     39925 MB          9977
Ordinary           :     40016 MB         82848
You might resize at 26874449920 bytes or 26875 MB (freeing 13141 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             grow file system to fill the partition  00:00:05    ( SUCCESS )             run simulation  00:00:04    ( SUCCESS )             ***ntfsresize -P --force /dev/sda1 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 40015954432 bytes (40016 MB)
Current device size: 40015954944 bytes (40016 MB)
New volume size    : 40015950336 bytes (40016 MB)
Nothing to do: NTFS volume size is already OK.
[/I]             real resize  00:00:01    ( SUCCESS )             ***ntfsresize -P --force /dev/sda1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 40015954432 bytes (40016 MB)
Current device size: 40015954944 bytes (40016 MB)
New volume size    : 40015950336 bytes (40016 MB)
Nothing to do: NTFS volume size is already OK.
[/I]                ========================================
    **Create Primary Partition #1 (ext4, 10.36 GiB) on /dev/sda**    ========================================

---

### Post by Tripwire32 on 2010-08-16
PS. I've read a few of the guides and have done suggested prep before  attempting the partitioning, i.e. delete unwanted files, defrag, disk  check, restart, install ubuntu/gparted from live cd

---

### Post by efflandt on 2010-08-16
Did you make a note of current WinXP virtual memory, then disable virtual memory and reboot XP (for it to take effect) before trying to resize?  I think that is in System > Advanced in Windows.  Virtual memory cannot be relocated, so that can limit shrinking the partition.

Note that if you successfully shrink Windows (or maybe slightly shrunk it due to something not movable) gparted marks the partition as dirty, so Windows will run chkdsk on it when booting.  And gparted is not going to even try to shrink it if it thinks it is dirty.  So you may want to boot Windows, let it go through its disk check, and then remove virtual memory before trying anything else.

---

### Post by Tripwire32 on 2010-08-17
Thanks for the response. While trying to implement the solution, I noticed many fragmented files in unusual places while defragging. These turned out to be viruses and as a result my pc now just cycles through logging off and on. Let me try to 1st fix windows (and recover NB files) before I try the virtual mem fix, then install ubuntu. 

If I don't succeed, I might try installing ubuntu on top of the now faulty XP installation. Is there anything specific I need to do to do this or can I just choose that option when installing from live cd? Unfortunately, I won't be able to make any backups due to XP mucking around. Right now, I'm quite ready to happily turn my back on windows forever!!!:mad:

---

