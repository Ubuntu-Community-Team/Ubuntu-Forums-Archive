---
title: "Installing on RAID 0+1 with Windows 7"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by Belbear on 2010-07-18
Hi,

I'm trying to install Ubuntu 10.04 LTS on my new system.
Until now I did only boot Ubuntu from CD

The Ubuntu installer does see two RAID0+1 drives
/dev/mapper/isw_bcihehfidi_raid0+1-0
/dev/mapper/isw_bcihehfidi_raid0+1-1
There is nothing in the columns Type, Mount point etc., buttons Add, Change and Delete are disabled
I don't dare to create new partitioning tables here, I don't want to lose my Win7 setup. 

It have a quad-1TB disk RAID 0+1 setup, with Windows 7 Ultimate 64-bit already installed.
According to Windows the partitioning is as follows:
"system reserved" partition of 75Mb
Windows C drive 254.6GB
Unpartitioned space ca. 60GB  (Ubuntu should go in here)
Windows D drive 1.5TB

Ubuntu can see all three Windows partitions and access their content.

How should I proceed to install Ubuntu in the unpartitioned space, of course without having to re-install Windows and with the option to choose between Ubuntu and Windows at boot time?

I found Darko's boot info script and ran it. Here's the results.txt:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/mapper/isw_bcihehfidi_raid0+1

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

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bcihehfidi_raid0+11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

isw_bcihehfidi_raid0+12: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

isw_bcihehfidi_raid0+13: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_bcihehfidi_raid0+15: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, 
                       isw_bcihehfidi_raid0+15 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2    *        206,848   534,063,103   533,856,256   7 HPFS/NTFS
/dev/sda3         598,976,512 3,907,037,183 3,308,060,672   f W95 Ext d (LBA)
Invalid MBR Signature found
/dev/sda5     ?   834,098,148   894,227,747    60,129,600  78 Unknown
/dev/sda6     ? 1,428,926,233 1,485,267,292    56,341,060  c1 DRDOS/sec (FAT-12)

/dev/sda3 ends after the last sector of /dev/sda

Drive: isw_bcihehfidi_raid0+1 ___________________ _____________________________________________________

Disk /dev/mapper/isw_bcihehfidi_raid0+1: 2000.4 GB, 2000404348928 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907039744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_bcihehfidi_raid0+11              2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/isw_bcihehfidi_raid0+12   *        206,848   534,063,103   533,856,256   7 HPFS/NTFS
/dev/mapper/isw_bcihehfidi_raid0+13        598,976,512 3,907,037,183 3,308,060,672   f W95 Ext d (LBA)
/dev/mapper/isw_bcihehfidi_raid0+15        598,978,560 3,907,037,183 3,308,058,624   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_bcihehfidi_raid0+11 C282EDD582EDCDCB                       ntfs       System Reserved               
/dev/mapper/isw_bcihehfidi_raid0+12 3AC4289AC4285B01                       ntfs       XP 64                         
/dev/mapper/isw_bcihehfidi_raid0+15 8ABEDA9CBEDA7FDD                       ntfs       Data                          
/dev/mapper/isw_bcihehfidi_raid0+1: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc                                                isw_raid_member                               
/dev/sdd                                                isw_raid_member                               
error: /dev/mapper/isw_bcihehfidi_raid0+13: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_bcihehfidi_raid0+1
isw_bcihehfidi_raid0+1-0
isw_bcihehfidi_raid0+11
isw_bcihehfidi_raid0+1-1
isw_bcihehfidi_raid0+12
isw_bcihehfidi_raid0+15

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/isw_bcihehfidi_raid0+12 /media/XP 64             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/mapper/isw_bcihehfidi_raid0+15 /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/mapper/isw_bcihehfidi_raid0+11 /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on isw_bcihehfidi_raid0+13



=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh sdi 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/mapper/isw_bcihehfidi_raid0+13: No such file or directory
hexdump: /dev/mapper/isw_bcihehfidi_raid0+13: No such file or directory

```

AFAIK the partition I should use is called /dev/mapper/isw_bcihehfidi_raid0+13 but how can I install Ubuntu into it if the installer does not list it?

---

### Post by ronparent on 2010-07-18
The first hurdle is to determine that dmraid will work with your chipset on raid 0+1. The output of dmraid -l is 'Intel Software RAID (0,1,5,01)'. I frankly don't know how to interpret this. If raid 0+1 is equivalent to '01' then you are supported.

The next hurdle is that gparted under 10.04 may not support partitioning your raid. The workaround is to use gparted in an earlier release to create a formatted target partition for you to install to. I did this and the install went smoothly. Many other have reported that the install fails if they try to partition during the install. Note that if you use a live cd for 9.04 and prior you will have to install dmraid (apt-get install dmraid) to your live cd session to enable gparted to see and work on the raid partitions.

The final hurdle is that you have to select the advanced box in step 8 of the 'select own partition' install process. That box will open a window that will allow you to install the grub2 bootloader to the raid. That is the right place to install it if you intend to boot from the raid. Sometimes that selection will try to install to sda anyhow and that will fail. It is fixable. You will either have to use another installed bootloader to open a terminal in your installed 10.04 or chroot to get to it from a live cd session terminal. In the terminal you would have to 'sudo install-grub /dev/mapper/isw_bcihehfidi_raid0+1' to write the grub 2 MBR.

This is a broad outline of what you need to do. If you need explicit instructions, post here. Good luck. (I have just gotten the call for a fresh blackberry pie - will have to get back to you later).:p

---

### Post by Belbear on 2010-07-18
Thanx for the quick reply.

> **ronparent said:**
> The first hurdle is to determine that dmraid will work with your chipset on raid 0+1. The output of dmraid -l is 'Intel Software RAID (0,1,5,01)'. I frankly don't know how to interpret this. If raid 0+1 is equivalent to '01' then you are supported.

My RAID is hardware "Intel ICH8R/ICH9R/ICH10R/DO SATA RAID controller"
dmraid -l outputs this:

ubuntu@ubuntu:~$ dmraid -l
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,5,01)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs

> **ronparent said:**
> 
The next hurdle is that gparted under 10.04 may not support partitioning your raid.

gparted only sees four devices /dev/sda through /dev/sdd
I guess these are the four physical HDD's I have. Because of the RAID0+1 they are seen as unpartitioned

> **ronparent said:**
> 
  The workaround is to use gparted in an earlier release to create a formatted target partition for you to install to. I did this and the install went smoothly. Many other have reported that the install fails if they try to partition during the install. Note that if you use a live cd for 9.04 and prior you will have to install dmraid (apt-get install dmraid) to your live cd session to enable gparted to see and work on the raid partitions.

This is a broad outline of what you need to do. If you need explicit instructions, post here. Good luck. (I have just gotten the call for a fresh blackberry pie - will have to get back to you later).:p

dmraid seems to be able to see the partitions I need using the isw, but again I don't like to experiment with this "dangerous" software other than the "display" options and this damned demo boot doesn't retain anything :(

Output of "sudo dmraid -s -s isw_bcihehfidi_raid0+1" is:
*** Group superset isw_bcihehfidi
--> Active Superset
name   : isw_bcihehfidi_raid0+1
size   : 3907039744
stride : 128
type   : raid01
status : ok
subsets: 2
devs   : 4
spares : 0
--> Active Subset
name   : isw_bcihehfidi_raid0+1-0
size   : 1953519872
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
--> Active Subset
name   : isw_bcihehfidi_raid0+1-1
size   : 1953519872
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0


I have only limited experience with *nix OS
Is it possible to get a working version of gparted without the need to get an entirely older version of ubuntu?
Or do I need to get a totally different version of *ubuntu? There are so many and I don't have a clue which one is best for me. This one looks very okay except for the fact that its installer can't see the partition space I have reserved for it.

---

### Post by ratcheer on 2010-07-18
> **Belbear said:**
> 
Is it possible to get a working version of gparted without the need to get an entirely older version of ubuntu?

Yes, just use a Live CD.

Tim

---

### Post by v1ad on 2010-07-18
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by ronparent on 2010-07-18
That's correct, use a live cd. For anything earlier than 9.10, you will have to install dmraid and activate the raid for gparted to see the raid and raid partitions. That live cd install of dmraid is to a virtual drive and will last only until the live cd session is ended. As long as you stick to the dmraid commands to display the raid drive status there is no likelihood of damaging your existing partitions. Once gparted can see the raid you should have no problem creating the raid partitions. 

I don't believe the problem is with gparted incidently because the same version is used in earlier releases and works fine.

ps  Except for giving you a better idea of fakeraid behavior, I don't believe that reference has yet been modified to deal with installing to a fakeraid in 10.04. That can prove easier than in earlier version as long as you remain aware of the new kinks involved.

---

### Post by v1ad on 2010-07-18
u will have to install grub separately. at least i had 2.

---

### Post by ronparent on 2010-07-18
vlad may be correct on that last point. I did have my most recent install of mint 9 work fine, so I don't know if that has yet been fixed for ubuntu 10.04.

---

### Post by Belbear on 2010-07-19
-should be deleted but I cannot -

---

### Post by Belbear on 2010-07-19
> **ronparent said:**
> That's correct, use a live cd. For anything earlier than 9.10,   
I don't believe the problem is with gparted incidently because the same version is used in earlier releases and works fine.

ps Except for giving you a better idea of fakeraid behavior, I don't believe that reference has yet been modified to deal with installing to a fakeraid in 10.04. That can prove easier than in earlier version as long as you remain aware of the new kinks involved.

I finally found a 9.10 liveCD version (had to use a torrent from an unknown source, the main ubuntu site doesn't offer back-issues :(), and booted from it.

It's not nearly as sleek as the 10.04 (which was love at first boot) and it could not get my display driver right out of the box (as 10.04 did very well, including the second screen on HDMI output) 
My hardware is of the newest generation, so I really don't want to install this or any older version.

The 9.10 installer had exactly the same issue as on 10.04: Showing only the two RAID subsets: 
isw_bcihehfidi_raid0+1-0 and isw_bcihehfidi_raid0+1-1, without any partition info.
Remark the "-" before the last digit. These are obviously not partitions!

However, gparted did much better on 9.10: It can actually see all my partitions and I could install an ext2 filesystem in the unallocated space it was intended for.

Apart from the four physical devices /dev/sda though /dev/sdd, gparted also shows the
/dev/mapper/isw_bcihehfidi_raid0+1
On this device, gparted now sees the following partitions: (Remark there is no '-' before the last digit now)
isw_bcihehfidi_raid0+11 = NTFS sytem reserved (windows 7 boot partition)
isw_bcihehfidi_raid0+12 = NTFS windows 7 'C' drive
isw_bcihehfidi_raid0+14 = ext2 partition intended for Linux
isw_bcihehfidi_raid0+13 = extended partition, holding the data partition isw_bcihehfidi_raid0+15 = NTFS data partition (windows 'D' drive)

However, without the installer being able to see this partition, I cannot install anything on it. 

So now the problem is: How can I install Ubuntu 10.04 or later in this partition, and how can I install this grub bootmanager (of course without losing my Windows)

Has anyone here ever used an actual RAID 0+1 setup? I only see references to raid0 or RAID1 but this is a combination of both (a mirrored striped set of four HDD's)

---

### Post by Belbear on 2010-07-19
Sorry for posting my reply twice, it is caused by this forum software: When submitting my long, tedious reply (it took a while to compose) it forced me to log in again although I was already logged in!
After logging in again, I ended up with an empty screen. 
Assuming the post was not submitted, I tried again with a copy-pasted reply

---

### Post by ronparent on 2010-07-19
Once you have the preformed target partition simply select the third option on your screen in which you choose where to install, in which you are basically selecting manually partitioning. For this case there will be a  next screen in which you will see your raid target partition and be able to select it and elect to install without partitioning it. In screen 8, of course, you will have to select the root raid drive to install the grub bootloader to (if you intend to boot from the raid in bios). The install should proceed without a glitch unless you hit the third hurdle in which case you will be forced to install the grub bootloader to the raid manually. I don't know what to expect at that point since I had to fix it for an early release of 10.04 but not for Mint 9? Once installed and bootable to, everything should work fine. The grub should boot fine to windows 7. If not we can fix it easily enough.

Since I've not yet seen any other reference to booting to a raid 0+1 you are probably a pioneer - isn't it exciting? I don't expect to see any other glitches however. Since the target raid partition will require no further modifications your win 7 installation should remain safely unaffected. Incidentally, you could have chosen to pre-format that target in ext3 or ext4 and either would have worked fine also. Good luck - I think you are headed right.

---

### Post by Belbear on 2010-07-19
> **ronparent said:**
> Once you have the preformed target partition simply select the third option on your screen in which you choose where to install, in which you are basically selecting manually partitioning. For this case there will be a  next screen in which you will see your raid target partition and be able to select it and elect to install without partitioning it. In screen 8, of course, you will have to select the root raid drive to install the grub bootloader to (if you intend to boot from the raid in bios). 


Well, that's the whole problem:
I can't get past step 4 in the installer (the first step where you shouls select a partition)
I see no option where I can choose where to install.
The only two devices I see listed have NO partition info whatsoever and the devices that should hold partition info (like the /dev/mapper/isw_bcihehfidi_raid0+1 that the gparted in 9.10 could access) is not listed in the installer. The (Windows)  partitions are accessible for Ubuntu, I can even mount them and access their content, just the installer does not see any partition so i'm stuck at step 4, even with the older version 9.10

I need help from someone who can show me the commands to make the partition table visible for the installer. If not i'm gonna have to find another Linux distro that works for me  

> **ronparent said:**
> Since I've not yet seen any other reference to booting to a raid 0+1 you are probably a pioneer - isn't it exciting? I don't expect to see any other glitches however. Since the target raid partition will require no further modifications your win 7 installation should remain safely unaffected. Incidentally, you could have chosen to pre-format that target in ext3 or ext4 and either would have worked fine also. Good luck - I think you are headed right.

Exciting indeed, but that doesn't help me if it doesn't work.

I don't know what the difference is between ext2 and the higher versions, (my previous linux experience was in the mid-1990's and included a lecture from Mr Linus Torvalds himself) but as long it's still empty I can always run the 9.10 gparted again. I didn't install a linux swap partition because it was one primary partition too many (appears to be limited to four). I guess there's little need for it anyway on a system with 8 gigs of RAM...

One more thing I could try is the 64-bit version of Ubuntu, bust just as with Windows I expect more troubles with drivers and apps on that one, so I'd like to stick to 32-bit

After all the very reason for installing Linux is to be able to compile open-source projects like VLC player in a more reliable fashion than on a Windows OS. And the real VLC gurus use Ubuntu, so...

---

### Post by ronparent on 2010-07-19
Look again at step 4. There are three options in the menu: 1) install to an entire drive 2) split the drive between ubuntu and another system 3) manually select where to install. Pick the third option. That should bring up a step 5 screen in which all your raid partitions are listed. Pick your target and the change box for it in the botom of the screen. In the window that comes up, pick '/' as the mount point, opt to install w/o formatting, and close that window. Now hit continue.

I see little differentiation between the 32 bit and 64 bit version unless you have 4 or more gig of RAM, then you would get better ram utilization with the 64 bit version. I operate the 64 bit on raid 0 and have no reservation.

You should have created The target in an extended partition if you are up against the four primary partition limit. Then you could create an unlimited number of linux partitions for yourself within the extended including the swap - Ubuntu doesn't require a primary partition installation. It is not wise to eliminate the swap.

---

### Post by Belbear on 2010-07-19
> **ronparent said:**
> Look again at step 4. There are three options in the menu: 1) install to an entire drive 2) split the drive between ubuntu and another system 3) manually select where to install. Pick the third option. That should bring up a step 5 screen in which all your raid partitions are listed. Pick your target and the change box for it in the botom of the screen. In the window that comes up, pick '/' as the mount point, opt to install w/o formatting, and close that window. Now hit continue.

I'm sorry, but all the options you mention are simply not there on the step4 panel. Looks like they appear only when an existing partition table is detected. :confused: Would send you a screenshot but I'm stuck with a demo run that's really out-of-the-box at each boot.
The install options you mention are indeed there when I accidentally left my USB HDD plugged in (then I see the partitioning of that USB drive) but it's not meant to be installed there.

All I see are the two useless devices mentioned earlier, two buttons, one saying "new partition table', another saying "revert" and three disabled buttons"add"-"change"-"delete". Apart from the quit-back-forward buttons and "forward" doesn't get anywhere. Clicking "new partitioning table" warns me that everything on the entire device will get erased, :o so I quickly bailed out of that.

I really need a method to let the installer see the partition table on that device isw_bcihehfidi_raid0+1 (without the -0 or -1 suffix!), then and only then can I continue. Looks like the built-in device filtering is wrong, I need a way to see ALL devices in /dev/mapper. If it's hard-coded, someone will need to compile one for me.

> **ronparent said:**
> 
I see little differentiation between the 32 bit and 64 bit version unless you have 4 or more gig of RAM, then you would get better ram utilization with the 64 bit version. I operate the 64 bit on raid 0 and have no reservation. 
Ok, I might consider the 64-bit version then. But I don't really intend to need all that RAM, unless you can point me to a pro grade open-source HD-video editing software for Linux that can match something like Adobe Premiere...;) 

> **ronparent said:**
> 
You should have created The target in an extended partition if you are up against the four primary partition limit. Then you could create an unlimited number of linux partitions for yourself within the extended including the swap - Ubuntu doesn't require a primary partition installation. It is not wise to eliminate the swap.
Well, that would require some more complicated repartitioning, as the entire extended partition is taken up by the Windows data partition. But it can be done, on condition I can get the installer to see the partition table in the first place.:cry:

---

### Post by Belbear on 2010-07-19
Actually things even got worse. Since I created that ext2 partition with the version 9.10 gparted, the ubuntu 10.04 livecd no longer mounts my Windows partitions, they are no longer seen in the device list. :cry:

Fortunately Windows still boots up...

---

### Post by ronparent on 2010-07-19
Below is a screen shot of step 4 of 7. You will note that I selected 'Specify partitions manually'

[http://ubuntuforums.org/attachment.php?attachmentid=163944&stc=1&d=1279573831](http://ubuntuforums.org/attachment.php?attachmentid=163944&stc=1&d=1279573831)

When you hit forward there will be some appreciable delay while the drives are scanned to produce the next screen (not likely more than five minutes). 

[http://ubuntuforums.org/attachment.php?attachmentid=163946&stc=1&d=1279573831](http://ubuntuforums.org/attachment.php?attachmentid=163946&stc=1&d=1279573831)

The next screen is step 5 of 8. You will click on the 'change' button after selecting your target partition if the process proceeds to that screen. The change button box looks as follows:

[http://ubuntuforums.org/attachment.php?attachmentid=163945&stc=1&d=1279573831](http://ubuntuforums.org/attachment.php?attachmentid=163945&stc=1&d=1279573831)

In this screen you will use the first downarrow to select the file format you have already formatted your target to. Do not check mark the 'Format the partition' box. And select the mount point '/' with the down arrow. 

You should now be able to proceed to step 8 of 8 without further problem. If step 5 never materializes then we have a problem I wouldn't know how to deal with. If in step 8 you have selected your array for the grub bootloader and you get a fatal error, we can deal with it. I hope this gives you enough to proceed with.

---

### Post by Belbear on 2010-07-20
Dear Ronparent,

I understand perfectly what you want me to do, but yet i'm totally screwed with this setup.
The only two devices listed are not the ones with the partition table, as you can see on this screenshot

So I cannot continue beyond this point unless someone comes up with a fix.

The content of my /dev/mapper is:
ubuntu@ubuntu:/dev/mapper$ ls -al
total 0
drwxr-xr-x  2 root root     200 2010-07-20 13:08 .
drwxr-xr-x 17 root root    4160 2010-07-20 11:52 ..
crw-rw----  1 root root  10, 59 2010-07-20 13:09 control
brw-rw----  1 root disk 252,  4 2010-07-20 13:09 isw_bcihehfidi_raid0+1
brw-rw----  1 root disk 252,  0 2010-07-20 11:51 isw_bcihehfidi_raid0+1-0
brw-rw----  1 root disk 252,  2 2010-07-20 13:09 isw_bcihehfidi_raid0+11
brw-rw----  1 root disk 252,  3 2010-07-20 11:51 isw_bcihehfidi_raid0+1-1
brw-rw----  1 root disk 252,  7 2010-07-20 13:09 isw_bcihehfidi_raid0+12
brw-rw----  1 root disk 252,  8 2010-07-20 13:09 isw_bcihehfidi_raid0+14
brw-rw----  1 root disk 252,  9 2010-07-20 11:14 isw_bcihehfidi_raid0+15

As you can see, a lot more than what the installer lists. So the installer needs to be fixed.

p.s. I also tried the "alternate CD" edition of ubuntu 10.04. It promised more advanced RAID install options, but its installer ended up with exactly the same two useless -0 and -1 devices. (see second screenshot)

Gonna have to give up on Ubuntu for now, unless someone comes up with a real solution for the incompatibility of the installer with RAID 0+1

---

### Post by ronparent on 2010-07-20
In a terminal type: blkid

This may give us better info on what the -0 and -1 represent.

---

### Post by Belbear on 2010-07-20
> **ronparent said:**
> In a terminal type: blkid

This may give us better info on what the -0 and -1 represent.

Too late now to slow-boot the linux one more time now, but all I know is that this RAID 0+1 appears to be a double-layered system: The master device (ending on 0+1)  contains two subsets that do the mirroring. These are the 0+1-0 and 0+1-1 devices. The actual partitions are ending on 0+11, 0+12 etc...

Probably the installer doesn't understand this double-layered RAID system and thinks that the -0 and -1 devices are containing the actual partitions, while it is in fact the  isw_bcihehfidi_raid0+1 device.
See my  ls /dev/mapper in previous post.

dmraid seems to know how it's working, as I posted earlier:
Output of "sudo dmraid -s -s isw_bcihehfidi_raid0+1" is:
*** Group superset isw_bcihehfidi
--> Active Superset
name   : isw_bcihehfidi_raid0+1
size   : 3907039744
stride : 128
type   : raid01
status : ok
subsets: 2
devs   : 4
spares : 0
--> Active Subset
name   : isw_bcihehfidi_raid0+1-0
size   : 1953519872
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
--> Active Subset
name   : isw_bcihehfidi_raid0+1-1
size   : 1953519872
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0

Find a way to get this the "superset" raid device listed in the installer instead of the "subsets" and i'm sure the partitions will appear.  
Maybe by deactivating the two subset objects, there should be a command for that

---

### Post by Belbear on 2010-07-21
> **ronparent said:**
> In a terminal type: blkid

This may give us better info on what the -0 and -1 represent.

This is all I got:

ubuntu@ubuntu:/dev/mapper$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/sdd: TYPE="isw_raid_member" 

Also got:

ubuntu@ubuntu:/dev/mapper$ sudo blkid -p isw_bcihehfidi_raid0+1
isw_bcihehfidi_raid0+1: PTTYPE="dos" 
ubuntu@ubuntu:/dev/mapper$ sudo blkid -p isw_bcihehfidi_raid0+1-0
isw_bcihehfidi_raid0+1-0: PTTYPE="dos" 
ubuntu@ubuntu:/dev/mapper$ sudo blkid -p isw_bcihehfidi_raid0+1-1
error: isw_bcihehfidi_raid0+1-1: No such file or directory

In this startup the -1 device vanished, I was also not able to mount the windows partitions. I think gparted broke some part of the RAID-1 mirroring when I made that linux partition with the 9.10 version

---

### Post by ronparent on 2010-07-21
At first bite it appears your raid set is supported. The question is whether or not all of the necessary symbolic links have been created (ie.  ls /de/mapper). If the individual partitions do not appear in /dev/mapper then as a practical matter dmraid is not supporting your raid devices as setup in windows. I would guess that that is not the case. It seems more likely at this point that the installer is not picking up on existing symbolic links?? In that case it appears you are right in you original assessment and that would be a bug report on 10.04.

I now see you have a posting #21 as well. I wouldn't worry about the -1 disappearing unless you cannot boot windows! The directory structure doesn't appear on a second 'drive' in the case of a raid 0 and this is likely the case here. Except for creating the partition within 9.10 you haven't yet done anything to modify your raid with dmraid. It does tell us that the capabilities of dmraid do appear different in 10.04 as opposed to 9.10 and those changed capabilities may not allow you to access your raid in 10.04 - also as you originally concluded. I admit that I am stumped and can't think of anything useful or doable that you could do to fix how dmraid is functioning for your case????

---

### Post by Belbear on 2010-07-21
Hi, Ron,

Well, I learned a lot on RAID in the process. I now know that RAID 0+1 is the simplest form of "nested RAID" (see this wiki [http://en.wikipedia.org/wiki/Nested_RAID_levels )]("http://en.wikipedia.org/wiki/Nested_RAID_levels")

Problem for the average cash-strapped student linux-geek seems to be that you need at least four physical HDD's in your system to set up one and many people are using only laptops now...:lolflag:
Apparently, nested RAID (or just RAID-1 mirroring) has never been tested by a developer with ubuntu 10.04. 

I don't know where to file a bug report, you're welcome to issue one. In the meanwhile i'm downloading a fedora distro, just to see what that's gonna do.

But it's all gonna have to wait until end this month, I'm going offline now to pack for a 9-day holiday trip tomorrow.... 

cu later...

---

### Post by ronparent on 2010-07-21
Enjoy your holiday.

Well, it has been a learning experience for me also. The fact you were able to see raid 0+1 partitions in 9.10 to create a target drive does illustrate that there is a problem with functioning of dmraid in the 10.04 environment (and also in the 10.10 development releases). I've already reported the inability to use gparted on raid in 10.04 and 10.10 with no meaningful response from the developers. I'll be happy to report this in launchpad as well. Since they are observing that I am the only one affected by a 10.04/10.10 dmraid bug in those environments I don't expect much response there either. Incidentally, the isw raid 0+1 seem to actually be a raid 1+0 as evidenced by the reported lack of a filesystem on your -1. 

I regret that I don't have the four drives (or otherwise need for them) lying around to explore it further myself. Again have a great holiday.

ps: shall we mark this a unsolvable -- ha ha

---

### Post by ronparent on 2010-07-21
You will probably miss this before you leave for your holiday, but, there may be a way to activate your subsets if they haven't already been activate. Unfortunately  I don't have the raid 0+1 setup to test it on.

In a terminal try 'sudo dmraid -ay /dev/mapper/isw_bcihehfidi_raid0+1-0 /dev/mapper/isw_bcihehfidi_raid0+1-1

Using the above in a live cd prior to running the installer might make the symbolic links for the raid target partition see able in the installer. This comment is applicable for 10.04 and Mint 9.

---

### Post by ronparent on 2010-07-24
I don't know if this will help for the problem with the nested raid, but, I just discovered yesterday of another situation that explains the incompetence of gparted with 10.04. I had posted a bug report etitled "Gparted not usable on fakeraid arrays" ([https://bugs.launchpad.net/bugs/600729](https://bugs.launchpad.net/bugs/600729)). That situation was explainred by Curtis Gedak as follows:


> GParted requires both dmraid and kpartx to properly function with
FAKERAID.  The Ubuntu 10.04 Live CD did not ship with kpartx and this is
why GParted will not automatically detect FAKERAID setups.

The kpartx application is required to create the proper device names
when the dmraid command does not create the proper name.

So the bottom line is that you can skip the workarounds I outlined previously - provided the nested raid can be handled. The solution (I checked -it works) is from a live cd session use Synaptics to install the package 'kpartx' and continue dirctly to the install within the session. You may still have to use the approach I outlined previously (#25) to access the nested partitions. Doing this basically allows the installer to format normally during the install.

---

### Post by Belbear on 2010-08-02
> **ronparent said:**
> 
So the bottom line is that you can skip the workarounds I outlined previously - provided the nested raid can be handled. The solution (I checked -it works) is from a live cd session use Synaptics to install the package 'kpartx' and continue dirctly to the install within the session. You may still have to use the approach I outlined previously (#25) to access the nested partitions. Doing this basically allows the installer to format normally during the install.

Hi, Ron, I'm back.

Sorry, but I don't know what a "Synaptics" is :-s, can you tell me how to find that kpartx and how to install it on an always-blanco livecd boot?

---

### Post by ronparent on 2010-08-02
Glad to hear from you.

The Synaptics Package Manager is on eveery live cd and is what Ubuntu uses to distribute supported programs. In you menu system at the top left of your live cd session desktop, go to System>Administration>Synaptics Pakage Manager. Do a search on kpartx (it will be the only listed search result). Check the box to install it and the check mark to 'apply' it and you are done. You can run gparted next to verify if your raid shows up. If it doesn't, then we have a special problem with a nested raid. Then try the instructions I posted in post #25 and see if that will handle it. But if that is necessary, we may be grasping at straws and may have to find something else to make the symbolic links for raid partitions available in the installer.

---

### Post by Belbear on 2010-08-02
> **ronparent said:**
> I don't know if this will help for the problem with the nested raid, but, I just discovered yesterday of another situation that explains the incompetence of gparted with 10.04.
So the bottom line is that you can skip the workarounds I outlined previously - provided the nested raid can be handled. The solution (I checked -it works) is from a live cd session use Synaptics to install the package 'kpartx' and continue dirctly to the install within the session. You may still have to use the approach I outlined previously (#25) to access the nested partitions. Doing this basically allows the installer to format normally during the install.

Well, i did the sloooow:-\" livecd boot again, got the kpartx and got gparted running. 
As you can see on the screenshot, this fixed gparted and it can see my partition table. 

However, kpartx did NOT fix the installer. Same problem, same result.
Actually its just the same now as in the 9.10 version: gparted works, installer does not.

INSTALLER DOES NOT LIST THE CORRECT RAID DEVICE 'isw_bcihehfidi_raid0+1', ALTHOUGH IT IS IN /DEV/MAPPER AND WORKS WITH GPARTED!

As a gparted test I could reformat the ext2 partition I made earlier to the ext4  filesystem. 
I Don't dare to do extensive repartitioning with this software to set up  linux partitions in the extended partition (involves shrinking my ntfs  'data' partition) instead of the primary it is now. 
Will do that from Windows. At least this is known to understand my RAID  setup properly.

I also tried the dmraid -ay trick you suggested, with all possible devices in /dev/mapper, but to no avail. As you can see, it only produces errors as a result and the installer does not change anything. Did I do something wrong? If there are any 'more options' i'd be happy to know them.

Installer still only lists those dreaded -0 and -1 devices (plus any usb devices connected) and no partitions it can install into. ](*,)

  Now it's 1 am and going to bed.<yawn>.

---

### Post by ronparent on 2010-08-03
It appears that dmraid is not handling your nested raid!? That would put us at a dead end. That is something I'll have to think about - I don't recall that the documentation has sufficient information to enlighten us.

---

### Post by Belbear on 2010-08-03
> **ronparent said:**
> It appears that dmraid is not handling your nested raid!? That would put us at a dead end. 

So you mean "game over"?#-o

---

### Post by ronparent on 2010-08-03
My first install of Ubuntu (8.04) was to a non-raid drive in a basically winXP system. It gave me a chance to probe the raid quirks until I was able to commit to a raid0 install. "game over" only if you want it to be, I would suggest an install to a usb drive. I have also an install to a 16GB memory key which can be carried to multiple computers. I keep hoping tha the developers get a better handle on fakeraid problems. The community could start by not refering to it as fakeraid. But enough venting. I may go back over this thread and post a bug report.

---

### Post by Belbear on 2010-08-03
Well,  I didn't want to use a usb drive (definitely not a flash stick!) because these things are dead slow in comparison to an internal HDD. When booting up or compiling a project with thousands of source files like VLC, that makes a huge difference. 

I might consider buying an e-sata disk (my computer has a socket for it) to make it run faster than usb-2 allows. 

And indeed, "fakeraid" is a lousy word, it would better be called "softraid" or "emuraid" (from emulator)

In that case, I have one more question: Is it possible to boot an installed ubuntu on such an external disk on ANOTHER computer? (with different video/sound/network... hardware?) 

If it is possible it would be nice to be able to shuttle it between my home system and my office system.

---

### Post by ronparent on 2010-08-03
There is no pat answer to that last question. It depends on the hardware differences. I haven't had a problem myself except for maybe using a special boot parameter on one box.

---

### Post by yasitha on 2010-08-21
Belbear, did you find any resolution to this? I'm in exactly the same boat.
 
I am completely new to linux and I wanted to start with ubuntu but this has thrown me a bit!

---

### Post by Belbear on 2010-08-21
> **yasitha said:**
> Belbear, did you find any resolution to this? I'm in exactly the same boat.
 
I am completely new to linux and I wanted to start with ubuntu but this has thrown me a bit!

No. I gave up the idea of installing Ubuntu (or Redhat, that is) on my RAID 0+1
I guess there are not enough people like us to have this kind of issue resolved by the programmers.

Have to get a small but fast external disk (faster than USB2!) to install it on. I don't want a fast OS on a fast PC to be clogged up by a slow HDD.

---

### Post by yasitha on 2010-08-23
Thanks for the reply. Seems to be two problems:
1. Loading into Ubuntu, even using the Live CD, seems to break the array. When you do the next cold boot the array is always degraded. 

2. Even though installing kpartx allows gparted to see the raid array and partition it, the installer itself is unable to see the new partitions.


I've installed Fedora 13 and it seems to work out of the box using LVM. This is my first venture into linux though and I hear Ubuntu is a good way to start! Hopefully there'll be a fix soon

---

### Post by ronparent on 2010-08-23
There is a fix upstream. I don't know when it will make its way to the 10.04 distro.

---

### Post by Belbear on 2010-08-24
> **ronparent said:**
> There is a fix upstream. I don't know when it will make its way to the 10.04 distro.

Can give it a try when it's due...

---

