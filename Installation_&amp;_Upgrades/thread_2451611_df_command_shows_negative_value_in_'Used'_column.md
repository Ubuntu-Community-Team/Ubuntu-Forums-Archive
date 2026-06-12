---
title: "df command shows negative value in 'Used' column"
date: 2020-10-07
forum: Installation &amp; Upgrades
---

### Post by RegUB on 2020-10-07
I have just installed Ubuntu 20.04 alongside a Windows 10 installation. In Ubuntu, if I mount the Windows partition and issue a df command I get the following output -
```

$ df | grep -v snap
Filesystem     1K-blocks       Used Available Use% Mounted on
udev             7923760          0   7923760   0% /dev
tmpfs            1590388       1888   1588500   1% /run
/dev/nvme0n1p5 383896064    8742396 355583136   3% /
tmpfs            7951932          0   7951932   0% /dev/shm
tmpfs               5120          4      5116   1% /run/lock
tmpfs            7951932          0   7951932   0% /sys/fs/cgroup
/dev/nvme0n1p1    262144      36824    225320  15% /boot/efi
tmpfs            1590384         20   1590364   1% /run/user/1000
/dev/nvme0n1p3 107715684 -349352264 457067948    - /media/reg/Windows-SSD

```
The machine is a Lenovo Thinkbook. There is 512Gb storage, with 110Gb allocated to the Windows partition (of which about 60Gb is free), so the figure 107715684 looks about right. But the 'Available' figure seems to consist of the total disk size (512) minus the actual free Windows space (60), and as a result the 'Used' figure has a negative value. (Of course 'Available' should show the 110 partition size minus 60).

How has this come about and what are the potential consequences? Can it be fixed?

---

### Post by deadflowr on 2020-10-07
I'd look at what the file system types are
```
df -Th -x squashfs
```
(The T will reveal the file system type like ntfs, or ext4 or other,
h is for human readable, it'll break it to MB or GB values,
and -x excludes the listed file system types in this case squashfs, which is what snaps use)

---

### Post by RegUB on 2020-10-07
> **deadflowr said:**
> I'd look at what the file system types are


```

$ df -Th -x squashfs
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.6G     0  7.6G   0% /dev
tmpfs          tmpfs     1.6G  1.9M  1.6G   1% /run
/dev/nvme0n1p5 ext4      367G  8.5G  339G   3% /
tmpfs          tmpfs     7.6G     0  7.6G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.6G     0  7.6G   0% /sys/fs/cgroup
/dev/nvme0n1p1 vfat      256M   36M  221M  15% /boot/efi
tmpfs          tmpfs     1.6G   20K  1.6G   1% /run/user/1000
/dev/nvme0n1p3 fuseblk   103G -331G  434G    - /media/reg/Windows-SSD

```

File systems appear to be as expected?

---

### Post by TheFu on 2020-10-07
Is the ntfs partition using a "basic" partition or one of msft's advanced offerings?
Was the ntfs file system properly closed by Windows?  Win8+ defaults to not closing file systems. The fact that it got mounted is interesting.

---

### Post by RegUB on 2020-10-08
> **TheFu said:**
> Is the ntfs partition using a "basic" partition or one of msft's advanced offerings?
Was the ntfs file system properly closed by Windows?  Win8+ defaults to not closing file systems. 

It was a pre-installed Windows 10 - the partitioning was done as part of the Ubuntu installation process. fdisk command shows the Windows partition as 'Microsoft Basic Data'.
```

Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     534527    532480   260M EFI System
/dev/nvme0n1p2    534528     567295     32768    16M Microsoft reserved
/dev/nvme0n1p3    567296  215998671 215431376 102.7G Microsoft basic data
/dev/nvme0n1p4 998166528 1000214527   2048000  1000M Windows recovery environmen
/dev/nvme0n1p5 216000512  998166527 782166016   373G Linux filesystem


```
Before installation of Ubuntu I had closed Windows down (before booting from an Ubuntu ISO on a memory stick). Would this not close down the Windows file system?
> **TheFu said:**
> The fact that it got mounted is interesting.

Not sure what you mean - I mounted it from the file manager - do you mean the fact that I was able to mount it?

---

### Post by TheFu on 2020-10-08
> **RegUB said:**
>  
Before installation of Ubuntu I had closed Windows down (before booting from an Ubuntu ISO on a memory stick). Would this not close down the Windows file system?
I don't know. Windows 8 and later do not close file systems or actually do a real reboot unless the defaults are changed.  This was changed by MSFT in attempts to speed up the appearance of a faster boot, since an actual reboot takes more time to find and validate hardware.  If or whether a memory stick has different behavior, I don't know.  Do you really have a SONY Memory Stick? I hadn't seen one of those in about a decade, when I replaced my SONY PnS camera.

> **RegUB said:**
>  
Not sure what you mean - I mounted it from the file manager - do you mean the fact that I was able to mount it?
My guess is that the storage is corrupted, somehow.  Usually Linux will refuse to mount corrupted storage.  
Initially, after just seeing the thread title and nothing else, my guess was that some advanced Linux file system like BTRFS was being used.  BTRFS lies about storage used. This is because it doesn't use it in the simplistic way we humans have come to think of for storage use.  Seeing that the file system involved is NTFS killed that idea, so I jumped over to the idea that perhaps Windows has some advanced file systems.  I know they do, but I didn't think they were used by default.

My last guess is that the storage is failing and has already failed profoundly.  I'd check the SMART data for problems.  Takes 2 minutes, but it will tell us much.  SMART is about the entire disk, but flash USB drives often don't support it at all.  SSDs and HDDs the last 25+ yrs all do. It is required for any storage to be purchased by the USGovt. No SMART, no sale.

---

### Post by RegUB on 2020-10-08
> **TheFu said:**
>  I'd check the SMART data for problems.  

How do I do that?

---

### Post by TheFu on 2020-10-08
> **RegUB said:**
> How do I do that?

[https://ubuntuforums.org/showthread.php?t=2450838&p=13987957#post13987957](https://ubuntuforums.org/showthread.php?t=2450838&p=13987957#post13987957)

Beware that SMART output will include something that says the test was successful. This isn't what you need to know, unless the test fails to complete.  A completed test just means the drive responded to SMART queries. The actual results, those that could explain corruption or a pending HDD/SSD failure are in the numbers.  You can lookup each parameter online for what they mean.

There's a GUI way to do all this too, but I've found the GUI doesn't work on 95% of my servers, and it didn't include the raw data, which I need to see to understand what is actually happening.

---

### Post by RegUB on 2020-10-08
> **TheFu said:**
> [https://ubuntuforums.org/showthread.php?t=2450838&p=13987957#post13987957](https://ubuntuforums.org/showthread.php?t=2450838&p=13987957#post13987957)

Beware that SMART output will include something that says the test was successful. This isn't what you need to know, unless the test fails to complete.  A completed test just means the drive responded to SMART queries. The actual results, those that could explain corruption or a pending HDD/SSD failure are in the numbers.  You can lookup each parameter online for what they mean.

There's a GUI way to do all this too, but I've found the GUI doesn't work on 95% of my servers, and it didn't include the raw data, which I need to see to understand what is actually happening.
Anything out of the ordinary here?
```

$ sudo smartctl -t short /dev/nvme0n1
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-48-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

NVMe device successfully opened

Use 'smartctl -a' (or '-x') to print SMART (and more) information

$ sudo smartctl -a /dev/nvme0n1
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-48-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Number:                       SAMSUNG MZALQ512HALU-000L2
Serial Number:                      S4UKNF0N462942
Firmware Version:                   AL2QFXV7
PCI Vendor/Subsystem ID:            0x144d
IEEE OUI Identifier:                0x002538
Total NVM Capacity:                 512,110,190,592 [512 GB]
Unallocated NVM Capacity:           0
Controller ID:                      5
Number of Namespaces:               1
Namespace 1 Size/Capacity:          512,110,190,592 [512 GB]
Namespace 1 Utilization:            55,007,522,816 [55.0 GB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            002538 a401b83241
Local Time is:                      Thu Oct  8 15:56:19 2020 BST
Firmware Updates (0x16):            3 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat Timestmp
Maximum Data Transfer Size:         512 Pages
Warning  Comp. Temp. Threshold:     82 Celsius
Critical Comp. Temp. Threshold:     85 Celsius

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     4.83W       -        -    0  0  0  0        0       0
 1 +     3.54W       -        -    1  1  1  1        0       0
 2 +     3.04W       -        -    2  2  2  2        0     500
 3 -   0.0500W       -        -    3  3  3  3      210    1200
 4 -   0.0050W       -        -    4  4  4  4     1000    9000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         0

=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        24 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    0%
Data Units Read:                    639,436 [327 GB]
Data Units Written:                 657,556 [336 GB]
Host Read Commands:                 7,384,209
Host Write Commands:                4,713,842
Controller Busy Time:               29
Power Cycles:                       77
Power On Hours:                     26
Unsafe Shutdowns:                   18
Media and Data Integrity Errors:    0
Error Information Log Entries:      200
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Temperature Sensor 1:               24 Celsius
Thermal Temp. 1 Transition Count:   43
Thermal Temp. 1 Total Time:         52

Error Information (NVMe Log 0x01, max 64 entries)
No Errors Logged

```

---

### Post by TheFu on 2020-10-08
Did you wait until the test finished before running the next command?  There should be a multi-column table in the output.
All that's being shown is the header data.

---

### Post by RegUB on 2020-10-08
> **TheFu said:**
> Did you wait until the test finished before running the next command?  There should be a multi-column table in the output.
All that's being shown is the header data.

That is the entire output (did you scroll it?). The smartctl -t command, however, did not take minutes but finished immediately (with 0 return code).

---

### Post by TheFu on 2020-10-08
[https://ubuntuforums.org/showthread.php?t=2447204&p=13974176#post13974176](https://ubuntuforums.org/showthread.php?t=2447204&p=13974176#post13974176) has example output.  The table with 
```
....
187 Uncorrectable_Error_Cnt 0x0032 100 100 000 Old_age Always - 0
195 ECC_Error_Rate 0x001a 200 200 000 Old_age Always - 0
198 Offline_Uncorrectable 0x0030 100 100 000 Old_age Offline - 0
199 CRC_Error_Count 0x003e 253 253 000 Old_age Always - 0
232 Available_Reservd_Space 0x0013 095 095 000 Pre-fail Always - 3108
241 Total_LBAs_Written 0x0032 099 099 000 Old_age Always - 29069747454
242 Total_LBAs_Read 0x0032 099 099 000 Old_age Always - 64077724089
...

```
is what I expected, though that poster didn't post the data very nicely inside code-tags, so we got ugly formatting.

Think this [https://serverfault.com/questions/928675/smartctl-6-6-missing-attributes-table](https://serverfault.com/questions/928675/smartctl-6-6-missing-attributes-table) explains it.

Well, I think you are stuck.  If it were me, I'd wipe the partition, reformat, restore my data and see if that doesn't correct whatever got messed up.  If that isn't viable, I'd have really good backups, assume the disk will fail any day, and hope it lasts 5 yrs. I'd get used to the lies for that file system.

---

