---
title: "multiple boot"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by Agonche on 2010-08-12
i just installed ubuntu 10.04
i have windows xp installed and i wanted dual boot
so i installed it but when i rebooted (the final step of the installation)
my pc doesnt show me the option to choose from which OS i want to boot
it directly goes on windows xp.

can anyone help.

---

### Post by Rubi1200 on 2010-08-12
How did you install Ubuntu; from the CD or via Wubi?

Do you have, or can you get, an Ubuntu CD?

What are your computer specs. e.g. RAM, disk capacity, graphics card etc?

---

### Post by Agonche on 2010-08-12
i downloaded ubuntu 10.04
i burned the .iso file with infrarecorder.
then it showed me the menu how i want to install it 
i choosed "install inside windows"
...
like i said i alredy have the CD (dvd)
...
RAM: 512MB
HDD: (C)samsung 40gb , (D) maxtor 320gb
VGA: radeon 9250 (128MB)

thanks for the quick reply :P

---

### Post by Rubi1200 on 2010-08-12
So, here is what I need you to try please.

Boot the computer with the CD, making sure BIOS is set to boot from the CD/DVD drive.

Then, when you see the Ubuntu logo, choose to try Ubuntu in live mode. 

Do not choose to install.

Once you are at the Desktop on the live CD, connect to the Internet and then click on the link at the bottom of my post.

Follow the instructions there and post the results back here.

We can then have a better idea of your setup and how to help with the next step.

If anything is unclear, please ask.

---

### Post by Agonche on 2010-08-12
[http://www.mediafire.com/?5tb58ve3e59e9vv](http://www.mediafire.com/?5tb58ve3e59e9vv)

RESULTS.txt

---

### Post by Rubi1200 on 2010-08-12
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,236,549    78,236,487   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        F05885275884EE22                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ECF05D48F05D1A62                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/ECF05D48F05D1A62  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


```I am not sure what you were trying to do here??

You have 2 drives, both with Windows XP and one of them with Wubi.

Wubi is not the way to install Ubuntu to the hard-drive; it is meant only for testing.

If you want to dual-boot using Ubuntu on the 40GB drive and leave XP on the other drive, then you will need to let us know.

---

### Post by Agonche on 2010-08-12
I have windows XP on my c drive (samsung 40gb)
my D drive does not have any OS

i just wanted multiple boot but i couldn't do this
i think i'll do a clean install of ubuntu.

---

