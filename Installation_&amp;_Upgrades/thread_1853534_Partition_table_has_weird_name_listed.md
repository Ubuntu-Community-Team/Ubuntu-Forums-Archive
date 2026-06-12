---
title: "Partition table has weird name listed"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by spectre2028 on 2011-10-02
I run a tri-boot setup with WindowsXP, straight Ubuntu, and whatever Linux flavor-of-the-moment I feel compelled to try out.

Somewhere in the process of installing/uninstalling the various versions of Linux, one of my Windows partitions somehow ended up getting assigned the rather strange name of "<_BODY><_HT". That is actually how it shows up now in Ubuntu's Places and all the different file managers that I use. Is there a safe/easy way to correct this in the main partition table?  (assuming that's where the error lies)

---

### Post by presence1960 on 2011-10-02
Before changing anything it is wise to see exactly what you have on that machine. Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by spectre2028 on 2011-10-02
> **presence1960 said:**
> Before changing anything it is wise to see exactly what you have on that machine. Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:


 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

___________________________________________

It's not a mysterious partition, it's the main 47Gig one I use in Windows and even in Linux. Sda5 originally.
```


                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 8 for (,msdos8)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 56258560.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda6 starts at sector 148537344.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb5 starts at sector 50796544.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdb6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb6 starts at sector 297109504.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdb7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb7 starts at sector 554024960.
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Netrunner 3 Chromatic
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    56,256,511    56,256,449   c W95 FAT32 (LBA)
/dev/sda2          56,258,558   312,580,095   256,321,538   f W95 Extended (LBA)
/dev/sda5          56,258,560   148,535,295    92,276,736   b W95 FAT32
/dev/sda6         148,537,344   240,730,111    92,192,768   b W95 FAT32
/dev/sda7         240,732,160   260,261,887    19,529,728  83 Linux
/dev/sda8         260,263,936   262,215,679     1,951,744  82 Linux swap / Solaris
/dev/sda9         262,217,728   312,580,095    50,362,368  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       999,423       997,376  82 Linux swap / Solaris
/dev/sdb2           1,001,470   976,773,119   975,771,650   5 Extended
/dev/sdb5          50,796,544   297,107,455   246,310,912   b W95 FAT32
/dev/sdb6         297,109,504   554,022,911   256,913,408   b W95 FAT32
/dev/sdb7         554,024,960   976,773,119   422,748,160   b W95 FAT32
/dev/sdb8           1,001,472    20,531,199    19,529,728  83 Linux
/dev/sdb9          20,533,248    50,782,207    30,248,960  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  32    15,633,407    15,633,376   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        DC8C-1748                              vfat       
/dev/sda5        2BB4-1849                              vfat       </BODY></HT
/dev/sda6        31FC-232B                              vfat       
/dev/sda7        28487a7f-dbd3-42c2-ae03-bcaa7d8f0c0a   ext4       
/dev/sda8        f7abe27e-ee5d-49eb-8392-9c38122b2bb0   swap       
/dev/sda9        73fde642-0331-4ac2-9973-1349087b9371   ext4       
/dev/sdb1        62c38748-aeeb-41ac-ac0f-195cae55f64c   swap       
/dev/sdb5        94BE-6D94                              vfat       
/dev/sdb6        9883-D26F                              vfat       
/dev/sdb7        9BAC-5E22                              vfat       
/dev/sdb8        d78164e7-ff78-4291-bc68-bd2541bc5166   ext4       
/dev/sdb9        879e5cfa-247f-4b55-ad30-1c24682938f5   ext4       
/dev/sdc1        39C6-A26C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /media/<_BODY><_HT       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda9        /home                    ext4       (rw,commit=0)
/dev/sdb5        /media/94BE-6D94         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc1        /media/39C6-A26C         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /bootlog

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------
```

---

### Post by coffeecat on 2011-10-02
@spectre2028, I've added code tags around your boot script output as presence1960 asked you to. It is unwieldy without. I've also tidied up your quote tags.

You might find this forum guide to BBCode useful:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

The quick way of adding code tags is to use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by spectre2028 on 2011-10-02
Thanks for putting in the tags.  Totally missed that in his post, and I agree that results file is pretty long.

---

### Post by presence1960 on 2011-10-03
Everything appears good. I would boot into ubuntu and use gparted to change the label on sda5. If you don't have gparted installed open a terminal and run ```
sudo apt-get install gparted
``` to install it. The run it and remove the label on sda5.

You do have some notices about partitions having conflicting beginning points on the disk. If they all work well I would leave it be.

Sorry for delay but my internet provider was down yesterday.

---

### Post by presence1960 on 2011-10-03
Just in case you don't know how to change the label in gparted. See attached pic. Highlight your sda5 partition and right click and choose label. if you want no label leave it blank or rename it if you want it named. 

Since it is FAT 32 you can also rename it from Windows Explorer or My Computer from within Windows.

---

### Post by spectre2028 on 2011-10-03
Thanks, I'll give Gparted a try.

Did verify yesterday that Windows is still seeing it as D:, and I don't think it has any other name listed, so this must be a Linux or grub thing.

---

### Post by spectre2028 on 2011-10-03
I was able to change the name, but the mystery isn't totally solved.  The other partitions have no labels, and when I bring up them up in Disk Utility or GParted, their name field is blank.  But when I blank out the name field (or put spaces) for the partition in question, it goes right back to the bizarre hyperlink-looking name I described at the start of this thread. It only looks halfway normal when a specific name is entered.  

I guess the only real solution here would be to delete the partition and recreate it.  Don't think I'll go that far yet, as the system still appears to be working okay, as is.

---

