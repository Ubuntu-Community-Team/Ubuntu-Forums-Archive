---
title: "Trouble installing Ubuntu 12.10 on Samsung NP700Z3C"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by tL0z on 2012-12-25
Hey guys,

I got a new laptop and I am having some trouble installing Ubuntu 12.10.

When I install with the Live CD I get an error saying:
> **Error removing intramfs-tools**
sub process installed post-installation script returned error status 1

I am able to restart and get to Grub but then I choose Ubuntu and it breaks.

Thinking it was something wrong with the DVD (even though I tick the option to update the packages), I tried with the mini-iso. With the mini-iso I get an error at the step 'Configuring  linux-image-3.5.0-21-generic'. It gets an error when instaling linux-generic-pae.

The laptop came with W7 pre-installed.

What might be wrong?

Thank you for your help!

---

### Post by oldfred on 2012-12-26
How new is system? Does it have UEFI and/or Intel SRT (a small SSD to speed Windows)?

Post this from live installer's terminal.

        sudo parted /dev/sda unit s print

---

### Post by tL0z on 2012-12-27
Hey oldfred!

Thanks for your reply.

Yeah, it does have an SSD. Actually, I'm not sure what to do with it. What do you suggest? I was thinking of using it as swap.

Here is the output:

> ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start        End          Size         Type      File system     Flags
 1      2048s        206847s      204800s      primary   ntfs            boot
 2      206848s      512206847s   512000000s   primary   ntfs
 4      512208894s   1900912639s  1388703746s  extended
 7      512208896s   512266239s   57344s       logical   ext4
 8      512268288s   543510527s   31242240s    logical   linux-swap(v1)
 6      543518720s   924348415s   380829696s   logical   ext4
 5      924352512s   1900912639s  976560128s   logical   ext4
 3      1900912640s  1953523711s  52611072s    primary   ntfs            diag

ubuntu@ubuntu:~$ sudo parted /dev/sdb unit s print
Model: ATA SanDisk SSD i100 (scsi)
Disk /dev/sdb: 15649200s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End        Size       Type     File system  Flags
 1      2048s  15646719s  15644672s  primary

I am not sure about UEFI. How do I find out?

Cheers

---

### Post by oldfred on 2012-12-27
Partition table is msdos ( or MBR) and you have an extended partition. So you do not have UEFI.

It looks like you installed and must have the RAID turned off? I do not understand the RAID that Intel uses, but some others posted how they either installed to the SSD and never use the SRT feature or installed to hard drive and turned SRT back on.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Quotes from above threads.
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

    

---

### Post by tL0z on 2012-12-31
Hey oldfield,

There is nothing in the BIOS related to SRT and according to dmraid I do indeed not have RAID on.

I resized my disk partitions using GParted. Might that be the problem? I just tried to install the system again using the LiveCD and I confirmed what error it is. It points to this [entry]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/220961").

How can there not be enough disk space?

This is frustrating. It used to be so simple to install Linux, grr! :(

Thanks!

---

### Post by grahammechanical on 2012-12-31
You might want to read the 12.10 release notes under Known Issues. It does not mention your laptop specifically but it comes close to it.

> Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557)

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop")

Regards.

---

### Post by tL0z on 2012-12-31
Hey Graham,

Yeah, I have tried with the Legacy support both on and off. It still fails on the same step which, by the way, is:
"Running post-instalation trigger initramfs-tools"

Cheers

---

### Post by oldfred on 2012-12-31
The bug report on space looked like it applied more to Virtual Memory installs with 8GB or less. 

Did you verify that download was good?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
    
Are you installing 64bit version. Just be sure not to boot in UEFI mode.

---

### Post by tL0z on 2012-12-31
I was trying with 32bit before. I just tried with the 64bit minimal install and got the same error in the "installing linux-generic" step.

I just confirmed that the downloaded files have the correct md5sums.

Yeah, UEFI is disabled in the BIOS.

---

### Post by tL0z on 2013-01-01
lol, this is embarassing.

Basically, I wasn't giving /boot enough space - only 30MB!

Problem is solved! :)

I ended up having just / and /home. Is it worth to have a separate partition for /boot? I have it in my old laptop with Arch, but I never actually justified having it.

---

### Post by oldfred on 2013-01-01
Most desktop installs do not need a separate /boot. If it works you do not need /boot. :)

 Servers, LVM, RAID or very old systems that cannot boot if partition is beyond 137GB and a few other special cases.

---

