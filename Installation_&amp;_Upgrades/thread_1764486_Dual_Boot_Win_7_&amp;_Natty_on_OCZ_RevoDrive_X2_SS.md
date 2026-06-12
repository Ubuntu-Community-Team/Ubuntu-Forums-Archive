---
title: "Dual Boot Win 7 &amp; Natty on OCZ RevoDrive X2 SSD?"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by enkrypt3d on 2011-05-21
I setup win 7 x64 without issues on my new OCZ RevoDrive X2 240GB and left about 80GB for Kubuntu Natty - Ok so got everything setup right in windows and booted onto my natty cd and created a swap slice and / slice... kubuntu recognized my drive and installed everything but after its done installing and reboots, it goes straight into grub recovery and I'm unable to use any of the commands... it says something about unable to mount and then a bunch of characters 234a-628b-f536 etc... Tried every command that I can think of while in grub recovery and nothing worked...

So after reinstalling natty again and making sure the boot drive is setup it still gives me the same results. I ended up having to reinstall windows 7 b/c it blew away the MBR. (Even in windows setup the fix startup didn't find anything wrong even after installing the ssd drivers)...... HELP! Thx

---

### Post by ajgreeny on 2011-05-21
Are you sure you set  / as the mountpoint for the / (root) partition you had already made, or it sounds as if you made it before you did the installation.

If you still have that kubuntu install on the drive, from the live CD can you click on the Boot-info-script in my signature, follow the instructions and copy back the RESULTS.txt file here in code tags (the # above the text entry box)

---

### Post by enkrypt3d on 2011-05-21
> **ajgreeny said:**
> Are you sure you set  / as the mountpoint for the / (root) partition you had already made, or it sounds as if you made it before you did the installation.

If you still have that kubuntu install on the drive, from the live CD can you click on the Boot-info-script in my signature, follow the instructions and copy back the RESULTS.txt file here in code tags (the # above the text entry box)

I created a / slice and swap slice and theres a drop down box at the bottom when you're creating the partitions... Its defaulted to /dev/sda which isn't right for the SSD so I set that to /dev/sil_aassd (dont remember the exact spelling) and that didnt work...

I can boot into the live cd without installing kubuntu and run the boot script to get your results right? What does the script do? Thx

[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

"Corrupted partition structure - "ls" returns only "(hd0)"

This is what I was seeing when kubuntu was done installing... FYI not sure if that helps!

---

### Post by enkrypt3d on 2011-05-21
Ok tried about 5 times to get your boot info script results ran and copied to a usb drive from the live cd but it (the entire system while running off the cd) is so painfully slow, and even after copying the results.txt to the usb drive, it wasn't there when I went to look at it in windows ....... I guess I can just use kubuntu thats already installed on my old hard drive instead. Oh well!

---

### Post by ajgreeny on 2011-05-22
I have no idea about your **/dev/sil_aassd,** which sounds like gobbledegook, and will certainly be seen as such by grub, hence your problem, I think.

The boot-info-script really is needed, so try again, if possible.  All it does is read all the files it finds related to booting the computer, and copies them all to a long text file called RESULTS.txt.

---

### Post by enkrypt3d on 2011-05-22
Here it is I was able to get the boot script to run here is the results:

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/mapper/sil_acadajaaddfg.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sil_acadajaaddfg1: _____________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sil_acadajaaddfg2: _____________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   468,914,175   468,707,328   7 NTFS / exFAT / HPFS

/dev/sda2 ends after the last sector of /dev/sda

Drive: sil_acadajaaddfg _____________________________________________________________________

Disk /dev/mapper/sil_acadajaaddfg: 240.1 GB, 240085630976 bytes
255 heads, 63 sectors/track, 29188 cylinders, total 468917248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/sil_acadajaaddfg1   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/sil_acadajaaddfg2            206,848   468,914,175   468,707,328   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/sil_acadajaaddfg1 3C4EE54D4EE5008E                       ntfs       System Reserved
/dev/mapper/sil_acadajaaddfg2 329AE5FE9AE5BF0B                       ntfs       
/dev/sda                                                silicon_medley_raid_member 
/dev/sdb                                                silicon_medley_raid_member 
/dev/sdc                                                silicon_medley_raid_member 
/dev/sdd                                                silicon_medley_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
sil_acadajaaddfg
sil_acadajaaddfg1
sil_acadajaaddfg2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2



========= Devices which don't seem to have a corresponding hard drive: =========

sde sdf 

=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
```

One thing I noticed during the install of kubuntu, the drop down that has the different partitions listed isn't wide enough to show me what the number is at the end of each partition to set the boot volume. So its hard to tell which one I'm setting it to. I'm guessing it would be the 3rd or 4th option since windows is on 1 & 2...

---

### Post by enkrypt3d on 2011-05-22
So I tried to reinstall and created swap and / and that created a /dev/mapper/sil_acadajaaddfg6 so I set the drop down at the bottom to install the boot loader onto /dev/mapper/sil_acadajaaddfg6 and rebooted and it went right back into grub recovery........ argg

So now Im on a live CD and this is the output of fdisk -l

root@ubuntu:~# fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff6c00e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       18990   152433664    7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/dm-0: 240.1 GB, 240085630976 bytes
255 heads, 63 sectors/track, 29188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 262144 bytes
Disk identifier: 0xff6c00e0

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/dm-0p2              13       18990   152433664    7  HPFS/NTFS

Disk /dev/dm-1: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(335, 10, 2) logical=(120527, 49, 53)
Partition 1 has different physical/logical endings:
     phys=(327, 84, 13) logical=(234813, 237, 34)
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/dm-1p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(119380, 132, 62)
Partition 2 has different physical/logical endings:
     phys=(256, 101, 36) logical=(153270, 41, 37)
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/dm-1p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(364, 116, 50) logical=(113201, 29, 24)
Partition 3 has different physical/logical endings:
     phys=(372, 65, 44) logical=(147074, 114, 59)
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/dm-1p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 101, 51) logical=(177063, 118, 26)
Partition 4 has different physical/logical endings:
     phys=(269, 114, 52) logical=(177066, 225, 63)
Partition 4 does not end on cylinder boundary.
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 156.1 GB, 156092071936 bytes
255 heads, 63 sectors/track, 18977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/dm-2p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/dm-2p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/dm-2p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order
root@ubuntu:~#

---

### Post by enkrypt3d on 2011-05-24
Anyone have any ideas? Please? No one has tried to install kubuntu on the OCZ RevoDrive x2 SSD? :confused:

---

### Post by enkrypt3d on 2011-05-26
[http://pileborg.org/blog5.php/2011/05/02/install-ununtu-11-04-on](http://pileborg.org/blog5.php/2011/05/02/install-ununtu-11-04-on)

Found this but haven't tried it yet....

---

### Post by enkrypt3d on 2011-05-29
Has anyone tried this?? no one is using Ubuntu on a raid'd SSD drive?

---

### Post by oldfred on 2011-05-29
It may be possible no one has. 

You use RAID to speed things up, primarily for servers with many users. A few compiling large apps might see some advantage to RAID on a desktop, but you cannot type faster nor download from the Internet faster. Those who want to compile faster now do use SSDs to speed up those kinds of applications and booting, loading apps, etc.

---

### Post by enkrypt3d on 2011-05-29
> **oldfred said:**
> It may be possible no one has. 

You use RAID to speed things up, primarily for servers with many users. A few compiling large apps might see some advantage to RAID on a desktop, but you cannot type faster nor download from the Internet faster. Those who want to compile faster now do use SSDs to speed up those kinds of applications and booting, loading apps, etc.

:lolflag: really?

I know what SSD's are used for - I bought one b/c I wanted it, not b/c I "needed" it... And thats not to say everyone else hasn't done the same. 

Its like asking someone why did they buy a BMW when they could have bought a civic? :confused: They dont NEED the luxury right?

See my point? Just b/c you don't need it doesn't mean you don't WANT it! :)

So back on topic, I'm sure there are plenty of ppl who have gotten it to work. Look at that link I posted. That means at least ONE person (other than me) has done it... just not on these boards.

---

### Post by oldfred on 2011-05-29
I did not realize RAID was built into the drive.

Tested with Ubuntu 11.04 & Arch
[http://openbenchmarking.org/s/RevoDrive%2050GB](http://openbenchmarking.org/s/RevoDrive%2050GB)

---

### Post by enkrypt3d on 2011-05-30
> **oldfred said:**
> I did not realize RAID was built into the drive.

Tested with Ubuntu 11.04 & Arch
[http://openbenchmarking.org/s/RevoDrive%2050GB](http://openbenchmarking.org/s/RevoDrive%2050GB)

okay thanks....... haha :-?:-k:???:

---

### Post by ronparent on 2011-05-31
Natty installation to a fakeraid can be flawless but can also be a total pain. First off, the results.txt shows no sign of any Linux installation!? I have very little idea where to begin to disentangle this situation. Also the reference you give may be for a software raid as opposed to the 'fakeraid' you are trying to install to. They are very similar except that with a faleraid no portion of the installation would be made to a component disk which is part of the raid (sda, sdb, etc). I see that in your case you have a raid of four component disks (sda, sdb, sdc, sdd). What level raid is this ( raid 0, 1, 5, S, etc). 

Incidentally the fakeraid is the only option if you intend to share partions between windows and linux. 
 
In my own system with one ssd with Win7 the gparted has always shown the ssd as unallocated space. You would need to check that in a live cd using gparted to examine your drives. Unless you see your raid as /dev/mapper/sil_acadajaaddfg you have little chance of installing to the raid and will probably incapacitate your Win7 as well. 

Since I never intended to use my ssd except for win7 I frankly never studied what had to be done to make it partitionable with gparted. I believe it requires 'aligning' it. This of course would also wipe out the win7 and require its reinstallation. 

Once you have attained a /dev/mapper/sil_acadajaaddfg array you can see and partition with gparted you could install to the array. This could entail much more work than you intended to reach that point. Are you open to other arrangements? Let us know where you are trying to head.

---

### Post by ronparent on 2011-05-31
Taking a hint from oldfred I researched the revodrive on the net. I frankly doubt that it can be accessed with any Ubuntu based distro unless by some chance recognized by dmraid. In the absence of that it is unlikely you can install side by side with windows.
Edit: dmraid does recognize the partitions win7 is written to (see Results.txt). Those partitions are probably mountable. If so then it would appear that the drives are usable with an Ubuntu distro. The problem may be partitioning with the installer or gparted. If the partitions you intend to install to (ie ext4 and swap) can be precreated with a live cd then you could install to those partitions with the custom install option. In my experience with Natty this does not insure the install is bootable but in my case it has been fixable with a grub reinstall. If you end up with an initramfs prompt on boot it is likely that dmraid was for some reason not installed properly. That is fixable with a chroot dmraid install to your ubuntu partition. In any case your install to the raid has to be seeable for any fix. That does not appear to be the case now.

---

### Post by KaMZaTa on 2011-06-17
I've find [this "solution"]("http://www.ocztechnologyforum.com/forum/showthread.php?76486-Revodrive-Ubuntu-10.04-install-issues&p=546024&viewfull=1#post546024"): I have starting grub from external USB pen (very very slow) but now I don't understand how to move /boot directory and bootloader inside my REVODRIVE X2.

How can I do?

---

