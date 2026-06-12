---
title: "Grub 2, Windows, Hibernation"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by Nickemans on 2010-05-16
Hey guys!

First of all, thanks for your time. Situation: I have a netbook which had Windows XP installed as well as Ubuntu 9.10. I decided to upgrade to Ubuntu 10.04 and decided to do this with a bootable USB.
Using GParted, I deleted my Karmic partition and resized the Windows partition. This last bit gave an error, yet it seemed to look fine, so I continued. Not the smartest thing to do, but I was feeling confident at the time...
Either way, I then launched the Install Ubuntu thing on the desktop and when it got to the partitioning screen, I opted for the side-by-side installation option. Clicked OK, then got an error, saying the partition could not be resized.
This is when I realised my Windows partition was still on hibernate =/
From this point on, whenever I restart I get a "grub-rescue>" screen...

Is there any way of getting grub back or something without having to reinstall Windows or use the entire disk for Ubuntu? As much as I dislike Windows, I do still need it...

Thanks!

---

### Post by Nickemans on 2010-06-03
Bump. I know there are a lot of similar threads about this kind of stuff on here, but I'm in a bit of a pickle as one of my partitions is on hibernate...

---

### Post by kansasnoob on 2010-06-03
A few observations, you said,

> Using GParted, I deleted my Karmic partition and resized the Windows partition.

But then:

> when it got to the partitioning screen, I opted for the side-by-side installation option. 

Side-by-side (aka: auto-resize) actually looks at the existing partitions and once again resizes (or attempts to resize) one of them :(

Anyway the "grub-rescue>" prompt is because you wiped out Karmic but undoubtedly still have a grub 2 MBR. But I need more information to be certain what the situation is.

First, using the Live USB (or CD) post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Also while in the Live Desktop take a screenshot of Gparted using the tool in Accessories and attach it here using the little paper clip thingy at the top of the reply box.

Also, something you can try, **assuming you have only one hard drive** (which would make it /dev/sda) copy-n-paste in the terminal:

```
sudo apt-get install lilo
``` 

```
sudo lilo -M /dev/sda mbr
```

That should allow Windows to **try** to boot and will also let us know how much trouble Windows is in :)

---

### Post by Nickemans on 2010-06-03
Thank you so much for your reply =)

Here the output from Boot Info Script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       194954208 sectors, but according to the info from 
                       fdisk, it has 299981504 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,595,200   312,576,704   299,981,505   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,945,059     3,944,998   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4026 MB, 4026531840 bytes
216 heads, 32 sectors/track, 1137 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     7,831,551     7,831,520   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       c52cb0fe-7478-4969-a3d3-1af737c6d34b   ext3                                     
/dev/sda1        9250A5F050A5DB6D                       ntfs       PQSERVICE                     
/dev/sda2        688E70958E705E0E                       ntfs       ACER                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D7B7-E437                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2060-2EF0                              vfat       Lexar                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/Lexar             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu Netbook Remix" 
```Also used the Lilo tool and surprise surprise, Windows booted!

Does this mean it is safe to try and install Ubuntu again? Or not quite yet?

---

### Post by oldfred on 2010-06-03
You should be able to reinstall. But do you really want to let the automatic installer resize everything or manually set up partitions so you have complete control over the sizes?

I usually recommend 10-20GB for root, 2GB or RAM size if you want to hibernate for swap and the rest of available space for /home. If you do the automatic setup you will not have a separate /home. You can use gparted to set up partitions and then use the manual install to choose those partitions for the install.

Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Version is older but process is still the same.
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

---

### Post by kansasnoob on 2010-06-04
First of all defrag Win XP! Then figure out how much space you want to give Ubuntu. I see Windows is using a bit over 56GB and I never like to fill a Windows partition beyond about 70% so I'd let Windows have at least 100GB to 120GB which would leave you roughly 30GB to 50GB for Ubuntu.

But a lot of that is up to you. You could give Ubuntu as little as 12GB total and just use the technique shown here:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

This one applies to the Lucid installer and shows creating a separate /home but it's spread over two discs:

[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

A separate /home can be beneficial later on if you have to reinstall. You'd still have to choose to use it as /home but just be sure NOT to reformat when reinstalling, but that's something to worry about later on.

Just as an example layout I'll show you on my spare 80GB drive. I'm just giving Ubuntu 30GB:

[ATTACH]159320[/ATTACH]

You'll notice that I labeled the first two primaries as "Your Windows", then created an 8GB Lucid root "/" primary partition, then created an extended partition to contain a logical /home and SWAP. That's because all drives have a 4 primary limit.

An 8GB / (aka: root) partition should be plenty with a separate /home. I basically double the size of my RAM up to 2GB of SWAP, and if RAM exceeds 2GB I then make SWAP just slightly larger than total RAM to ensure hibernation.

If this is at all confusing please ask more questions, planning is always best :)

---

### Post by Nickemans on 2010-06-04
Thanks guys!
@kansasnoob, I'm not very familliar with the way hard drives and partitions work, so I'm kind of lost haha. Why are there two different windows partitions and two different Lucid partitions?
And is an extended partition just so you can keep with the 4 primary limit?

Cheers!

---

### Post by kansasnoob on 2010-06-04
> Why are there two different windows partitions and two different Lucid partitions?

There are two Windows partitions because that's what you already have according to your screenshot. One is called PQSERVICE and the other ACER according to Gparted.

My sample screenshot actually shows three partitions for Lucid: / (aka: root), /home, and SWAP. You don't have to create a separate /home but it does make reinstalling easier if something goes wrong later on.

> And is an extended partition just so you can keep with the 4 primary limit?


Yes. I usually create 3 primaries and one extended which can contain many logical partitions. Sometimes I'll use only 2 primaries and one extended if I anticipate adding a second Windows because Windows doesn't like to live in a logical partition.

---

### Post by Nickemans on 2010-06-04
Ah yes youre right haha.
Oh i see, I'll have a look into it =)

---

