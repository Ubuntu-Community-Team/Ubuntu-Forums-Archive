---
title: "wubi installer error message"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by burf on 2011-07-11
I am trying to install ubuntu 11.04 desktop onto a partition i created on my netbook called U:.
I am using the latest version of wubi installer.

it installs, let's say.. all the way to the end (the blue bar that shows progress of the installation is full) and then an error message shows:

Error executing command
>>command=C:\Windsows\System32\bcdedit.exe /set{f09e831d-8778-1dff-ad9d-c14a3e115248} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported

>>stdout=





the log file is attatched below:

Whoever solves this problem is my hero. THank you.



log file:(i only pasted the part that seems to be useful)

(...)
07-11 22:26 DEBUG  WindowsBackend: total size=5000
  root=1500
  swap=256
  home=0
  usr=3244
07-11 22:26 DEBUG  TaskList: ## Finished choose_disk_sizes
07-11 22:26 DEBUG  TaskList: ## Running create_preseed...
07-11 22:26 DEBUG  TaskList: ## Finished create_preseed
07-11 22:26 DEBUG  TaskList: ## Running modify_bootloader...
07-11 22:26 DEBUG  TaskList: New task modify_bcd
07-11 22:26 DEBUG  TaskList: ### Running modify_bcd...
07-11 22:26 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 66080.3632813 mb free ntfs)
07-11 22:27 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {f09e831d-8778-11df-ad9d-c14a3e115248} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {f09e831d-8778-11df-ad9d-c14a3e115248} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
07-11 22:27 DEBUG  TaskList: # Cancelling tasklist
07-11 22:27 DEBUG  TaskList: New task modify_bcd
07-11 22:27 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {f09e831d-8778-11df-ad9d-c14a3e115248} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {f09e831d-8778-11df-ad9d-c14a3e115248} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
07-11 22:27 DEBUG  TaskList: New task modify_bcd
07-11 22:27 DEBUG  TaskList: New task modify_bcd
07-11 22:27 DEBUG  TaskList: New task modify_bcd
07-11 22:27 DEBUG  TaskList: ## Finished modify_bootloader
07-11 22:27 DEBUG  TaskList: # Finished tasklist

---

### Post by Rubi1200 on 2011-07-13
Hi and welcome to the forums :)

We actually need you to post the whole log file please.

Two other things that would also help are a screenshot of the Windows Disk Management utility and the results of the boot info script:

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

### Post by jaypanchal.4397 on 2011-11-19
Hi I had the same porblem. I did what you mentioned in the above reply. I got this::


```



                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 204799 sectors, 
                       but according to the info from fdisk, it has 1984 
                       sectors.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 206848. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       419223551 sectors, but according to the info from 
                       fdisk, it has 204799 sectors.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda3 starts 
                       at sector 419430400. But according to the info from 
                       fdisk, sda3 starts at sector 206848. According to the 
                       info in the boot sector, sda3 has 419430399 sectors, 
                       but according to the info from fdisk, it has 419223551 
                       sectors.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 starts 
                       at sector 838860800. But according to the info from 
                       fdisk, sda4 starts at sector 419430400. According to 
                       the info in the boot sector, sda4 has 419430399 
                       sectors, but according to the info from fdisk, it has 
                       1534092719 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       206,847       204,800  42 SFS
/dev/sda3             206,848   419,430,399   419,223,552  42 SFS
/dev/sda4         419,430,400 1,953,523,119 1,534,092,720  42 SFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4250C9BD50C9B7C5                       ntfs       System Reserved
/dev/sda2        7AE0E5CCE0E58EA7                       ntfs       
/dev/sda3        98DCE9B5DCE98E36                       ntfs       
/dev/sda4        C464ECA464EC9B06                       ntfs       
/dev/sda5        18E2D33AE2D31AB8                       ntfs       New Volume
/dev/sda6        EAC034DDC034B225                       ntfs       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  ea 22 10 00 00 00 00 00  |FILE0...."......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  03 00 a2 93 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  bd bf ab c9 31 74 cc 01  bd bf ab c9 31 74 cc 01  |....1t......1t..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  bd bf ab c9 31 74 cc 01  |............1t..|
000000c0  bd bf ab c9 31 74 cc 01  bd bf ab c9 31 74 cc 01  |....1t......1t..|
000000d0  bd bf ab c9 31 74 cc 01  00 40 00 00 00 00 00 00  |....1t...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 00 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 04 00 00 00 00 00  |@...............|
00000130  00 00 04 00 00 00 00 00  00 00 04 00 00 00 00 00  |................|
00000140  21 40 55 21 00 01 a8 8f  b0 00 00 00 50 00 00 00  |!@U!........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  21 01 54 21 21 01 fe fd  |........!.T!!...|
00000190  00 00 01 00 00 d0 a2 93  ff ff ff ff 00 00 00 00  |................|
000001a0  00 00 04 00 00 00 00 00  21 40 55 21 00 01 a8 8f  |........!@U!....|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  21 01 54 21 21 01 fe fd  00 00 01 00 00 d0 03 00  |!.T!!...........|
00000200
MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  ea fd 4f 74 00 00 00 00  |FILE0.....Ot....|
00000010  01 00 01 00 38 00 01 00  a8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  87 41 af 93 00 00 00 00  10 00 00 00 60 00 00 00  |.A..........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  7f 1b e3 e4 31 74 cc 01  7f 1b e3 e4 31 74 cc 01  |....1t......1t..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  7f 1b e3 e4 31 74 cc 01  |............1t..|
000000c0  7f 1b e3 e4 31 74 cc 01  7f 1b e3 e4 31 74 cc 01  |....1t......1t..|
000000d0  7f 1b e3 e4 31 74 cc 01  00 40 00 00 00 00 00 00  |....1t...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  bf b2 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 2c 0b 00 00 00 00  |@.........,.....|
00000130  00 00 2c 0b 00 00 00 00  00 00 2c 0b 00 00 00 00  |..,.......,.....|
00000140  32 80 4d 00 00 0c 42 40  65 d5 bc 74 01 00 f2 8e  |2.M...B@e..t....|
00000150  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
00000160  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 70 00 00 00 00 00 00  |@........p......|
00000180  08 60 00 00 00 00 00 00  08 60 00 00 00 00 00 00  |.`.......`......|
00000190  31 01 ff ff 0b 31 06 1b  7c 04 00 00 00 10 f2 8e  |1....1..|.......|
000001a0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
000001b0  ff ff ff ff 00 00 00 00  01 00 40 00 00 00 05 00  |..........@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 00 01 00 00 d0 87 41  |1..............A|
00000200



```

---

### Post by Rubi1200 on 2011-11-19
Hi and welcome to the forums :)

If you can boot Windows, check the Disk Management utility to see if the disks are labeled as Basic or Dynamic.

I suspect they are Dynamic and if that is the case you would be well advised to not attempt to install Ubuntu (Wubi or regular) on the disk.

The best alternative is to get an external hard-drive and install Ubuntu there.

---

### Post by jaypanchal.4397 on 2011-11-20
Hi and Thanx a lot for your reply. I found my disk type to be dynamic. I hope that is the real problem. I will try to convert the disk type to basic after backing up all my data and then I will check it works or not. Once again thanking you.

---

### Post by Rubi1200 on 2011-11-20
Please make backups!!!

As far as I know, converting the disks is possible but not without risks.

---

