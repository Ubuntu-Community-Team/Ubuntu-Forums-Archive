---
title: "BOOTMGR missing, any help on how to fix?"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by liamhale on 2012-03-27
hello guys,
spent a long time yesterday trying to sort my laptop out, i have ubuntu installed on my pc but previously my computer just loaded up a black screen with a white cursor, someone suggested it was the video driver, so i have downloaded onto a usb and i have got somewhat further, but now i have the error 'BOOTMGR is missing'
any chance of fixing this without wiping and reinstalling preferably on a usb stick?

thanks guys

---

### Post by darkod on 2012-03-27
I think you tried running the boot info script in your other thread earlier. We really need those results in this case to help troubleshoot.

If you need more instructions, follow the link in my signature which has the instructions how to run the script and post the results.

If your ubuntu boots you can do that from ubuntu, if not you can do it from ubuntu cd in live mode.

This is a windows message, that the boot file bootmgr is missing. Doesn't have much to do with ubuntu, something happened to your windows boot files.

---

### Post by liamhale on 2012-03-27
> **darkod said:**
> I think you tried running the boot info script in your other thread earlier. We really need those results in this case to help troubleshoot.

If you need more instructions, follow the link in my signature which has the instructions how to run the script and post the results.

If your ubuntu boots you can do that from ubuntu, if not you can do it from ubuntu cd in live mode.

This is a windows message, that the boot file bootmgr is missing. Doesn't have much to do with ubuntu, something happened to your windows boot files.

i am a begginer at ubuntu, i am trying my hardest not to keep ask seemingly obvious questions,  but i have downloaded the file and i have put it onto the ubuntu desktop, and typed the code sudo bash and almost every combination i can think of.

i have this code for certain: '/home/ubuntu/Desktop/boot_info_script.sh'

and i need sudo bash or just sudo


thanks again for helping me so much, i know i am not the most easiest of people to help as i am very much in the dark when it comes to the basics etc of ubuntu

---

### Post by darkod on 2012-03-27
Sometimes I am not 100% sure myself. :)

Also, at the end of the file name, before the extension, add * to replace any version number it might contain. So, try something like:

```
sudo bash /home/ubuntu/Desktop/boot_info_script*.sh
```Don't forget, in linux desktop is not the same as Desktop. Type exactly as it says.

---

### Post by liamhale on 2012-03-27
> **darkod said:**
> Sometimes I am not 100% sure myself. :)

Also, at the end of the file name, before the extension, add * to replace any version number it might contain. So, try something like:

```
sudo bash /home/ubuntu/Desktop/boot_info_script*.sh
```Don't forget, in linux desktop is not the same as Desktop. Type exactly as it says.
I finaly have it
thanks for the code, i was missing the asterisk, it is still beyond me why that was needed :P
i also managed to search for the results.txt file as i couldnt find that originally either

but these are the results:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:   Syslinux looks at sector 36128324 of /dev/sdb for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   154,222,591   154,220,544  83 Linux
/dev/sda2         154,224,638   156,301,311     2,076,674   5 Extended
/dev/sda5         154,224,640   156,301,311     2,076,672  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        e2359f4d-788e-4340-9c7c-ce7ed8cd0e19   ext4       
/dev/sda5        326b6b44-75e8-46d7-9340-1b9a236c036f   swap       
/dev/sdb         0EE3-0B30                              vfat       PENDRIVE
/dev/sdc         08AE-9315                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/e2359f4d-788e-4340-9c7c-ce7ed8cd0e19 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc         /media/08AE-9315         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e2359f4d-788e-4340-9c7c-ce7ed8cd0e19 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=326b6b44-75e8-46d7-9340-1b9a236c036f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                vmlinuz                                        1

========================== sdb/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================== sdb: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

=============== sdb: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc

00000000  eb 58 90 58 42 4f 58 33  36 30 20 00 02 20 52 18  |.X.XBOX360 .. R.|
00000010  02 00 00 00 00 f8 00 00  11 00 04 00 00 00 00 00  |................|
00000020  00 80 3d 00 d7 03 00 00  00 00 00 00 02 00 00 00  |..=.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 15 93 ae 08 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 42 4f  |..............BO|
000001b0  4f 54 4d 47 52 20 69 73  20 6d 69 73 73 69 6e 67  |OTMGR is missing|
000001c0  ff 0d 0a 44 69 73 6b 20  65 72 72 6f 72 ff 0d 0a  |...Disk error...|
000001d0  50 72 65 73 73 20 61 6e  79 20 6b 65 79 20 74 6f  |Press any key to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  00 ac c1 ce 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by darkod on 2012-03-27
Out of what ever reason, the grub2 bootloader never installed. Boot into live mode, open terminal and execute one by one these commands to enter inside your hdd installation and install grub2 (the package name is officially grub-pc):

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

I am breaking them down to be easier to view, you just keep executing line by line:
```
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
```

```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

If during execution some error shows up, make sure you typed the command correctly. If yes, stop executing the commands and tell us exactly the error message and after which command it showed up.

If you finish all of the above without errors, restart and hopefully ubuntu will boot.

---

### Post by liamhale on 2012-03-27
> **darkod said:**
> Out of what ever reason, the grub2 bootloader never installed. Boot into live mode, open terminal and execute one by one these commands to enter inside your hdd installation and install grub2 (the package name is officially grub-pc):

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```I am breaking them down to be easier to view, you just keep executing line by line:
```
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
``````
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```If during execution some error shows up, make sure you typed the command correctly. If yes, stop executing the commands and tell us exactly the error message and after which command it showed up.

If you finish all of the above without errors, restart and hopefully ubuntu will boot.

sorry, i donot understand what it is i need to do, i have these codes, and i am currently running the live version of ubuntu, and i have terminal open. what is it i am copying and pasting one at a time and do i need any other codes that i need every time or is is just a case of copying one line then entering and then do that for the other 4 or so. if so what are the other simplfied code box's for?

sorry to be a pain, iam sure you will be glad to get rid of me :P

---

### Post by liamhale on 2012-03-27
i have managed to work out the way in wich you meant
ist box - paste all at once
2nd box - paste line by line
3rd box - paste all at once

but, i have carried this out and terminal closed itslef after last chunck of codes, and i have restarted without my hard drive and the same has happened, i have not seen any errors when terminal was executing the codes either :(
would you like me to run the boot manager again?

---

### Post by darkod on 2012-03-27
No, don't copy-paste. I think it can't work that way.

You need to type it line by line in terminal hitting Enter after each line. It needs the Enter, that's why you can't copy paste. It's not that much to type.

I also noticed another thing just now, you seem to be missing the kernel file which is the main file, so the above instructions might not work 100%, but do them anyway and later we will see if we can do something about the kernel file.

It's like the install never finished so the kernel file is missing and the bootloader never got installed.

I am wondering if it's better to simply reinstall again. It would be best if you use the manual install method, not one of the automatic ones but you don't seem to be experienced enough for it. If you can handle it, installing manually is always best because it gives you total control and in your case you are installing from a usb hdd if I understand correctly, which might be confusing the installed additionally.

Another idea is to try using a cd or usb stick if possible, but not usb hdd.

---

### Post by liamhale on 2012-03-27
> **darkod said:**
> No, don't copy-paste. I think it can't work that way.

You need to type it line by line in terminal hitting Enter after each line. It needs the Enter, that's why you can't copy paste. It's not that much to type.

I also noticed another thing just now, you seem to be missing the kernel file which is the main file, so the above instructions might not work 100%, but do them anyway and later we will see if we can do something about the kernel file.

It's like the install never finished so the kernel file is missing and the bootloader never got installed.

I am wondering if it's better to simply reinstall again. It would be best if you use the manual install method, not one of the automatic ones but you don't seem to be experienced enough for it. If you can handle it, installing manually is always best because it gives you total control and in your case you are installing from a usb hdd if I understand correctly, which might be confusing the installed additionally.

Another idea is to try using a cd or usb stick if possible, but not usb hdd.

okay i will try the writing of codes in now,
i did have a slight error, at the end of the installation it said something about a cd/dvd at the end, but i thought this was because i didnt have a cd or dvd in the disc drive it couldnt add any extra material that i assumed wasnt needed

---

### Post by umitarabul on 2013-03-13
Maybe, you also forgot a USB disk plugged, as I did. Check your boot sequence and remove any USB :)

---

### Post by coffeecat on 2013-03-13
The OP has not logged in since last July.

Back to sleep, old thread.

---

