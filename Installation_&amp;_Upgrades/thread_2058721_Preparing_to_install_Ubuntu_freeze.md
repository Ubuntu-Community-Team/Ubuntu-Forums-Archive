---
title: "Preparing to install Ubuntu freeze"
date: 2012-09-16
forum: Installation &amp; Upgrades
---

### Post by Noudledeen20 on 2012-09-16
Hi, I know a bunch of others posted about this but they always used terms I don't understand. I am a complete noob with this stuff and my windows 7 os isn't working anymore so I am going to this. Once I try to install it gets stuck at preparing to install Ubuntu. I have no idea why and in other threads they were saying things about partitions which I have no idea what they are. Please help because I am really lost. I would like step by step walk through. Thanks a ton in advance!

---

### Post by Bashing-om on 2012-09-16
Noudledeen20; Hi ! Welcome to the forum.

Not to worry, We try and get you up.

How are you attempting to install ? cd, usb, wubi ????...please advise and we take it from there.

 Do you want that ubuntu is the only operating system on your system ?

[INDENT]regards <==BDQ
[/INDENT]

---

### Post by Noudledeen20 on 2012-09-16
I am installing through usb and yes I would like it to be the only operating system. Thanks btw I didn't think anyone would actually reply. :)

---

### Post by Bashing-om on 2012-09-16
Outstanding ...

  This is a very active forum..we take care of one another... This forum's level of activity is such that a post can get to be several hours old before we can get to it///on occasion a post gets buried (rare indeed) ....

To get you up on ubuntu via usb install have a read on this howto:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

 Any questions or additional assistance -> ask .. BDQ

---

### Post by snowpine on 2012-09-16
Welcome to the forums!

The first thing you want to do is "check CD for defects" as described here: [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

The second thing you want to do is run Ubuntu in "Live" mode (without installing) to make sure it runs well and supports your hardware.

Please check back once you've done those two things. :)

---

### Post by Noudledeen20 on 2012-09-16
@SnowPine: I am not using a cd and also when I boot ubuntu, there is no option that says "check cd for defects"-probably because I am using usb stick
@Bashing-om: I just read what you put and it doesn't solve my problem. I am just booting off of a usb stick. What I am trying to do is install it to my hard drive so that I don't need the usb stick everytime I turn on my laptop. Also, with the usb stick, it takes around ten minutes to boot. The ubuntu desktop shows up and there is an app on the desktop that says Install Ubuntu 12.04.1 LTS. I click on that, but it doesn't get any further than "preparing to install Ubuntu". All it does is show the loading wheel, but it never actually gets passed that part. I'm sorry that I didn't really say this before.

---

### Post by snowpine on 2012-09-16
You should still have the option to test integrity even though it is a USB instead of a CD. If it is a bad download or bad burn then there is no solution except to download and burn again.

What are your hardware specs (CPU and RAM in particular)??

---

### Post by Noudledeen20 on 2012-09-16
Memory: 2.7GiB
Processor: AMD Semphron(tm) SI-42
Graphics: Unknown
OS type: 32-bit
Disk: 1.5GB

---

### Post by snowpine on 2012-09-16
Your computer meets the minimum specs according to: [https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)

Checking the integrity of the install medium is my recommended next step.

---

### Post by Noudledeen20 on 2012-09-16
I'm sorry, but how do I do that?

---

### Post by snowpine on 2012-09-16
> **Noudledeen20 said:**
> I'm sorry, but how do I do that?

I provided links above, there should be an option to "Check CD for errors" option when you first boot your Live USB.

---

### Post by Bashing-om on 2012-09-16
the link I supplied is the instructions to get the install onto hard disk from a usb device.

we await your response to snowpine's directives.

[INDENT][INDENT]regards <==BDQ
[/INDENT][/INDENT]

---

### Post by Noudledeen20 on 2012-09-16
There is no option for that.. The only options I have are: 
-Run Ubuntu from this USB
-Install Ubuntu in a Hard Disk
-Test Memory
-Boot from first hard disk
-Advanced Options >
-Help
"boot from first hard disk" does nothing and advanced options only has the option of going back..

---

### Post by Noudledeen20 on 2012-09-16
I followed the howto and it tells me to use GParted but my Gparted doesn't allow me to do anything because it is still "Searching /dev/sdb partitions"

---

### Post by Bashing-om on 2012-09-17
Noudledeen20;

 At the present time I am at a loss as to how to proceed.
 These items bother me.
1. I assume only the one hard disk is installed.
      a. only 1.5 GB disk (not enough to install on) [surely a type-o]
      b. one disk and Gparted is seeing as sdb rather than the expected sda
2. I do not know how to verify the integrity of the usb  --insert it into another computer, see if it will install ???--

Lets take a look at the disk and see what we see.

boot back into the live mode "try ubuntu":
from terminal post the output of 
```
sudo fdisk -lu
sudo parted -l
```(these are lower case 'L"s)
Might provide some info as to what the disk is up to !
[INDENT]regards <==BDQ 
[/INDENT]

---

### Post by Noudledeen20 on 2012-09-20
Sorry for late reply.. internet messed up... This is what I got after typing those in: 


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 2056 MB, 2056257536 bytes
16 heads, 32 sectors/track, 7844 cylinders, total 4016128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75e05295

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32     4016127     2008048    6  FAT16

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x118bd073

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sdb2         3074048   471748607   234337280    7  HPFS/NTFS/exFAT
/dev/sdb3   *   471748608   488396799     8324096    7  HPFS/NTFS/exFAT



ubuntu@ubuntu:~$ sudo parted -l
Model: Memorex TD Classic 003B (scsi)
Disk /dev/sda: 2056MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  2056MB  2056MB  primary  fat16        boot


Model: ATA TOSHIBA MK2555GS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1574MB  1573MB  primary  ntfs         diag
 2      1574MB  242GB   240GB   primary  ntfs
 3      242GB   250GB   8524MB  primary  ntfs         boot

---

### Post by Bashing-om on 2012-09-21
Noudledeen20;

  My apologies for leaving you hanging ( busy with other threads and life does intrude on our passtimes  !)
To insure the integrity of the usb install medium, this is the suggested methologies:
[https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM)
[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

Boot up the computer using the newly made  install on USB stick

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) 
[INDENT][INDENT]hth <==BDQ
[/INDENT][/INDENT]

---

### Post by akshatk on 2012-12-23
hi,

m facing same issue while trying to install lubuntu 12.10.

m using a cd, i checked its mdsum, burnt it with lowest rate, also checked the cd via "check disc for errors".

no error came in above mentioned tests.

please help ??

---

### Post by Bashing-om on 2012-12-23
akshatk;

Set in bios to boot from cd as 1st priority ?
Insert the install disk, wait a bit for ubuntu to load. Do you get to the greeter screen with the two options: 
a) try ubuntu
b) install ubuntu 
Then: what is the result of choosing "try ubuntu" ?

[INDENT][INDENT]willing to help ==> BDQ

[/INDENT][/INDENT]

---

