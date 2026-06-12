---
title: "GRUB2 Won't load (blinking cursor)"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by Tickeldi on 2011-11-17
Cheers,

I just installed Ubuntu 11.10 on a MSI Notebook (VR600) alongside Vista.
Sadly GRUB2 won't load. Instead all I get to see is a blinking cursor until I turn the machine of or do a warm reboot.

If I keep holding shift I get "GRUB loading." and the blinking cursor below that.

I can boot into the USB stick from which I installed Ubuntu just fine. From there I tried chrooting and reinstalling GRUB with no effect. I also used [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), no luck.

Here is the [RESULT.TXT]("http://paste.ubuntu.com/741874/") of Boot Info Script for that system. It seems to me that 
> core.img is at this location and looks      for  on this drive.should be something like
> core.img is at this location and looks      for (msdos5)/boot/grub/ on this drive.but why isn't it?

Edit: I also commented out
# GRUB_HIDDEN_TIMEOUT=00

---

### Post by oldfred on 2011-11-18
The script does not seem to show the partition with the very newest grub 1.99.  Older versions even 1.99 did work and show partition. On my boot script it does not show the partition but Ubuntu boots ok.

---

### Post by Tickeldi on 2011-11-18
I see. Still it won't boot for me. I will try to fall back on GRUB legacy to see if that brings me any luck. Will post if something explodes.

---

### Post by Rubi1200 on 2011-11-18
Install gawk in the live environment and then run the boot info script to see if it picks up on the missing information.

---

### Post by Tickeldi on 2011-11-18
I will do that.
I just tried installing GRUB Legacy and basically followed the HOWTO for that [here]("http://ubuntuforums.org/showthread.php?t=1298932").

I now have on my screen:


> GRUB Loading stage1.5.



GRUB loading, please wait...
[blinking cursor]


This is starting to get old. I have the strong feeling that this has nothing to do with GRUB2. Now going on to install gawk.

---

### Post by Tickeldi on 2011-11-18
Here the updated RESULTS.txt now with gawk and grub legacy.
Everything seems to point in the right direction.

I am pretty desperate.


Edit:
The problem obviously revolves around the fact that neither GRUB Legacy or GRUB2 can access the grub files on sda5 while booting. I assume that this must have to do with the bios on that machine. The partition to be booted is near to the end of the hd. Does that make any sense? I will create a seperate "boot" partition at the beginning of the disk and hope that this will solve the whole thing. Stay tuned ;)

---

### Post by Tickeldi on 2011-11-18
Nope. I am f****d.

---

### Post by Rubi1200 on 2011-11-18
I wouldn't have thought the position of the GRUB files should make a difference on a drive of less than 137GB (which is often where there would be a problem when BIOS couldn't see beyond that limit. 

However, why not try reinstalling GRUB using a chroot before creating a separate /boot partition?

See here for more details:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

```
                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => ISOhybrid (Syslinux 4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: /dev/sdb1 ist bereits eingehängt oder sdb1 wird gerade benutzt

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 Köpfe, 63 Sektoren/Spur, 12161 Zylinder, zusammen 195371568 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    12,290,047    12,288,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     12,290,048    83,970,047    71,680,000   7 NTFS / exFAT / HPFS
/dev/sda3          83,970,048   162,075,517    78,105,470   7 NTFS / exFAT / HPFS
/dev/sda4         162,076,670   195,371,007    33,294,338   5 Extended
/dev/sda5         162,076,672   193,292,287    31,215,616  83 Linux
/dev/sda6         193,294,336   195,371,007     2,076,672  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16013852672 bytes
19 Köpfe, 24 Sektoren/Spur, 68590 Zylinder, zusammen 31277056 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             64     1,423,959     1,423,896  17 Hidden NTFS / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        32343C3D343C05FF                       ntfs       WinRE
/dev/sda2        727206A772066FE1                       ntfs       OS_Install
/dev/sda3        CEEC4ED4EC4EB68D                       ntfs       Data
/dev/sda5        7a6e025c-b01a-4897-b6c6-8fd2e3c78d79   ext4       
/dev/sda6        def465b8-31cf-43fc-a259-160f5259e15a   swap       
/dev/sdb1                                               iso9660    Ubuntu 11.10 i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered)


=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7a6e025c-b01a-4897-b6c6-8fd2e3c78d79 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7a6e025c-b01a-4897-b6c6-8fd2e3c78d79

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.10, kernel 3.0.0-12-generic
uuid        7a6e025c-b01a-4897-b6c6-8fd2e3c78d79
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=7a6e025c-b01a-4897-b6c6-8fd2e3c78d79 ro quiet splash 
initrd        /boot/initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
uuid        7a6e025c-b01a-4897-b6c6-8fd2e3c78d79
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=7a6e025c-b01a-4897-b6c6-8fd2e3c78d79 ro  single
initrd        /boot/initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, memtest86+
uuid        7a6e025c-b01a-4897-b6c6-8fd2e3c78d79
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title         Windows Vista
root          (hd0,2)
makeactive
chainloader   +1
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7a6e025c-b01a-4897-b6c6-8fd2e3c78d79 /               ext4    errors=remount-ro 0       1
# /mnt/C was on /dev/sda2 during installation
UUID=727206A772066FE1 /mnt/C          ntfs    defaults,umask=007,gid=46 0       0
# /mnt/D was on /dev/sda3 during installation
UUID=CEEC4ED4EC4EB68D /mnt/D          ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=def465b8-31cf-43fc-a259-160f5259e15a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  89.559452057 = 96.163729408   boot/grub/menu.lst                             1
  89.541858673 = 96.144838656   boot/grub/stage2                               1
  78.671863556 = 84.473270272   boot/initrd.img-3.0.0-12-generic               2
  89.484764099 = 96.083533824   boot/vmlinuz-3.0.0-12-generic                  1
  78.671863556 = 84.473270272   initrd.img                                     2
  89.484764099 = 96.083533824   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ec cf ab 2a 92 4d 61 f8  d8 eb b7 e6 be a9 ad f4  |...*.Ma.........|
00000010  44 87 43 22 6a 85 79 70  30 a3 4f de 96 e1 c5 6c  |D.C"j.yp0.O....l|
00000020  9c 3f db 1a 42 bd 91 e8  88 5b e7 d6 6e 19 dd e4  |.?..B....[..n...|
00000030  f4 f7 73 12 1a f5 a9 60  e0 13 7f ce 46 51 f5 5c  |..s....`....FQ.\|
00000040  4c af 0b 0a f2 2d c1 d8  38 cb 17 c6 1e 89 0d d4  |L....-..8.......|
00000050  a4 67 a3 02 ca 65 d9 50  90 83 af be f6 c1 25 4c  |.g...e.P......%L|
00000060  fc 1f 3b fa a2 9d f1 c8  e8 3b 47 b6 ce f9 3d c4  |..;......;G...=.|
00000070  54 d7 d3 f2 7a d5 09 40  40 f3 df ae a6 31 55 3c  |T...z..@@....1U<|
00000080  ac 8f 6b ea 52 0d 21 b8  98 ab 77 a6 7e 69 6d b4  |..k.R.!...w.~im.|
00000090  04 47 03 e2 2a 45 39 30  f0 63 0f 9e 56 a1 85 2c  |.G..*E90.c..V..,|
000000a0  5c ff 9b da 02 7d 51 a8  48 1b a7 96 2e d9 9d a4  |\....}Q.H.......|
000000b0  b4 b7 33 d2 da b5 69 20  a0 d3 3f 8e 06 11 b5 1c  |..3...i ..?.....|
000000c0  0c 6f cb ca b2 ed 81 98  f8 8b d7 86 de 49 cd 94  |.o...........I..|
000000d0  64 27 63 c2 8a 25 99 10  50 43 6f 7e b6 81 e5 0c  |d'c..%..PCo~....|
000000e0  bc df fb ba 62 5d b1 88  a8 fb 07 76 8e b9 fd 84  |....b].....v....|
000000f0  14 97 93 b2 3a 95 c9 00  00 b3 9f 6e 66 f1 15 fc  |....:......nf...|
00000100  6c 4f 2b aa 12 cd e1 78  58 6b 37 66 3e 29 2d 74  |lO+....xXk7f>)-t|
00000110  c4 07 c3 a2 ea 05 f9 f0  b0 23 cf 5e 16 61 45 ec  |.........#.^.aE.|
00000120  1c bf 5b 9a c2 3d 11 68  08 db 67 56 ee 99 5d 64  |..[..=.h..gV..]d|
00000130  74 77 f3 92 9a 75 29 e0  60 93 ff 4e c6 d1 75 dc  |tw...u).`..N..u.|
00000140  cc 2f 8b 8a 72 ad 41 58  b8 4b 97 46 9e 09 8d 54  |./..r.AX.K.F...T|
00000150  24 e7 23 82 4a e5 59 d0  10 03 2f 3e 76 41 a5 cc  |$.#.J.Y.../>vA..|
00000160  7c 9f bb 7a 22 1d 71 48  68 bb c7 36 4e 79 bd 44  ||..z".qHh..6Ny.D|
00000170  d4 57 53 72 fa 55 89 c0  c0 73 5f 2e 26 b1 d5 bc  |.WSr.U...s_.&...|
00000180  2c 0f eb 6a d2 8d a1 38  18 2b f7 26 fe e9 ed 34  |,..j...8.+.&...4|
00000190  84 c7 83 62 aa c5 b9 b0  70 e3 8f 1e d6 21 05 ac  |...b....p....!..|
000001a0  dc 7f 1b 5a 82 fd d1 28  c8 9b 27 16 ae 59 1d 24  |...Z...(..'..Y.$|
000001b0  34 37 b3 52 5a 35 e9 a0  20 53 bf 0e 86 91 00 fe  |47.RZ5.. S......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 50 dc 01 00 fe  |...........P....|
000001d0  ff ff 05 fe ff ff 02 57  dc 01 00 b1 1f 00 00 00  |.......W........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb1

00000000  01 43 44 30 30 31 01 00  20 20 20 20 20 20 20 20  |.CD001..        |
00000010  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
00000020  20 20 20 20 20 20 20 20  55 62 75 6e 74 75 20 31  |        Ubuntu 1|
00000030  31 2e 31 30 20 69 33 38  36 20 20 20 20 20 20 20  |1.10 i386       |
00000040  20 20 20 20 20 20 20 20  00 00 00 00 00 00 00 00  |        ........|
00000050  96 6e 05 00 00 05 6e 96  00 00 00 00 00 00 00 00  |.n....n.........|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  01 00 00 01 01 00 00 01  |................|
00000080  00 08 08 00 f2 02 00 00  00 00 02 f2 5f 00 00 00  |............_...|
00000090  00 00 00 00 00 00 00 60  00 00 00 00 22 00 23 00  |.......`....".#.|
000000a0  00 00 00 00 00 23 00 08  00 00 00 00 08 00 6f 0a  |.....#........o.|
000000b0  0c 0f 0f 29 00 02 00 00  01 00 00 01 01 00 20 20  |...)..........  |
000000c0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
000001b0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 58 4f  |              XO|
000001c0  52 52 49 53 4f 2d 31 2e  30 2e 38 20 32 30 31 31  |RRISO-1.0.8 2011|
000001d0  2e 30 34 2e 31 34 2e 30  37 33 30 30 31 2c 20 4c  |.04.14.073001, L|
000001e0  49 42 49 53 4f 42 55 52  4e 2d 31 2e 30 2e 38 2c  |IBISOBURN-1.0.8,|
000001f0  20 4c 49 42 49 53 4f 46  53 2d 31 2e 30 2e 38 2c  | LIBISOFS-1.0.8,|
00000200
```

---

### Post by oldfred on 2011-11-18
Have not seen old grub legacy & menu.lst for ages. How did you install it. From a chroot into Ubuntu, whcih should work? 

Old versions of grub .97 do not work with ext4 partitions, so it has to be from a version since 9.04 as that was when Ubuntu started using ext4.

---

### Post by Tickeldi on 2011-11-20
> **oldfred said:**
> Have not seen old grub legacy & menu.lst for ages. How did you install it. From a chroot into Ubuntu, whcih should work? 

Old versions of grub .97 do not work with ext4 partitions, so it has to be from a version since 9.04 as that was when Ubuntu started using ext4.

Yes I chrooted into the installed system, deinstalled grub2, a message warning me that my system is now unbootable appeared, then I installed the package "grub" and grub-installed it into the MBR. I wasn't aware of its incompatibility to ext4 though. In any case, it didn't work.

I reinstalled GRUB2 via chroot many times. Sorry I didn't state that before but thats how I did it. I actually come from gentoo so I know how to use the terminal and how to chroot into a system.

I also tried a GRUB rescue cd (rescatux) and bootrepair.

I did a backup of the whole disk so I am grateful for any ideas.

---

### Post by Tickeldi on 2011-11-20
wow

I just got it to work. As I said I have a backup of the whole disk so I just killed the whole thing and made a solo install of ubuntu. That did it. I still don't know why it didn't work before though.

Now I just have to do perform a bit of partition dancing. I guess I'll have to reinstall windows which will [word I learned I am not even allowed to hint at here] the MBR again. So uh. Wish me luck and many many thanks to you for your support.

---

### Post by Rubi1200 on 2011-11-20
Glad you got things sorted out in the end :)

Please mark this Solved using the Thread Tools near the top of the page.

---

