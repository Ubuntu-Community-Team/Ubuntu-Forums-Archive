---
title: "Error in partiontioning hdd"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by arun@ubunt on 2011-05-08
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=104452830720, size=395652418560, type=0x07
Entering MS-DOS parser (offset=0, size=500107862016)
MSDOS_MAGIC found
looking at part 0 (offset 1048576, size 51198820352, type 0x0b)
new part entry
looking at part 1 (offset 51199868928, size 2047868928, type 0x82)
new part entry
looking at part 2 (offset 53247737856, size 51199868928, type 0x83)
new part entry
looking at part 3 (offset 104452830720, size 395652418560, type 0x05)
Entering MS-DOS extended parser (offset=104452830720, size=395652418560)
readfrom = 104452830720
MSDOS_MAGIC found
readfrom = 1104517663744
lseek failed (Invalid argument)
Exiting MS-DOS extended parser
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it
Error: Can't have a partition outside the disk!
ped_disk_new() failed


gparted is not there on my machine and not able to install it using sudo apt-get install gparted:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "gparted"
Couldn't find any package whose name or description matched "gparted"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

tried some options but nothing helping...
absolute beginner.. plz help

---

### Post by srs5694 on 2011-05-08
It sounds like you were trying to create a partition that was too big for the device. It's also possible that your partition table has an error. To rul out the second possibility, please run the following diagnostic command:

```

sudo fdisk -lu

```

Post the output here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. That will show us what your partition table is like.

You should also show us exactly what you did with parted, if that's what you used. (If you used some other program, please identify what it was and say what you did with it.)

---

