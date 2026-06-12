---
title: "Problem installing Ubuntu 11.04 - No root system defined- !"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by daca00991 on 2011-07-29
As it was discussed many time before  this problem,and i noticed that not everyone had same way of fixing it i decied to open new post so i can figure out what is mine.

Downloaded wubi from ubuntu site,started it and waited till it dowanload-installed ubuntu on my pc.Rebooted,started ubuntu,as it was prepering fot installation at loading "verifying config" window at the end of it it poped out new window "No root system defined... " 

So i am wondering is there a chance of helping me fixing my problem.

Cheers!

---

### Post by jerrrys on 2011-07-29
i have never used wubi.  wubi is an excellent way to just to try ubuntu.  kind of like for taking a car for a test drive.  i would suggest instead just do a side by side install. 

the downside of this is ubuntu boot will take over windows boot.  so if you decide to remove it you need your windows recovers cd.

for just trying out ubuntu and giving yourself some room to play with would require 10G

---

### Post by bcbc on 2011-07-29
> **daca00991 said:**
> As it was discussed many time before  this problem,and i noticed that not everyone had same way of fixing it i decied to open new post so i can figure out what is mine.

Downloaded wubi from ubuntu site,started it and waited till it dowanload-installed ubuntu on my pc.Rebooted,started ubuntu,as it was prepering fot installation at loading "verifying config" window at the end of it it poped out new window "No root system defined... " 

So i am wondering is there a chance of helping me fixing my problem.

Cheers!
Usually the no root filesystem issue is caused by an unsupported raid setup or a mix of MBR and GPT partition tables or some other partition problem that Ubuntu is sensitive to (and not windows).

Boot from a live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") - this normally gives enough clues to the problem.

PS you'll have this same problem trying to do a direct install.

---

### Post by chauwa on 2011-07-29
Hello.
I have a similar problem, I can not install any linux when it is active ICH10 raid 0. Normal installation destroys W7 start, after the repair you can not even update the raid array because w7 is like cheese


last hope wubi instaler also is not working, just after the start asking for change mount the directory, see the disks, partitions, but not working, you can not even format

---

### Post by bcbc on 2011-07-29
> **chauwa said:**
> Hello.
I have a similar problem, I can not install any linux when it is active ICH10 raid 0. Normal installation destroys W7 start, after the repair you can not even update the raid array because w7 is like cheese


last hope wubi instaler also is not working, just after the start asking for change mount the directory, see the disks, partitions, but not working, you can not even format

If the normal install doesn't work with your raid setup, neither will wubi. Your best bet is a virtual machine. I've used virtual box and vmware and they both work reasonably well (except you don't get the graphics acceleration.) Or you could install it on another drive (e.g. external).

---

### Post by daca00991 on 2011-07-30
```

```          Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   912,359,423   911,947,776   7 NTFS / exFAT / HPFS
/dev/sda3         912,359,424   955,219,968    42,860,545   5 Extended
/dev/sda5         912,361,472   955,219,967    42,858,496   7 NTFS / exFAT / HPFS
/dev/sda4         955,219,968   976,773,119    21,553,152  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        74042DCC042D91E2                       ntfs       
/dev/sda2        EC182F6E182F374C                       ntfs       
/dev/sda4        C27A34FF7A34F1B1                       ntfs       LENOVO_PART
/dev/sda5        F84071324070F928                       ntfs       LENOVO

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

---

### Post by daca00991 on 2011-07-30
Here is boot info scrip,got it booting from Live CD.I hope it tells you guys something!

Cheers!

---

### Post by bcbc on 2011-07-30
What's the output of:
```
sudo parted -l 
```

(that's a lower case -L ; you'll need to boot the live CD again to do this)

---

### Post by daca00991 on 2011-07-30
Error: Can't have overlapping partitions.                                 

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label


this is what appears after sudo parted -l

---

### Post by srs5694 on 2011-07-30
I don't know if it's related to your main problem, but one issue is that your extended partition (/dev/sda3) is one sector too long. This causes it to overlap with the following partition (/dev/sda4) by one sector. Fortunately, the one logical partition contained in the extended partition (/dev/sda5) is short enough that you can safely resize the extended partition. You can do this most easily with my [FixParts](http://www.rodsbooks.com/fixparts/) program. Read its Web page for usage details. Alternatively, you could use sfdisk to do the job, but that's a little more involved and provides more opportunities for human error to mess things up.

---

### Post by bcbc on 2011-07-30
Yes that'll do it. I swear I stared at that fdisk output but missed the overlapping sector... but 'parted' and *srs5694* got it.

So basically if there is any error like that, the installer will fail and this affects Wubi as well as normal installs.

---

### Post by daca00991 on 2011-07-30
So,i only start FixParts and thats it.  

```

```ubuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.7.1

Loading MBR data from /dev/sda

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0xC3FFC3FF
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048       411647   primary              Y      0x07
   2                411648    912359423   primary              Y      0x07
   4             955219968    976773119   primary              Y      0x12
   5             912361472    955219967   logical     Y        Y      0x07

MBR command (? for help):

---

### Post by chauwa on 2011-07-30
> **bcbc said:**
> If the normal install doesn't work with your raid setup, neither will wubi. Your best bet is a virtual machine. I've used virtual box and vmware and they both work reasonably well (except you don't get the graphics acceleration.) Or you could install it on another drive (e.g. external).

virtual machine +ubuntu not work ;) debian work ;d

I managed to solve the problem, I did two volumes from the controller (CTRL +I) Volume0 75GB and Volume1 1,2T.

I installed W7 64 in volume2 and partition volume2 part 1  NTFS and part 2 ext3 and part 3swap volume1 otherwise unchanged install "easyBCD" add new entry-
NeoSmart ISO Entry(iso debian)-load from memory volume2 

Installed  XP in Volume1 and install paragon "partition manager" and  
"Boot-US" I created a boot manager Volume1 and boot disk emergency for FD0

Now install ubuntu boot volume 2 iso debian ;) install and format ext3 to ext4 hmoe/  grub instal VOLUME2 no SDA grub- destroy everything

Now CD W7 and startup repair and very fast click to repair(before you will see the info with you can not fix, you must be very fast), now start w7 volume2 and go partition manager and update mbr

boot fd0 emergency disk load XP and reinstal bootmanager Boot-US

go w7 and easyBCD add entry linuks- save.Do not overwrite mbr-update



> There are a total of 4 entries listed in the bootloader.

Default: Windows 7 Ultimate 
Timeout: 10 seconds
EasyBCD Boot Device: D:\

Entry #1
Name: Windows 7
BCD ID: {3d32dcce-b76d-11e0-b18b-8373ac45ea81}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: Windows 7 Ultimate 
BCD ID: {current}
Drive: D:\
Bootloader Path: \Windows\system32\winload.exe

Entry #3
Name: linuks ubuntu
BCD ID: {dc301628-ba3b-11e0-ac9e-00261884e793}
Drive: D:\
Bootloader Path: \NST\AutoNeoGrub0.mbr

Entry #4
Name: Windows XP
BCD ID: {26fce0cb-baa0-11e0-a0dd-00261888e108}
Drive: D:\
Bootloader Path: \NST\easyldr1everything is elsewhere than the shows but the program works reliably

now Volume1 xp,volume2 part2ubuntu,part1 w7 boot no problem ;)very tortuous and unfortunately I know very little English,  work will greet

---

### Post by srs5694 on 2011-07-30
> **daca00991 said:**
> So,i only start FixParts and thats it.  

```

ubuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.7.1

Loading MBR data from /dev/sda

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0xC3FFC3FF
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048       411647   primary              Y      0x07
   2                411648    912359423   primary              Y      0x07
   4             955219968    976773119   primary              Y      0x12
   5             912361472    955219967   logical     Y        Y      0x07

MBR command (? for help):
```

You've got to use the "w" command to save the changes, but that's it. FixParts is showing all your partitions (except for the extended partition, which as the program's output specifies, doesn't show up in the list by design), so it looks OK.

BTW, when posting the output of programs, and especially those that format things in columns, it's best to post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags; that preserves the formatting and makes it easier to read. I've added those tags to the above-quoted output, but that sometimes doesn't work right when quoting.

---

