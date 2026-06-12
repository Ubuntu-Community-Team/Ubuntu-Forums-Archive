---
title: "uninstall disaster"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by ten_dot_ten on 2010-10-16
Hello,

I'm a brand new user who just installed Ubuntu last weekend. I've been having some problems, and decided to start over by deleting the partition and reinstalling. I followed uninstall info from here: [http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/). 

There was the main Windows partition and two "unknown" partitions - one was very small and one was approximately the size of the partition I'd set up for Ubuntu. I deleted the large unknown partition, and within a couple of minutes I got a blue screen with long messages about an error.

I rebooted, but the system wouldn't boot. My original installation disk wouldn't boot either, and I got a "grub rescue" prompt. I followed the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=1326788](http://ubuntuforums.org/showthread.php?t=1326788), and have these results from the script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,320,945   117,320,883   7 HPFS/NTFS
/dev/sda2         117,321,726   195,371,007    78,049,282   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5     ? 1,269,146,865 3,468,159,573 2,199,012,709  87 NTFS volume set

/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        62EAFBF16D5E4C87                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
error: /dev/sda5: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  29 bf bf 3f d7 4d 6b 66  31 0b e7 ff 7e fc e0 a8  |)..?.Mkf1...~...|
00000010  b8 e0 b7 80 09 cf e0 83  8b 75 57 80 0d cf 03 ef  |.........uW.....|
00000020  aa 88 aa e0 86 31 ea e2  0e 07 aa d7 d1 4c 17 00  |.....1.......L..|
00000030  e2 e0 0a ee fb d5 64 87  81 ca 17 bf 2b 03 e0 fc  |......d.....+...|
00000040  e0 00 e7 80 1a 47 e0 ab  ab 0a a9 44 07 e0 f7 bf  |.....G.....D....|
00000050  a2 d6 04 0f c3 d4 77 00  ae 80 2a e0 eb 2b 3a 5d  |......w...*..+:]|
00000060  04 5f e0 aa aa a8 57 80  1e 27 c3 8d e7 00 5d e2  |._....W..'....].|
00000070  eb 63 c7 77 8b 2a e0 c7  39 ab 8d 46 57 ef 9f 81  |.c.w.*..9..FW...|
00000080  e8 87 2e dd 7f e0 8d a2  fb ef 64 ff e0 bf e2 ff  |..........d.....|
00000090  2a 64 ff e0 7f b5 af 68  04 6f e0 5e 7f af 82 80  |*d.....h.o.^....|
000000a0  26 7f 0b 27 7f 5f af 81  e2 b7 d5 b8 f6 81 e8 a7  |&..'._..........|
000000b0  e3 7f f5 e0 c3 bf fb fb  80 2c 97 e2 35 17 de 27  |.........,..5..'|
000000c0  0c 63 00 00 58 5c 5e 5c  c0 c3 5f 27 c0 bd cf 03  |.c..X\^\.._'....|
000000d0  e0 57 ea 58 f4 80 13 1f  43 4f 7a 11 8f e0 25 29  |.W.X....COz...%)|
000000e0  5f b0 29 e7 f7 e0 5f fe  b7 0a 80 05 1f c3 91 b7  |_.)..._.........|
000000f0  01 5d 5e fe 07 27 55 d6  e0 e0 15 e5 7d 59 80 07  |.]^..'U.....}Y..|
00000100  3f e2 ac f7 ef ee 45 29  24 21 78 5e 95 7d 80 07  |?.....E)$!x^.}..|
00000110  27 c3 a1 77 00 bf de bc  e2 0a 57 fa 2a 65 29 25  |'..w......W.*e)%|
00000120  29 7f 55 37 7b 04 1f e0  bf f5 f0 e2 04 0f e0 57  |).U7{..........W|
00000130  75 df e8 04 0f e0 ff d7  28 a8 01 07 65 c3 ba ff  |u.......(...e...|
00000140  00 af 5f 5b e0 a2 eb fd  75 80 1b 8f e0 08 a7 ea  |.._[....u.......|
00000150  dd 04 07 e0 aa 02 ff 55  04 07 e0 ac b8 5f cb 80  |.......U....._..|
00000160  09 b7 d3 51 df 00 22 82  ab d3 4e 17 00 be f2 ff  |...Q.."...N.....|
00000170  e0 aa fb f7 d3 80 1d cf  d3 51 ff 00 f2 6a e2 e0  |.........Q...j..|
00000180  a8 2a da 7f 80 07 6f 63  c7 7b 6f c7 e0 45 29 25  |.*....oc.{o..E)%|
00000190  9d 46 6f ff bb 4b 8f a8  af d7 e0 ca 60 6b 7d 80  |.Fo..K......`k}.|
000001a0  10 07 e2 a8 fe de ab a7  39 04 21 ea bb 35 ee 24  |........9.!..5.$|
000001b0  9f 0e 4f eb bc e2 2f ff  7f f5 a6 31 65 29 00 fe  |..O.../....1e)..|
000001c0  ff ff 05 fe ff ff c3 af  74 04 3f 40 32 00 00 00  |........t.?@2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda5



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
```Please help me restore my computer to a bootable and preferably unpartitioned state!

---

### Post by Megaptera on 2010-10-16
When you tried your Windows rescue disc, had you set the BIOS to boot from CD? I've used that MakeUseOf guide a couple of times myself & it works so that's why I ask about the BIOS boot order.

On my Dell at start-up (for instance) one has to click F12 to access BIOS menu.

---

### Post by ten_dot_ten on 2010-10-16
F10 gets me into BIOS (HP Pavilion laptop). I'm there now. In the >Tools dropdown, when I select the >Boot Order sub-menu, I get an option for >HDD Self-test. When I select it's sub-menu, I get 3 options: >Exit Saving Changes, >Exit Discarding Changes, >Load Setup Defaults. That's it. Since  selecting >Boot Order, I can no longer access the other Tools in that sub-menu. :(  But the Ubuntu disk boots perfectly, so the CD/DVD drive must be in the lineup.

edit:
I got the boot order: 
Floppy Diskette Drive (don't have one)
CD-ROM Drive 
+Hard Drive
Network Adaptor

There are still no other Tools showing up other than HDD Self-test, which I ran the short one (one minute) and it passed.

Also, before the grub rescue prompt is an error message:
"error: no such partition."

And when I try to boot from the OS install disk, I get this message:
"press any key to boot from CD"
and then after I press a key, I get this message:
"Setup is inspecting your computer's hardware configuration..."
After that, one of two things happens: 1) I get a message about a media error (can't reproduce that at the moment), or 2) nothing at all - a blank screen and the CD stops spinning.

---

### Post by ten_dot_ten on 2010-10-16
I believe this problem is resolved. I'm not sure how it happened, but I'm able to boot into Windows again. I was feeling pretty desperate, so inserted my PartitionMagic disk, and while it wouldn't actually boot the computer, the computer booted after I tried with PM. All that's left now is to reallocate the now unallocated space, which shouldn't be too big of a deal.

---

### Post by Megaptera on 2010-10-17
Glad to read that it's solved and I hope it goes OK.

---

