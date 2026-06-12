---
title: "This computer currently no detected operating system &quot;ubuntu 11.04&quot;"
date: 2011-10-03
forum: Installation &amp; Upgrades
---

### Post by Di4Bl3-N0iR on 2011-10-03
Hello guy's.
Pleaz help me.. i have a problem with ubuntu 11.04  i wanna install it like a 2 nd windows with Windows 7 (i wanna install it from the CD not from Windows 7) so when install it this msg come.. "This computer currently no detected operating system" but i already have Windows 7 alsoo i try to install it from Wuby but Nothing ... pleaz guy's help me i wanna install it coumplai not from Windows 7.. Luck to this pictur... " i have just 2 choice not 4 like tuto in Youtub".. and soory guy's i dont speack the englaich very well !!!!


[IMG]http://www.pikipimp.com/pp/pimped_photo/s/image/60/154/883/Capture-preview.png?ts=1317662152919[/IMG]
i'm waiting .. ):P

---

### Post by presence1960 on 2011-10-03
I need to see exactly what you have on your machine before trying to install Ubuntu. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Di4Bl3-N0iR on 2011-10-03
Okey.. This is the result:

```

_______________________________________________________________________________
                  Boot Info Script 0.60    from 17 May 2011


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
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disque /dev/sda: 250.1 Go, 250058268160 octets
255 têtes, 63 secteurs/piste, 30401 cylindres, total 488395055 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   102,397,951   102,191,104   7 NTFS / exFAT / HPFS
/dev/sda3         102,398,371   488,396,799   385,998,429   f W95 Extended (LBA)
/dev/sda5         102,398,373   204,796,619   102,398,247   7 NTFS / exFAT / HPFS
/dev/sda6         204,796,683   307,194,929   102,398,247   7 NTFS / exFAT / HPFS
/dev/sda7         307,194,993   409,593,239   102,398,247   7 NTFS / exFAT / HPFS
/dev/sda8         409,600,863   488,375,999    78,775,137   7 NTFS / exFAT / HPFS

/dev/sda3 ends after the last sector of /dev/sda

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3AA07236A071F929                       ntfs       System Reserved
/dev/sda2        04AE8185AE816FCA                       ntfs       WinDows 7
/dev/sda5        A000C2C700C2A39E                       ntfs       RiaD_M-b
/dev/sda6        1CBCC988BCC95D40                       ntfs       Di4BL3 NoiR
/dev/sda7        AA968CB5968C8413                       ntfs       Effect
/dev/sda8        60A0875BA0873696                       ntfs       LiNux

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
```

---

### Post by oldfred on 2011-10-03
Please you code tags on longer data, I edited to add them.

Did you use Windows to create the partitions? Your extended partition is beyond the end of the drive.

> 255 têtes, 63 secteurs/piste, 30401 cylindres, total [COLOR=DarkRed]488395055[/COLOR] secteurs
/dev/sda3         102,398,371 [COLOR=DarkRed]  488,396,799[/COLOR]   385,998,429   f W95 Extended (LBA)
/dev/sda3 ends after the last sector of /dev/sda

copy partition table to a backup just in case.
sudo sfdisk -d /dev/sda > sdaparts.txt

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Best to create partitions with gparted from liveCD. Plus Linux needs linux formats like ext3 or ext4 (many others) but not Windows formats like NTFS to work. You need two partition one EXT4 and one unformated for swap as a minimum. I often suggest a shared NTFS partition just for data you may want in both & it looks like you have several NTFS partitions.

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Di4Bl3-N0iR on 2011-10-03
i have about 38 Giga free in ntfs partition ... how i can use it or how i can change the partition format ntfs to  swap & ext4. with a programme or what ? i'm now in ubuntu Live CD ....

---

### Post by oldfred on 2011-10-03
You can either shrink the NTFS partition or backup any data and delete and recreate as ext4. Generally we suggest using the Windows partition tools just for shrinking the windows system partition.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

If you partition in advance then you have to use manual install (Something else in Natty). 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Di4Bl3-N0iR on 2011-10-03
i try but luck to the pictur.. in windows 7 i have 5 partition, 1 for w 7 and the 3 outher for y files and the last ne is ampty for linux but he is in ntfs...

[IMG]http://desmond.imageshack.us/Himg214/scaled.php?server=214&filename=capturetry.png&res=medium[/IMG]

---

### Post by Di4Bl3-N0iR on 2011-10-03
Okey... oldfred .. i will try to recreate  the partition ntfs to ext4 from windows . thnx gey's .. i will be back soooon :P .

---

### Post by oldfred on 2011-10-03
Until you fix the partition error gparted will not work. And I do not trust Windows with extended partitions as we have seen the error before. Please make sure you have good backups as partition errors can lead to huge problems and backups are the last resort if things go South.

---

