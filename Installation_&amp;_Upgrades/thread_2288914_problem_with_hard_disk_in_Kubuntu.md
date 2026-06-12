---
title: "problem with hard disk in Kubuntu"
date: 2015-07-30
forum: Installation &amp; Upgrades
---

### Post by keithunder on 2015-07-30
paste.ubuntu.com/11968622 from the boot repair program

No known boot loader is installed in the MBR of /dev/sda.

I am a beginner when it come to problems like this. There are a lot of photos on the hard drive that my friend would like to recover.

The disk is still visible in the bios.

If it can be fixed great .. if not how can I recover the data??

Help!

---

### Post by Bashing-om on 2015-07-30
keithunder; Hello;

Well:
> 
If it can be fixed great .. if not how can I recover the data??


With a liveDVD(USB) the system is always fixable.
So, do you have on-hand the medium you used to install kubuntu ?

Now boot up the liveDVD of Kubuntu in " try ubuntu " mode to a terminal:
post back the outputs - Between Code Tags - of terminal commands:
```

sudo fdisk -lu
parted -l

```
Which will show:
The partitions on the hard drive(s)
If the kubuntu file system is present
where to install the bootcode 

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once we have this information, we have an idea of exactly what to do.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by keithunder on 2015-07-30
Wow   thanks for the prompt reply
```

kubuntu@kubuntu:~$ sudo fdisk -lu
kubuntu@kubuntu:~$ parted -l
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk! 


```

This does not look like good news to me at least!

---

### Post by Bashing-om on 2015-07-30
keithunder; Yukkie;

yes we have no hard drives
> 
This does not look like good news to me at least!

concur, does not look well for the home team.

So now we are in the realm of hardware issues.
Ya got access to another hard drive ? and spare this one off, see if bios sees this other hard drive .
swap out the hard drive's cables both the power cable and the SATA cable . ( assuming you do not have a volt meter to see what the voltage on the power cable is ).
Spare off the sata controller board port to another port.
Stick that hard drive in a different box with new cables, is the drive then recognized ?

As advised, 'til bios sees that hard drive, there is nothing we can do at our level.

[INDENT][INDENT]what to do
[INDENT][INDENT][INDENT]what to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2015-07-30
Your pastebin shows two errors.
>  Invalid MBR Signature found.
Error: /dev/sda: unrecognised disk label



But you show an ubuntu entry in UEFI, so partitioning should have been gpt.
I might try this.
       sudo gdisk -l /dev/sda

If you do not have gdisk:
      
 sudo apt-get install gdisk

---

### Post by keithunder on 2015-07-30
```
sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): A55E0268-ED74-499B-B3F7-EB7AB5E8EF7D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2048-sector boundaries
Total free space is 488397101 sectors (232.9 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
kubuntu@kubuntu:~$ sudo fdisk -lu
kubuntu@kubuntu:~$ parted -l
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!   
```

---

### Post by keithunder on 2015-07-30
I did try swapping the data cables around with the dvd drive.. but the disk is working physically and is ok in thebios

---

### Post by Bashing-om on 2015-07-30
keithunder; K

oldfred, spot on as always.


> 
I did try swapping the data cables around with the dvd drive.. but the disk is working physically and is ok in thebios


Now we move to the realm of data recovery.
To see about fixing the partitions:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

To recover the data:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
[http://ubuntuforums.org/showthread.php?t=2112112](http://ubuntuforums.org/showthread.php?t=2112112)

[INDENT][INDENT]where there is life
[INDENT][INDENT][INDENT]there is hope
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by keithunder on 2015-07-30
THank you all very much  I have a lot of reading etc to do so I am going togo to bed first before I dive into this

---

### Post by Bashing-om on 2015-07-30
keithunder; Oh Yes !

Sleep well on this.
My meager advise, study well. A 'image' to work from is strongly advised.
Be sure of what you are doing, here there may be no room for error.

As said before time
[INDENT][INDENT][INDENT]haste makes waste
[/INDENT][/INDENT][/INDENT]

---

### Post by keithunder on 2015-07-31
using testdisk I keep getting disk errors the same as with my original paste.ubuntu.com/11968622 from the boot repair program.
I am begining to think all the data is lost
This  is my friend's machine I am thinking of replacing the hard drive and  taking the naughty one home with me where I can try and recover the data  with my windows machine!
Is this a sensible plan?
```
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition               Start        End    Size in sectors


```

---

### Post by oldfred on 2015-07-31
There is no way to recover Linux partitions from Windows. If there was a NTFS formatted partition some Windows third party tools work very well. But the best charge for the software.

You can still use a live installer of Ubuntu or Kubuntu to work on drive even if a Windows hard drive.

---

### Post by keithunder on 2015-07-31
Oh OK Thanks for that info..... I have some Linux machines at home that I will have to use!

---

