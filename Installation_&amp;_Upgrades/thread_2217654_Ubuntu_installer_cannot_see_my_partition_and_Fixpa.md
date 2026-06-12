---
title: "Ubuntu installer cannot see my partition and Fixparts does not work"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by dhruba1 on 2014-04-18
I tried to install Ubuntu before and managed to do that easily alongside with Windows 8, but then I had to delete that for some reason and now I cannot install Ubuntu at all. The previous version was 13.10 and now everytime I try to install any version of ubuntu it cannot see my partition. I Googled a little and found out the fixparts  tutorial, but in my case the return is 
"Warning: 0xEE partition doesn't start on sector 1. This can cause problems in some OSes."
but I was supposed to get a prompt about cleaning my stray GPT data. Can anyone help me?

I am using a first generation core i3 laptop. As a noob here I do not really know what I should have included with this problem

---

### Post by Bashing-om on 2014-04-18
dhruba1; Hi !

Windows is not in my sphere of interest, but to nudge this along;
Windows 8 = UEFI and you need to download and install some additional tools to look at the hard drive.
Boot up the install DVD -> "try ubuntu" mode; -> terminal.
Install gdisk:
```

sudo apt-get install gdisk

```
Post back the out puts of terminal commands:
```

sudo parted -l
sudo gdisk -l /dev/sda

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

As a place to start looking.
[INDENT][INDENT]when we know more
[INDENT][INDENT][INDENT]can advise better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dhruba1 on 2014-04-18
I have just downgraded to windows 7. I will soon post the results after restart. Thanks for your interest to help :)

---

### Post by oldfred on 2014-04-18
Did you install in UEFI boot mode or BIOS mode mode?

If drive was gpt and you reinstalled Windows in BIOS mode it does not correctly convert drive to MBR(msdos). Post commands suggested above by bashing-om.
Windows only boots with UEFI from gpt drives.
Windows & Ubuntu only boot from MBR drives with BIOS.

---

### Post by dhruba1 on 2014-04-19
Here is what I got. I do not know much about UEFI and BIOS but I guess it is in BIOS mode given my laptop is 4 year old. I guess I have leftover GPT data, but fixparts cannot find that
```
. 
[COLOR=#000080]ubuntu@ubuntu:~$ sudo parted -l
Error: Can't have overlapping partitions.                                 

Model: JetFlash Transcend 8GB (scsi)
Disk /dev/sdb: 8097MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8097MB  8096MB  primary  fat32        boot, lba


ubuntu@ubuntu:~$ sudo -l /dev/sda
sudo: /dev/sda: command not found
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 558ABF8F-4E30-4BE7-BD41-A7439AA1CD98
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 1-sector boundaries
Total free space is 5415 sectors (2.6 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63        73722284   35.2 GiB    0700  Microsoft basic data
   2       278518968       380917214   48.8 GiB    0700  Microsoft basic data
   5        73722348       152970929   37.8 GiB    0700  Microsoft basic data
   6       152970994       225632924   34.6 GiB    0700  Microsoft basic data
   7       225632988       278518904   25.2 GiB    0700  Microsoft basic data
   8       380917278       488392064   51.2 GiB    0700  Microsoft basic data[/COLOR]

```

---

### Post by oldfred on 2014-04-19
It looks like this is the error?
[COLOR=#000080]Error: Can't have overlapping partitions.

[/COLOR]And running fixparts may have converted to gpt not remove extra old gpt data. 
If system is 4 years old you probably did not have gpt partitions.[COLOR=#000080]
[/COLOR]

---

### Post by dhruba1 on 2014-04-19
What should I do now? With this I will never be able to install any version of Ubuntu :(

---

### Post by Bashing-om on 2014-04-19
dhruba1: Hello,

Not a hopeless situation by any means.
[INDENT]What I would do:[/INDENT]

I would wipe that disk, and start all over.
Install Windows ->
In Windows run defrag a couple of times AND then in Windows shrink the Windows Partition to make room for ubuntu to be installed onto, There are a couple of methods. In that legacy partition scheme one can only have 4 primary partitions, now one of those primary partitions may be allocated as "extended" and within this "extended partition" one may have as many logical partitions as one desires. ubuntu will happily install within that "extended partition". When done with the Windows partitioning - set up, in Windows run check disk to make sure windows is happy happy. IF there are but 3 primary partitions (not likely) you can make an "extended partition" for Ubuntu. The ubuntu install requires a minimum of 2 partitions, One for '/' (root) and one for 'swap'. Once you are in the ubuntu installer choose "something else" and direct the installation to the partition that you have prepared ( ubuntu: terminal command 'sudo fdisk -lu' so you know what partition is for ubuntu). 

The easier solution is to wipe that disk, re-install Windows and in the ubuntu's installer, choose the option "install along side" and let the install wizard take care of all the details. If the install wizard sees that it can install. Else the above will need to be done.

If you are the more comfortable you may post back - after Window is re-installed the output from the ubuntu liveDVD of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

``` To show us the current disk layout and a continued discussion of your options to install ubuntu and keep Windows.

[INDENT][INDENT]we will keep plugging away
[INDENT][INDENT]'till the deed is done
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dhruba1 on 2014-04-19
wiping the disk is not an option for me.. otherwise I could format and partition the whole hdd from the Ubuntu setup. The setup sees my hdd as one unallocated disc and wants to partition and format the whole thing

---

### Post by Bashing-om on 2014-04-19
dhruba1; Welp;

> 
Error: Can't have overlapping partitions.


I do not know what else can be advised.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]othertimes I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-04-19
Post output from commands suggested by bashing-om in post #8.

---

