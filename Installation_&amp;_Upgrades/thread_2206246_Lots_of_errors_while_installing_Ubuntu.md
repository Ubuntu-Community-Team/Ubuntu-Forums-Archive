---
title: "Lots of errors while installing Ubuntu"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by sicloan67 on 2014-02-18
Hi, 

I'm totally desperate. I try t install Ubuntu without success since two days. I read a lot of messages o forums, read instruction manuals... but I still have all my problems. 

I have a PC (desktop) with windows 7 and I want to have a dual boot. 
Configuration : Two hard drive, RAM : 8 Go, intel i7, 2.88 Ghz.

What I do : 

Defragmentation of my hard drive C:. (hard drive array0)
Use of Easeus to make some place.
Download the latest release of ubuntu.
Use live linux usb to make a bootable usb.
Restart my computer.
Use the option "install linux alongside the others"
Go to the choice of time zone
Have an error with no text but interrogation markets (title : ??? message : ???)
Cannot continue, have to quit
Return to the menu : the choice "install alongside" has disappeared
choose "do somethings else"
leads to the same error at the same point

After this experience, I tried to use linux on live. Using the command sudo parted -l I get the following :

```
it@it:~$ sudo parted -l
Error: Can't have a partition outside the disk!                           

Error: /dev/sdb: unrecognised disk label                                  

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_bcjecidibe_ARRAY1p1: 67.7GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  67.7GB  67.7GB  ntfs


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_bcjecidibe_ARRAY1: 67.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  67.7GB  67.7GB  primary  ntfs


Error: /dev/mapper/isw_bcjecidibe_ARRAY0p8: unrecognised disk label       

Error: /dev/mapper/isw_bcjecidibe_ARRAY0p7: unrecognised disk label       

Error: /dev/mapper/isw_bcjecidibe_ARRAY0p6: unrecognised disk label       

Error: /dev/mapper/isw_bcjecidibe_ARRAY0p5: unrecognised disk label       

Error: Can't have a partition outside the disk!                           

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_bcjecidibe_ARRAY0p3: 1468GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1468GB  1468GB  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_bcjecidibe_ARRAY0p2: 10.3GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  10.3GB  10.3GB  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_bcjecidibe_ARRAY0p1: 90.4MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  90.4MB  90.4MB  fat16


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_bcjecidibe_ARRAY0: 1933GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size     Type      File system  Flags
 1      32.3kB  90.5MB  90.4MB   primary   fat16        diag
 2      91.2MB  10.4GB  10.3GB   primary   ntfs         boot
 3      10.4GB  1478GB  1468GB   primary   ntfs
 4      1478GB  1933GB  455GB    extended
 6      1478GB  1488GB  10000MB  logical
 7      1488GB  1492GB  4000MB   logical
 8      1492GB  1924GB  432GB    logical
 5      1924GB  1933GB  8547MB   logical


Model: Kingston DataTraveler G2 (scsi)
Disk /dev/sdg: 4003MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4003MB  4003MB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label 
```


I go back to windows, free again the place 'unloccated' retry this last command. This time the line 

```

 4      1478GB  1933GB  455GB    extended
 6      1478GB  1488GB  10000MB  logical
 7      1488GB  1492GB  4000MB   logical
 8      1492GB  1924GB  432GB    logical
 5      1924GB  1933GB  8547MB   logical

```

have disappeared. 

I do not understand what happens. I really need your help. 


I really thank you for your help.

---

### Post by TheFu on 2014-02-18
Is your Windows 
* encrypted?
* using RAID
* using disk spanning
Since you already have logical partitions, why not free some space, shrink the existing partitions, and create 2 more "plain logical" for Linux?

I'm unclear why there is any "drive mapper" - could you please run **boot-info** (links in my signature).
If you have enough RAM and fast enough CPU, could I recommend trying virtualization?

---

