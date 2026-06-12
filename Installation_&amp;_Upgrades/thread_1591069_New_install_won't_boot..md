---
title: "New install won't boot."
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by elosier on 2010-10-08
I have a machine I'm trying to install 10.04 on.  During the install everything works right, but after reboot it drops to busybox and complains that /dev/mapper/pdc_igjhadhe3 does not exist.

The setup is a raid array consisting of 2 identical 1TB caviar green (for a total of 2TB).

I booted the livecd and started disk utility and gparted to see what was there. Disk Utility sees the two hard drive has /dev/sda and /dev/sdb under Sata Host Adapter and it seems to see the raid array as /dev/mapper/pdc_igjhadhe under Peripherals.  When I try to run benchmark on that I get an error message saying that 'The deamon is being inhibited'.
Gparted only sees /dev/sda and /dev/sdb as 2 unalocated 931.51Gb drives (it doesn't see the combined array of 2TB).

Yet, when I do the install everything works well.  I tried to use the entire disk as one partition and then tried again but this time defining my partition (1 /, 1 swap and the rest for /home).  When I get to chose, the only choice I have to to partition /dev/mapper/pdc_igjhadhe.

Anybody has any idea what's going on or what I'm doing wrong?

---

### Post by ronparent on 2010-10-08
I believe the major problem you describe occurred in 10.4 and have been fixed in 10.04.1.

Gparted needs the install of a small program called kpartx to enable it to see the raid partitions. Otherwise your main problem on the boot may be that you left the install to try to install the grub boot loader on sda. That doesn't work! To boot from a raid the boot loader must be installed to the root raid device (the first name after Control in a list of similar names listed in /dev/mapper. This is fixable. Reinstall grub per this: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

Your target for mounting to /mnt is the raid partition you installed to. The next command is to reinstall and the boot loader location is the the entire array as I just described (ie sudo grub-install --root-directory=/mnt/ /dev/mapper/<YourRaidArrayName>). This grub 2 reinstall usually works like magic (provided you wrote =/mnt/) and starts your new install on the first boot. Good luck.

If for some reason you run into more problem with the boot, post the outcome here.

---

### Post by elosier on 2010-10-08
When I try to mount I get an error message saying that I need to enter the right filesystem.  When I do ('-t ext4') it says it's the wrong filesystem.
```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/pdc_igjhadhe /mnt/
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/mapper/pdc_igjhadhe /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/mapper/pdc_igjhadhe,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Here's the result of boot_info_script.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 335823528 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Grub 2 is installed in the MBR of /dev/mapper/pdc_igjhadhe and looks at 
    sector 335823528 of the same hard drive for core.img, but core.img can not 
    be found at this location.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

pdc_igjhadhe1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

pdc_igjhadhe2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

pdc_igjhadhe3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,906,788,095 3,906,788,095  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1             256   390,625,023   390,624,768 Linux or Data
/dev/sda2     390,625,024   406,429,695    15,804,672 Linux Swap
/dev/sda3     406,429,696 3,906,787,071 3,500,357,376 Linux or Data

/dev/sda3 ends after the last sector of /dev/sda
Drive: pdc_igjhadhe ___________________ _____________________________________________________

Disk /dev/mapper/pdc_igjhadhe: 2000.3 GB, 2000275505152 bytes
255 heads, 63 sectors/track, 243186 cylinders, total 3906788096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_igjhadhe1                  1 3,906,788,095 3,906,788,095  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/mapper/pdc_igjhadhe1            256   390,625,023   390,624,768 Linux or Data
/dev/mapper/pdc_igjhadhe2    390,625,024   406,429,695    15,804,672 Linux Swap
/dev/mapper/pdc_igjhadhe3    406,429,696 3,906,787,071 3,500,357,376 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_igjhadhe: PTTYPE="gpt" 
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb                                                promise_fasttrack_raid_member                               
error: /dev/mapper/pdc_igjhadhe1: No such file or directory
error: /dev/mapper/pdc_igjhadhe2: No such file or directory
error: /dev/mapper/pdc_igjhadhe3: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_igjhadhe

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on pdc_igjhadhe1


Unknown BootLoader  on pdc_igjhadhe2


Unknown BootLoader  on pdc_igjhadhe3



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/mapper/pdc_igjhadhe1: No such file or directory
hexdump: /dev/mapper/pdc_igjhadhe1: No such file or directory
hexdump: /dev/mapper/pdc_igjhadhe2: No such file or directory
hexdump: /dev/mapper/pdc_igjhadhe2: No such file or directory
hexdump: /dev/mapper/pdc_igjhadhe3: No such file or directory
hexdump: /dev/mapper/pdc_igjhadhe3: No such file or directory
```

---

### Post by ronparent on 2010-10-08
It appears you got far enough to create a complete mess. 

Let's start again. 1) What do you think you had before you started? Right now you appear to have nothing coherent. 2) What do you want to end up with? 3) What level raid are you working with - raid0 or raid1. 4) Do you intend to install another OS along side on the raid?

I can't tell for sure, but it appears that you tried to install to sda and broke the raid. If that is the case it may be best to remove all partitions, both sda and raid and start again to install on raid.  If only Ubuntu is involved use gparted in a live cd to delete the sda partitions - assuming that sda is one of the raid components. Install kpartx and use gparted again to remove the apparently defective raid partitions. 

Post your intent and I'll try to guide you.

---

### Post by elosier on 2010-10-09
> Let's start again. 1) What do you think you had before you started?  Right now you appear to have nothing coherent. 2) What do you want to  end up with? 3) What level raid are you working with - raid0 or raid1.  4) Do you intend to install another OS along side on the raid?
1) initially nothing.  Well, in fact that's not entirely true.   I had Ubuntu 10.04 installed from this machine (upgraded from 9.10) but one of the disk in the raid array crashed and I had to send for a replacement.
When the replacement came in I deleted the previous array in the raid utility during boot and created a new one with the new disk and the old still functionnng one. I then reinstalled 9.10 cuz that's the disk I had, and got the error that's currently bugging me.  I then d/led 10.04 with the same result.
2) I want to end up with a standard Desktop install that I will customize to act as a server (as it was before the disk failure).
3) It's a raid0 array.
4) no, just ubuntu.
 
>   If only Ubuntu is involved use gparted in a live cd to delete the sda  partitions - assuming that sda is one of the raid components
Yes it is, only two disk in this machine (/dev/sda and /dev/sdb) in a raid0.
Gparted doesn't see the raid disk.  It only sees /dev/sda and /dev/sdb without any partitions.  And both disk only have unallocated space, according to Gparted.

---

### Post by ronparent on 2010-10-09
You are in much better shape that I feared. The unallocated space on the devices is fine, but we have to make sure you install to the raid.

Apparently you have the 10.04 earlier release. That creates some problems, but, none that can't be overcome. The fault with gparted in that release is that in the installer it doesn't see the raid.  This is a bug that has been corrected in the later releases. If you are going to download anything I would not normally recommend a new release, but, for your I do because it seems to work with fakeraid much better.

Regardless, the 10.04 is installable with one very critical workaround. To install you need to boot to the live cd and install the program called kpartx to the session before you start the install. That install can be done using the Ubuntu add programs, Synaptics Program Manager or simply Using a terminal (sudo install kpartx). That install will only last the life of your live cd session but at that point gparted will see and modify the raid partitions. Without quitting the session, start the install from the icon on the desktop. If in the partition step (step 3 of four) you are presented only with sda and sdb with unallocated space, then you should select to manually partition. If presented with the raid, you can select to install to the entire drive.  

As long as gparted is functioning as it should for the install, the install itself should proceed fine. Post if you run into difficulties.

I should note that since you are only using Ubuntu without windows, that many would recommend you set up a pure software raid. I am neutral on this issue but have worked only with 'fakeraid' and couldn't guide you in setting that up. If you do consider a software raid setup, be aware that in turning on the raid in bios that meta data has been written to your hard drives that should be erased prior to trying to set up a software raid (a very minor issue that you need to be aware of). Best of luck in whatever you want to do.

---

### Post by elosier on 2010-10-09
I used most of my breaks to try and fix this thing today.

I booted using the live CD and installed kpartx.  That seemed to help a lot as Gparted now saw the raid array and the partitions within.  The only unknown to me was that the grub partition was labeled as an 'unknown' filesystem and several warnings.

So I proceeded to reinstall Ubuntu 10.04.1 LTS, which once again worked without errors.  But after a reboot it would not get past the post.

I tried the grub reinstall procedure suggested at the start of this thread but the grub-install complained that it couldn't find a working partition.

As a last ditch effort, I deleted the array, quick erased the drives using the Western Digital boot disk, activated AHCI in bios and tried to reinstall Ubuntu again...and (much to my dismay, I must say, because I need the whole 2TB space) it worked.  It booted without errors or warnings.

So I guess now I have to try the software raid way.  I'll have to think this through.

---

### Post by ronparent on 2010-10-09
At least with the software raid I don't think you have to commit the entire drive to a raid. Glad to hear it is progressing for you.

---

### Post by elosier on 2010-10-10
Well, I reinstalled using the 9.10 server disk.  Created a software raid array and, lo and behold, it worked.
I then upgraded to 10.04LTS without a problem and installed ubuntu-desktop.

Thank you very much for your help.  I think I would have ran in circle without it.

---

### Post by ronparent on 2010-10-10
Glad to hear you have it all worked out.

---

