---
title: "Boots up to Grub command line"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by osiris123d on 2010-12-02
I am trying to install Ubuntu 10.10.  I first tried to install by booting up the CD and selecting Install Now.  Everything went well until it tried to set up Grub.  I cancelled the install and found this post on this forum

[http://ubuntuforums.org/showthread.php?t=1598478](http://ubuntuforums.org/showthread.php?t=1598478)

So I booted up with LiveCD and did the boot info script.  Then I did 
sudo mount /dev/sda1 /mnt                      
sudo grub-install --root-directory=/mnt/ /dev/sda                      

I tried to do the following
sudo grub-install --root-directory=/mnt/ /dev/sda                      

But it barked at me for that.  

Then I rebooted and I am at the Grub command line.  

Not sure what is wrong.  Here is a printout of the Boot Loader Report

                Boot Info Script 0.55    dated February 15th, 2010              
      

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _________________________________________________
____

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solar
is


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL        
                 

/dev/loop0                                              squashfs                
                 
/dev/sda1        d905e941-2bc2-41df-9cb1-3f3bf46a253c   ext4                    
                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        44a5b09a-30ad-46c1-84b8-89a11b3b7493   swap                    
                 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ======================
=====

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d905e941-2bc2-41df-9cb1-3f3bf46a253c /               ext4    errors=remount
-ro 0       1
# swap was on /dev/sda5 during installation
UUID=44a5b09a-30ad-46c1-84b8-89a11b3b7493 none            swap    sw            
  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
    .5GB: boot/initrd.img-2.6.35-22-generic
   2.2GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
   2.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc ======================
=

Unknown BootLoader  on sda2

00000000  61 89 4d c8 62 78 3a 3e  9e 0f 97 c1 85 c0 64 11  |a.M.bx:>......d.|
00000010  3a ec 45 33 21 f2 c0 7c  31 9f ec 26 5c 88 61 80  |:.E3!..|1..&\.a.|
00000020  ae 11 d4 11 0c 06 42 03  3d 82 be c2 32 16 20 a0  |......B.=...2. .|
00000030  78 35 50 08 54 43 63 a1  d0 e0 72 29 be 0c 3f 27  |x5P.TCc...r)..?'|
00000040  ff 10 27 90 46 0a e0 15  28 4d 26 17 cd 3a c8 3c  |..'.F...(M&..:.<|
00000050  70 20 f7 4a 75 d2 99 40  e5 00 b0 25 15 19 c0 95  |p .Ju..@...%....|
00000060  00 a8 41 40 b6 49 3a 10  0a c5 3e d9 e0 ba 56 0f  |..A@.I:...>...V.|
00000070  c4 12 49 84 da 35 8a 5d  20 61 a9 d1 d8 d4 a2 d9  |..I..5.] a......|
00000080  5c 12 18 f8 31 3f d9 52  79 00 c9 e1 fb a2 7a 47  |\...1?.Ry.....zG|
00000090  d2 10 1a a7 7e af 5d aa  d7 7e f5 5f fe ab 54 3f  |....~.]..~._..T?|
000000a0  60 56 18 55 7b f5 4f f6  e2 eb 40 3e 08 70 2c 30  |`V.U{.O...@>.p,0|
000000b0  fd 4f ae 6a d4 50 ea d7  67 fb f8 ac 9e cb 85 c7  |.O.j.P..g.......|
000000c0  9c a4 29 fe da 57 62 33  3b bc f6 e3 58 12 df 05  |..)..Wb3;...X...|
000000d0  19 03 61 b9 c8 28 e8 08  5a 08 1e 08 34 8e 2f ad  |..a..(..Z...4./.|
000000e0  ca a5 70 20 3e 0c 7e 1b  3c 9b 20 90 e3 01 34 1b  |..p >.~.<. ...4.|
000000f0  ac 14 c6 84 57 e0 8d 51  2d d0 30 09 84 02 25 6e  |....W..Q-.0...%n|
00000100  cd 42 30 d1 9e 04 63 25  85 c5 5e 21 15 b8 92 58  |.B0...c%..^!...X|
00000110  c3 d9 39 82 c8 d1 3c 14  8f 77 33 2d 18 2e 68 1e  |..9...<..w3-..h.|
00000120  b0 22 b3 68 c6 50 2d 61  12 8d 74 e1 4f 4b 05 97  |.".h.P-a..t.OK..|
00000130  04 03 85 e4 e2 c3 fa 17  89 4c 88 8a 61 e0 d5 ea  |.........L..a...|
00000140  b1 65 36 1a 7d 62 d5 3c  d2 49 24 17 17 9a 04 8a  |.e6.}b.<.I$.....|
00000150  cd 0e a4 45 a9 18 7e 02  9e c3 52 45 c0 4c 70 60  |...E..~...RE.Lp`|
00000160  f4 78 d5 35 01 45 4b a5  c0 e1 05 8c 31 1e a5 18  |.x.5.EK.....1...|
00000170  01 63 42 42 a3 51 82 e8  13 a4 04 d2 08 af 52 73  |.cBB.Q........Rs|
00000180  c0 2a e0 50 a5 10 e8 64  39 31 40 9b d0 4d e8 29  |.*.P...d91@..M.)|
00000190  3c 03 bc 0a 6a 09 14 4d  71 e0 8f 60 80 e4 e0 31  |<...j..Mq..`...1|
000001a0  3f 0c 7e 83 db 71 28 66  93 4c 12 cc 41 de 82 02  |?.~..q(f.L..A...|
000001b0  0a 20 fa 47 7c d2 1a 11  4d 00 ce 61 0c d0 00 fe  |. .G|...M..a....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by wilee-nilee on 2010-12-02
sda1: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.10
Boot files/dirs:  **/boot/grub/grub.cfg** /etc/fstab /boot/grub/core.img

Your missing the highlighted part here and in the script altogether. I think this is a fairly simple fix you just need the right person with that information. Hang on your on at the right time of night so I think your close.

If you can to as well look in my signature at the code tags description and code tag the text it will be helpful for those helping.;)

---

### Post by ramaswamyps on 2010-12-02
```
sudo grub-install --root-directory=/mnt/ /dev/sda

```
instead try grub-install /dev/sda

after you can boot in the system you can edit grub.conf as needed.

your root is /dev/sda1 not /dev/sda
that is why you had problems.[as you said barking at you :)]

---

### Post by drs305 on 2010-12-02
You don't have a full grub installation. Although 'grub-install' sounds like it would install grub, it really is more about writing to the MBR and telling that where to look for the grub files.

Since you already have a grub installation, you will need to boot from the LiveCD and chroot into your Ubuntu partition (sda1). 'Chrooting' will allow you to use the CD files but let them act on your real Ubuntu installation.

You can go to the following link and begin at Step 1. Your Ubuntu install is sda1.
Do not worry about creating the /mnt/temp/boot folder - you don't need it. 

You can either run the "purge" command and then install grub-pc or **Added:** you can change the "apt-get install" command to "apt-get install --reinstall" so grub.cfg is created.

[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by wilee-nilee on 2010-12-02
> **drs305 said:**
> You don't have a full grub installation. Although 'grub-install' sounds like it would install grub, it really is more about writing to the MBR and telling that where to look for the grub files.

Since you already have a grub installation, you will need to boot from the LiveCD and chroot into your Ubuntu partition (sda1). 'Chrooting' will allow you to use the CD files but let them act on your real Ubuntu installation.

You can go to the following link and begin at Step 1. Your Ubuntu install is sda1.
You don't have to run the "purge" commands nor worry about creating the /mnt/temp/boot folder;  but you should run the install command for grub-pc.

[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

+1 this is what I thought as well, op this should get you back in shape.

---

