---
title: "Need help with instalation plz"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by Xaulleon on 2010-12-24
Hi guys, first of all Im a beginner, I downloaded the iso from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and burned it using infra recorder. I restarted my pc to instal ubuntu however a purple screen with commands shows up and I dont know what to do, plz help.
I have a HP pavilion dv4 with windows 7

---

### Post by Quackers on 2010-12-24
What commands do you see?
Also, as a precaution, before you elect to install Ubuntu it would be wise (using a HP) to find out how many primary partitions are already in use on your hard drive. If you already have 4 primarys you will need to delete one before installing another OS.

---

### Post by Xaulleon on 2010-12-24
im using 1 partion and the typical recovery, as for the commands im gonna check right now

---

### Post by GregBrannon on 2010-12-24
An install that is going well will progress past the point you describe to a series of graphical screens that tell you what is going on, occasionally asking for input to ensure the installation is correct for your application.  In fact, you should get the opportunity to choose whether you're doing an install or running a 'live' session from the CD/DVD.  Since your install is stalling, I suggest your .iso may be bad.

You can verify whether your iso source file is correct.  The directions should be on the page from which you downloaded it, but I haven't checked.  Others have suggested that the iso should be burned to CD/DVD at the slowest speed possible to ensure that it is done correctly, but I haven't had that experience myself.

If any of the 'commands' you're seeing on the purple screen look like error messages, note what they are, copied and pasted if possible, and post those to help diagnose and correct the problem.

---

### Post by Xaulleon on 2010-12-24
alright, I tried to install but I had the same problem, heres what shows up:
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
enter 'help; for a list of built-in commands

(initramfs)mount)mount: mounting/dev/loop0 on//filesystem.squashfs failed : input/output error

can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs


*I also tried using wubi, however it said something about permission denied...

---

### Post by kansasnoob on 2010-12-24
When you first boot the Live CD you should see a purple screen with two small graphics at the bottom once the system/bios screen passes. When that screen appears you have 3 seconds to press a key (any key) to display the boot options.

If you get that screen to display then select "Check disc for defects". It takes a few minutes to run, if it passes without errors then select "Try Ubuntu without changes" and make sure the Live CD runs on your hardware.

Once you're sure the Live CD runs on your hardware you should check and see how many Primary partitions already exist. You can do so by running this command from terminal:

```
sudo parted -l
```

Mine is insane but just as an example:

```
lance@lance-desktop:~$ sudo parted -l
[sudo] password for lance: 
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.5GB  21.5GB  primary   ext3            boot
 2      21.5GB  42.9GB  21.5GB  primary   ext3
 3      42.9GB  151GB   108GB   primary   ext3
 4      151GB   500GB   349GB   extended
14      151GB   172GB   21.1GB  logical   ext4
15      172GB   193GB   21.1GB  logical   ext4
16      193GB   215GB   21.4GB  logical   ext4
17      215GB   236GB   21.4GB  logical   ext4
13      236GB   258GB   22.0GB  logical   ext4
12      258GB   280GB   21.6GB  logical   ext4
11      280GB   301GB   21.7GB  logical   ext3
10      301GB   323GB   21.8GB  logical   ext4
 5      323GB   378GB   55.1GB  logical   ext3
 6      378GB   432GB   53.6GB  logical   ext3
 7      432GB   487GB   54.9GB  logical   ext3
 8      487GB   498GB   10.7GB  logical   ext3
 9      498GB   500GB   2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  642MB   641MB   primary   ext3
 2      642MB   9215MB  8573MB  primary   ext3
 3      9215MB  80.0GB  70.8GB  extended
 5      9216MB  78.9GB  69.7GB  logical   ext3
 6      78.9GB  80.0GB  1130MB  logical   linux-swap(v1)

```

You can see from that I have two drives and on the 500GB drive I have many partitions but only 3 are primary partitions, the rest are logical partitions created within an extended partition.

Should you find that you already have 4 primary partitions STOP! You'll need help!

You should also know that bugs exist in the new 10.10 live installer:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by Xaulleon on 2010-12-24
I tried checking the disk for errors but I got the error that I mentioned on top

---

### Post by Xaulleon on 2010-12-24
ima download the 10.04 version to see what happens...

---

