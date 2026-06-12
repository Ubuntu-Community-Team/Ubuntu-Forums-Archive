---
title: "Wubi install doesnt work"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by Chocchief on 2011-05-28
Hello i installed ubuntu desktop 11.04 on my acer aspire one 751h and found that the wifi didnt work. the netbook remix was the same so i went through all the previous releases up until 8.0.4.4 which worked fine on the live cd. so i tried to install but the installer didnt see my main hard drives only the usb i was using to install. so i tried using wubi installer which only left me with this screen when i tried to load up ubuntu
[IMG]http://img855.imageshack.us/img855/1214/img20110528154334.jpg[/IMG]
Help???:confused:

---

### Post by Rubi1200 on 2011-05-28
Hi and welcome to the forums :-)

Do you have a LiveCD or LiveUSB?

If yes, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Chocchief on 2011-05-28
Heres the results.txt:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1467712 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4041 MB, 4041211904 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892992 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006e8dc

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,892,991     7,892,929   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        EAC4-4273                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options



============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Try Ubuntu without any change to your computer 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.gz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry1 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.gz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry2 
menu label ^Check CD for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.gz boot=casper integrity-check  quiet splash -- 
 
label ubnentry3 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit - 
 
label ubnentry4 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit - 
 
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys
            ?? = ??             menu.c32
            ?? = ??             syslinux.cfg

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sda 

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by Rubi1200 on 2011-05-28
This shows the results for the USB stick (I assume) and not the hard-drive where you are trying to install.

Do you have Windows installed in a RAID array or some other non-regular configuration?

What does this command from the LiveUSB show?

```
sudo fdisk -l
```

(lowercase L not 1)

---

