---
title: "boot fails on clean install for 11.04"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by wolfsburg18 on 2011-05-24
I just want to start off with a thanks to all the highly experienced members of this forum,, the knowledge i have gained has been fantastic.   However I have an issue at this time that I am unable to solve.

Initially I did the upgrade from 10.04 to 11.04 after ignoring the pop ups for the first few weeks.   The upgrade failed and at first I thought it was a failed disk.  I removed the raid config, tested the disks with the seagate tool and did not find a single error.   I performed a write to 0 on both disks, tested them again and everything came back clean.

I once again configured for raid 1 and did a clean install of 11.04.   The install went fine, at the end the install requested the final reboot and locked up at this point.   I forced a reboot of the system, after updating the VBI info via the MB the system just hangs, this is normally where it would boot to CD or other device.   

I ran through the install process again and ubuntu was able to see the 11.04 install but would not boot to it.  I have noted the boot script info below as requested in a number of other posts where users are having similar issues.   The live CD boot runs without issue.

Not sure if it helps but here is my hardware info

MB: Gigabyte X58-USB3 rev 1.0
Bios Version: F2
HD: Seagate 320GB Raid 1
Memory: 4gb Mushkin
Drives: LG bluray RW
Video: EVGA GTX 285

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 72bcfe7f-5e0d-43e2-a784-b58b423412c0 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of 
    /dev/mapper/isw_dhgjdgcifb_Volume0 and looks at sector 1 of the same hard 
    drive for core.img. core.img is at this location and uses an embedded 
    config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 72bcfe7f-5e0d-43e2-a784-b58b423412c0 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dhgjdgcifb_Volume01: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dhgjdgcifb_Volume02: _______________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_dhgjdgcifb_Volume05: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   616,751,103   616,749,056  83 Linux
/dev/sda2         616,753,150   625,137,663     8,384,514   5 Extended
/dev/sda5         616,753,152   625,137,663     8,384,512  82 Linux swap / Solaris


Drive: isw_dhgjdgcifb_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_dhgjdgcifb_Volume0: 320.1 GB, 320070619136 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625137928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_dhgjdgcifb_Volume01   *          2,048   616,751,103   616,749,056  83 Linux
/dev/mapper/isw_dhgjdgcifb_Volume02        616,753,150   625,137,663     8,384,514   5 Extended
/dev/mapper/isw_dhgjdgcifb_Volume05        616,753,152   625,137,663     8,384,512  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_dhgjdgcifb_Volume0p1 72bcfe7f-5e0d-43e2-a784-b58b423412c0   ext4       
/dev/mapper/isw_dhgjdgcifb_Volume0p5 b4534995-3ef7-44c5-a2cc-b945f1667e42   swap       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_dhgjdgcifb_Volume0
isw_dhgjdgcifb_Volume0p1
isw_dhgjdgcifb_Volume0p5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda5


Unknown BootLoader on isw_dhgjdgcifb_Volume01


Unknown BootLoader on isw_dhgjdgcifb_Volume02


Unknown BootLoader on isw_dhgjdgcifb_Volume05



=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/mapper/isw_dhgjdgcifb_Volume01: No such file or directory
hexdump: /dev/mapper/isw_dhgjdgcifb_Volume01: No such file or directory
hexdump: /dev/mapper/isw_dhgjdgcifb_Volume02: No such file or directory
hexdump: /dev/mapper/isw_dhgjdgcifb_Volume02: No such file or directory
hexdump: /dev/mapper/isw_dhgjdgcifb_Volume05: No such file or directory
hexdump: /dev/mapper/isw_dhgjdgcifb_Volume05: No such file or directory


```

---

### Post by rabideau on 2011-05-24
Same for me when attempting 11.04 64 bit...

---

### Post by wolfsburg18 on 2011-05-24
I have tested a number of other things and still can't get this system to boot with 11.04 but I have no issues with 10 LTS.   I have also downloaded and burned multiple copies of 11 without any success.   

Hedge hog if you read this your insight would be appreciated.

---

### Post by rabideau on 2011-05-24
My problem was 'simply' that I had left an sd card in my laptop and the install failure was simply the system attempting to write to that device rather than my HDD. :(

---

### Post by Hedgehog1 on 2011-05-25
> **wolfsburg18 said:**
> **Hedge hog** if you read this your insight would be appreciated.

[SIZE="3"]OH NO!!!!! They are asking for me by name!!!![/SIZE]

Let me study the boot info script and see what I can see.

:D

**EDIT:** First - you need to understand that ***all hedgehogs*** prefer hardware raid (ask the next one you see) because the are much cheaper (Really) when you add in the down time that software raid, fake raid and mother board based raids create.

I mean something like this: [TowerRAID 5-Bay USB 3.0/eSATA Hardware RAID 5]("http://www.amazon.com/Sans-Digital-TowerRAID-Hardware-TR5UT-BP/dp/B003YDZE0Q/ref=sr_1_9?s=electronics&ie=UTF8&qid=1306297200&sr=1-9"). It present itself though an esata cable as one big, fast drive.

With that said - I have seen a number of folks with software raids that work fine on earlier kernels but they get the 'mount: unknown filesystem type' errors and cannot understand the raid drive(s) anymore from Natty.

Here is my suggestion (and it is untested!) - the Alternate install CD does offer RAID support.  It ***might*** see your raid drives.  It is worth a download to see.

I am going to ask another forum member who knows software raid really well to look at you post and see of he has any in sites.

***The Hedge***

:KS

---

### Post by ronparent on 2011-05-25
> ========================= "ls -R /dev/mapper/" output: 

/dev/mapper:
control
isw_dhgjdgcifb_Volume0
isw_dhgjdgcifb_Volume0p1
isw_dhgjdgcifb_Volume0p5

This may be the problem. The meta data on the disk seems to have been written with a version of gparted that appended a partition number with 'p' preceding it. You will note that in the result.txt that this naming convention is not used elsewhere! Since the names in /dev/mapper are the handles (symbolic links) used to mount the file system if partition names without a 'p' are used no file systems will be found.  If this is the case the alternate cd will also fail. 

Your best bet may be to 1) turn off the raid in the raid bios 2) erase the meta data from a live cd (sudo dmraid -rE) 3) turn the raid back on in bios 4) do the install over again. Of course everything on the drives will be erased and you will have to start all over again - but at least the names for the symbolic links will be consistent.

Just for your information, if you do erase the meta data, you will end up with a new name for your array. By the isw naming convention the name ending up with .._Volume0 will be the name for your two disk array. This is where your boot loader will be installed. Grub itself will be installed to whichever partition your system is installed to (probably .._Volume01). Natty has to my experience been consistent in installing correctly to a fakeraid - but that is based on a sample of one.

Linux allows you three ways to set up a raid: a harware raid, a linux software raid and a windows/linux 'fakeRAID'. I won't argue the relative merits of any of these except to say each has its place. If you wish to use a raid shared between windows and linux that would explicitly rule out only the linux software raid. I'll only say that if you are unfamiliar with the particulars of your choice attempting to set up a raid will be an education. But, that may be the only compelling reason to use a raid in a home system.:)

I don't know if any of this will be useful to you, but, do post if you still have questions.

---

### Post by ronparent on 2011-05-25
I have another thought. If you haven't done anything yet, lets try a quick experiment. Boot to the natty live cd and open a terminal.

At the prompt write: 
```
ls /dev/mapper
```
If there is the output shown in the Results.txt write:
```
sudo mount isw_dhgjdgcifb_Volume0p1 /mnt
```
Use **ls /mnt** to verify that your install is mounted.
If it is then reinstall grub with:
```
sudo grub-install --root-directory=/mnt/ isw_dhgjdgcifb_Volume0
```
Now check to see if the system can be booted normally.

Although the Results.txt in general show the wrong designations for your symbolic links the entries in /etc/fstab agree with the designations in /dev/mapper for those links. If grub is installed correctly your system should be bootable. If not there are other factors innvolved that may have nothing to do with raid.

---

### Post by wolfsburg18 on 2011-05-27
Ronparent

thanks for your input here is the output, unfortunately that did not resolve the issue.  

```

ubuntu@ubuntu:~$ ls /dev/mapper
control                 isw_dhgjdgcifb_Volume0p1
isw_dhgjdgcifb_Volume0  isw_dhgjdgcifb_Volume0p5
ubuntu@ubuntu:~$ sudo mount isw_dhgjdgcifb_Volume0p1 /mnt
mount: special device isw_dhgjdgcifb_Volume0p1 does not exist
ubuntu@ubuntu:~$ ls /mnt
ubuntu@ubuntu:~$ sudo mount isw_dhgjdgcifb_Volume0p5 /mnt
mount: special device isw_dhgjdgcifb_Volume0p5 does not exist


```

I am not worried about removing the meta data from the disks if that resolves the issue as all the data is backed up.  The only thing I would need to do is reload my applications which is easy enough.

Let me know if you have any other insights or I will go ahead and try the meta data method with 11, if that fails I will install 10 LTS

---

### Post by ronparent on 2011-05-27
It looks like the developers have again left us with an unresolved fakeraid mess to deal with. You are probably best to reinstall from scratch after removing the meta data after all. 

Now for my rant. I hate the term fakeraid. You could say the same of any software raid. The terms seems to be indicative of how the Linux views it as a simple minded windows artitfact. It does serve the purpose of enabling sharing of an array data between windows and Linux and in my experience has never given me any implementation problems within windows. Within Ubuntu it is another story. The problems evolve and change with each release. Unless you are determined to share raid data between windows and Ubuntu I would be inclined to state that you might as well chuck it for a software raid except that software raids seem to carry their own implementation problems. In any event if what you are looking for is an education in the use of raids in Ubuntu that is what you will get. Of course in windows you need learn nothing!

But that said I'll be happy to watch your progress and help wherever possible.

---

