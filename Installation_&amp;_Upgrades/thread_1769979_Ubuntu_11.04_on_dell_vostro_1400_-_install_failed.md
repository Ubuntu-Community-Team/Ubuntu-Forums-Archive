---
title: "Ubuntu 11.04 on dell vostro 1400 - install failed"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by skolnick on 2011-05-28
Hi!

I have a laptop dell vostro 1400 (core 2 duo T7500, 4GB RAM, 500GB Seagate hard drive) and I'm trying to install ubuntu desktop 11.04 on it. It has a 500GB Seagate hard drive. The problem is that when installing, after creating the partition (I create only a 20GB /, 2GB swap and the rest /home) it will complain that the partition /home is too small (which is not possible, since it's more than 400GB) and it should be at least this size: 0TB0 (whatever that means). Here's the exact error:

Some of the partitions you created are too small, Plaese make the following partitions at least this large: /home 0TB0

After this error, it gives the option to continue or go back to correct the "error". If I go back, no matter what I do, the error remains the same and if I continue, then during the copy of files stage it will fail complaining about an I/O error. I don't know what to do at this point. This laptop has worked fine with linux before (it has had all fedora editions from 8 to 14 working perfectly) and this is the first time I try ubuntu on it.

I already checked the MD5 of the ISO and it's OK, and also burned the CD twice (once in linux, the other time using a mac) but both fail in the exact same way.

Thanks for any help, I already use ubuntu (10.04) on my desktop and I kind of like it, and wanted to test the new Unity :)

Regards.

Germán.

---

### Post by Hedgehog1 on 2011-05-28
We need to get familiar with your partition layout.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

[IMG]http://img694.imageshack.us/img694/2095/bartsimpsonchalkboard.png[/IMG]

---

### Post by skolnick on 2011-05-28
Hi!

Thanks for your advice, I ran the script as you suggested and these are the results:

```
ubuntu@ubuntu:~/Documents$ cat RESULTS.txt 
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy is installed in the MBR of /dev/sda and looks at sector 18751 
    on boot drive #1 for the stage2 file, but no stage2 files can be found at 
    this location..

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    39,999,487    39,997,440  83 Linux
/dev/sda2          39,999,488   972,773,375   932,773,888  83 Linux
/dev/sda3         972,773,376   976,771,071     3,997,696  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        436c43b0-70b2-48a8-8ac1-20f78721a5b4   ext4       
/dev/sda2        9972bdec-677c-452d-af59-4682f5d1e20b   ext4       
/dev/sda3        e88b3d51-9ea6-4864-a52c-15d635872058   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=436c43b0-70b2-48a8-8ac1-20f78721a5b4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=9972bdec-677c-452d-af59-4682f5d1e20b /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=e88b3d51-9ea6-4864-a52c-15d635872058 none            swap    sw              0       0
--------------------------------------------------------------------------------


ubuntu@ubuntu:~/Documents$ 

```

I don't really see anything strange about it, if you do, please advice me.

Regards,

German.

---

### Post by Hedgehog1 on 2011-05-30
This is a puzzler.

Other then see vestiges of the older grub on the disk (which should be harmless as you are about to install the new grub in the process); things look OK to me also.

If you have not done so already, does your situation allow you to wipe the partition map in the disk for a completely clean install?


[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://img858.imageshack.us/img858/9979/mbrpariondemo03.png[/IMG]


And then create your partitions as intended.

Other than that I am out of ideas to try.

***The Hedge***

:HS

---

### Post by skolnick on 2011-05-30
Hi!

I am also completely out of ideas on this. I already tried the following:

1. Recreated the partition table as you suggested - same error
2. Checked the RAM on the laptop with memtest86+ - passed twice with no error
3. Tried to install Ubuntu 10.10 - this installs with no error at all

So, based on the above results, I would tell this is definitely a bug on the ubuntu 11.04 installer, and it doesn't allow the installation of Ubuntu desktop 11.04 on my laptop. Strange, as this is an old and supposedly well-supported laptop, but anyway.

I ended installing Fedora 15 on it (it works like acharm) whch is too bad, since I really wanted to test unity. Guess I'll have to try it on a virtual machine.

THanks again, and best regards.

Germán

---

