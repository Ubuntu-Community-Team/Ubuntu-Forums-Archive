---
title: "Error with installing Lucid Lynx/ Device busy"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by shaenrayce on 2011-05-26
Hello,  I had a terrible crash with Windows, and decided it was high time to migrate Linux, something I've wanted to do for a while.  Anyways, I managed to get ahold of a disk with Ubuntu 10.04 LTS.

I tried running the installer, but I got an error message saying that the installer couldn't create a partition.

I tried opening the disk utility to manually create one and got this error message:

Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=0, size=233181019392, type=0x83
Entering MS-DOS parser (offset=0, size=320072933376)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
new partition
added partition start=32256 size=233178430464
committed to disk
Error doing BLKPG ioctl with BLKPG_ADD_PARTITION for partition 1 of size 32256 at offset 233178430464 on /dev/sda: Device or resource busy


I later tried to format the disk and received this error message.

Any suggestions?

Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sda, scheme=0
got it
got disk
committed to disk
BLKRRPART ioctl failed for /dev/sda: Device or resource busy

---

### Post by uRock on 2011-05-26
Hello and welcome to the forums,

Are you running the installer from a live session? (A live session is where you boot the disk and you can use the regular menus and such.) If yes, then you need to unmount the drive. You can do this from the partition editor by right-clicking the partition(s) and selecting to "unmount"

---

### Post by tommcd on 2011-05-27
> **shaenrayce said:**
> 
I tried running the installer, but I got an error message saying that the installer couldn't create a partition.

How many partitions are on the hard drive already? From the Ubuntu live CD, open a terminal and post the output of: ```
sudo fdisk -l
```

---

### Post by shaenrayce on 2011-05-27
Thank you, Urock.  Your advice seemed to work  a little bit.  Unfortunately,  I got another error message that kept the installer from working.

[Errno 5] Input/output error: 'target/var/backups'

I was warned that my hard drive could be too old.  Is two years too old?

---

### Post by psusi on 2011-05-27
The drive may be failing.  Open the disk utility and check the SMART status and maybe run the long self test.

---

### Post by shaenrayce on 2011-05-30
Turns out my hard drive is failing.  Bummer.  Thanks for all your help

---

