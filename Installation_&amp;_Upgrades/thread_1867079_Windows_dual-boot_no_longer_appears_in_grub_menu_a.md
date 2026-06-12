---
title: "Windows dual-boot no longer appears in grub menu after upgrade"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by killerrobot on 2011-10-22
I have been successfully running ubuntu with a windows xp dual boot for a long time.  Now  I can no longer boot into windows because  it does not show up on the grub screen.  IIRC, this is the first time I've tried to boot into windows since upgrading to 11.10.  I have not changed any partitions recently and have never had raid.  I've done a bunch of searching and tried simple debugging (including boot-repair, checking grub-customizer) to no avail. 

Several bits of info follow

output of boot-info script:
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /NTLDR /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________
    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    31,455,269    31,455,207   7 NTFS / exFAT / HPFS
/dev/sda2          31,455,331   222,853,119   191,397,789   f W95 Extended (LBA)
/dev/sda5          31,455,333   199,222,064   167,766,732   7 NTFS / exFAT / HPFS
/dev/sda6         199,223,296   203,223,039     3,999,744  82 Linux swap / Solaris
/dev/sda7         203,225,088   203,710,463       485,376  83 Linux
/dev/sda8         203,712,512   222,853,119    19,140,608  83 Linux
/dev/sda3         222,853,680   625,137,344   402,283,665  83 Linux
```

I think this shows that sda1 is my windows boot partition.    I found the following regarding os-prober on sda1 in my syslog:
```
Oct 22 10:06:28 killermobot os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Oct 22 10:06:28 killermobot 50mounted-tests: debug: mounted using GRUB
Oct 22 10:06:28 killermobot 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Oct 22 10:06:28 killermobot 10freedos: debug: /dev/sda1 is a FUSE partition
Oct 22 10:06:28 killermobot 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Oct 22 10:06:28 killermobot 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Oct 22 10:06:28 killermobot 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Oct 22 10:06:28 killermobot macosx-prober: debug: /dev/sda1 is a FUSE partition
Oct 22 10:06:28 killermobot 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Oct 22 10:06:28 killermobot 20microsoft: debug: /dev/sda1 is a FUSE partition
Oct 22 10:06:28 killermobot 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Oct 22 10:06:28 killermobot 30utility: debug: /dev/sda1 is a FUSE partition
Oct 22 10:06:28 killermobot 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Oct 22 10:06:28 killermobot 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Oct 22 10:06:28 killermobot 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Oct 22 10:06:28 killermobot 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Oct 22 10:06:28 killermobot 83haiku: debug: /dev/sda1 is a FUSE partition
Oct 22 10:06:28 killermobot 83haiku: debug: Stage 1 bootloader not found: exiting

```

also the os-prober section of my grub.cfg is empty:
```
### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

```

how can i fix this?  is there more info that can help?

thank you!

---

### Post by coffeecat on 2011-10-22
You are missing the boot.ini file in your Windows sda1 parition:

> **killerrobot said:**
> 
```

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /NTLDR /NTDETECT.COM

```

Which is why:

> **killerrobot said:**
> the os-prober section of my grub.cfg is empty:
```
### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

```

The os-prober script looks for a valid bootable Windows partition and adds this if it can find all the necessary boot files.

Question: do you have or can you borrow a Microsoft Windows XP install CD? Not a manufacturer's OEM restore disc, but a genuine Microsoft one. I *think* what you need to do is to run fixboot from the Windows CD, but it's been some time since I've used XP much and I'm not 100% sure, tbh.

By the way, most of your boot script output is missing. I doubt whether it will tell us much more, but did you know that you only posted part of it?

---

### Post by killerrobot on 2011-10-22
> **coffeecat said:**
> You are missing the boot.ini file in your Windows sda1 parition:
...
Question: do you have or can you borrow a Microsoft Windows XP install CD? Not a manufacturer's OEM restore disc, but a genuine Microsoft one. I *think* what you need to do is to run fixboot from the Windows CD, but it's been some time since I've used XP much and I'm not 100% sure, tbh.


that makes sense, and yes,  I think I can get a disk tomorrow.   If someone can confirm how to repair it, that would be great.  This is actually becoming a very urgent issue as I need to be able to use this windows partition for work.  Any ideas how the boot.ini went missing in the first place?

> 
By the way, most of your boot script output is missing. I doubt whether it will tell us much more, but did you know that you only posted part of it?
yeah, sorry - i posted what I thought would be relevant

Thank you for your help.

---

### Post by killerrobot on 2011-10-22
> **coffeecat said:**
> 
Question: do you have or can you borrow a Microsoft Windows XP install CD? Not a manufacturer's OEM restore disc, but a genuine Microsoft one. I *think* what you need to do is to run fixboot from the Windows CD, but it's been some time since I've used XP much and I'm not 100% sure, tbh.

another thought on this:   would the windows repair program overwrite my whole mbr and remove grub? I'm sure that's fixable after the fact but would be another pain to deal with..

---

### Post by coffeecat on 2011-10-22
> **killerrobot said:**
> another thought on this:   would the windows repair program overwrite my whole mbr and remove grub? I'm sure that's fixable after the fact but would be another pain to deal with..

It might. I was thinking about that when posting first. I'm fairly sure (not 100%) that fixboot only repairs the boot sector in your Windows C: partition and that you need fixmbr to rewrite the Windows mbr. Having said that, it's probably wise to be prepared for fixboot "repairing" the mbr as well. At least this is easily fixable with the Ubuntu live CD.

I'll pm another member who's knowledgeable about Windows boot repair problems and ask them to look at this thread.

---

### Post by killerrobot on 2011-10-22
I got it working and it was much simpler than all of that.   A little googling told me that boot.ini is a text file that is common for most systems.  I found a web site with the contents of the file and put it where it belonged.  Then I refreshed  the grub config and everythong worked after that.

:D


in case anyone else ever has the  same issue, here's the contents of boot.ini
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=”Microsoft Windows XP Professional”/fastdetect
```

---

### Post by coffeecat on 2011-10-22
Congratulations! I never thought Windows would be tolerant of something that sounds more like a Linux fix - adding/editing a text config file. :) I'll remember this one.

Good luck!

---

