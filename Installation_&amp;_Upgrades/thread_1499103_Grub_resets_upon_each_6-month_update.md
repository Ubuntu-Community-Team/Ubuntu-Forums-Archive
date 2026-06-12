---
title: "Grub resets upon each 6-month update"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by misetusame on 2010-06-01
Part of my default menu.lst contains the following line:
```

kernel          /boot/vmlinuz-2.6.32-22-generic root=UUID=[REMOVED_JUST_IN_CASE] ro splash xforcevesa vga=769
```

(I changed the UUID for any privacy concerns.) That [FONT=Courier New]xforcevesa vga=769[/FONT] bit causes the splash screen to show up weirdly. If I remove it, the splash screen shows just fine (in low resolution).

I had removed the [FONT=Courier New]xforcevesa vga=769[/FONT] bit before upgrading to 10.04.

My dilemma is: I chose to replace menu.lst when upgrading to 10.04. That means it removed my manual customisation. It was either that, or menu.lst wouldn't have gotten updated with the latest suggested settings. Can I remove  [FONT=Courier New]xforcevesa vga=769[/FONT] without causing any upgrade conflicts upon the next release?[FONT=Courier New]
[/FONT]

---

### Post by kansasnoob on 2010-06-01
It might help to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please DO NOT edit! We can't use your UUID's to hack your system!

But I'm guessing you have something edited in this part of the menu.lst:

> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=771 quiet

Which then writes to the boot options.

---

### Post by misetusame on 2010-06-01
Thanks.

> But I'm guessing you have something edited in this part of the menu.lst:
Ah, perhaps, but the current version is what the upgrade generated and I haven't edited it.

Here's the output:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587   6 FAT16
/dev/sda2    *        160,650     4,369,679     4,209,030   c W95 FAT32 (LBA)
/dev/sda3           4,369,680    33,672,239    29,302,560  83 Linux
/dev/sda4          33,672,240   156,248,189   122,575,950   5 Extended
/dev/sda5          33,672,303   150,143,489   116,471,187  83 Linux
/dev/sda6         150,143,553   156,248,189     6,104,637  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,065   586,067,264   586,051,200   f W95 Ext d (LBA)
/dev/sdb5              16,128   524,634,704   524,618,577  83 Linux
/dev/sdb6         524,634,768   586,051,199    61,416,432   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   390,716,864   390,716,802  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0C0B                              vfat       DellUtility                   
/dev/sda2        07D7-0C0B                              vfat       DELL UTIL                     
/dev/sda3        cb4cafb9-cd04-41bb-84ef-2764b30a463a   ext3                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b4c86252-8780-486e-a5da-47d1d9b96405   ext3                                     
/dev/sda6        602e9c87-5465-45e1-9e18-3dd2212be49c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        e3965bb9-4b7e-4221-88fd-3831bd31c10c   ext3       Mor300                        
/dev/sdb6        1AB4A2CEB4A2ABA7                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        0a02deed-c203-4e2a-9b4e-f19ba295b5e5   ext3       Documents                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda2        /windows/c               vfat       (rw,iocharset=utf8,umask=000)
/dev/sdb6        /windows/d               fuseblk    (ro,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /home                    ext3       (rw,relatime)
/dev/sdc1        /doicimeid               ext3       (rw)
/dev/sdb5        /mor                     ext3       (rw)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=5 
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\="Unidentified operating system on drive C."  

=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
timeout        2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=cb4cafb9-cd04-41bb-84ef-2764b30a463a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=splash xforcevesa vga=769

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
# howmany=1

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=cb4cafb9-cd04-41bb-84ef-2764b30a463a ro splash xforcevesa vga=769
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=cb4cafb9-cd04-41bb-84ef-2764b30a463a ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP
rootnoverify        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=cb4cafb9-cd04-41bb-84ef-2764b30a463a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b4c86252-8780-486e-a5da-47d1d9b96405 /home           ext3    relatime        0       2
# /dev/sda6
UUID=602e9c87-5465-45e1-9e18-3dd2212be49c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda2 /windows/c vfat iocharset=utf8,umask=000 0
/dev/sdb6 /windows/d ntfs users,gid=users,ro,umask=0222,utf8=true 0 0 

/dev/sdc1 /doicimeid ext3 defaults     0 2
/dev/sdb5 /mor ext3 defaults         0 2

=================== sda3: Location of files loaded by Grub: ===================


  12.9GB: boot/grub/menu.lst
  12.9GB: boot/grub/stage2
  13.6GB: boot/initrd.img-2.6.31-20-generic
  12.8GB: boot/initrd.img-2.6.32-21-generic
  15.2GB: boot/initrd.img-2.6.32-22-generic
  12.7GB: boot/vmlinuz-2.6.31-20-generic
  15.2GB: boot/vmlinuz-2.6.32-21-generic
  13.1GB: boot/vmlinuz-2.6.32-22-generic
  15.2GB: initrd.img
  12.8GB: initrd.img.old
  13.1GB: vmlinuz
  15.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  f8 44 fb ff 00 00 80 01  |.........D......|
000001c0  01 00 83 fe ff ff 3f 00  00 00 82 dd 49 17 00 00  |......?.....I...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-06-01
Your grub legacy menu.lst shows the vga setting.

Have you run into this:
vga=799 is a deprecated boot option
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)

It seems they are obsoleting vga= and using gfxpayload for grub2. It may not impact you now but eventually you will be converting.

---

### Post by kansasnoob on 2010-06-01
During upgrades have you seen "GRUB menu.lst: install the maintainer's version vs. keep the local version"?

Look here:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version)

> If you have previously modified the menu.lst  bootloader configuration for GRUB, either by hand or with a tool such as kgrubeditor, you may be asked on upgrade whether you wish to keep your local version of the menu.lst or install the package maintainer's version. This question is asked because such changes cannot be merged automatically with 100% reliability, and care is taken to not overwrite the user's manually edited bootloader configuration without warning.

However, if you choose to "keep the local version currently installed," your system will not be set up to boot from any newly-installed kernels. Manual action is required on your part to ensure that your system is running the current, security-supported kernel after upgrade. If you have local changes to your bootloader config that you want to keep, it is recommended that you follow these steps:

    * Choose "keep the local version currently installed" at the prompt.
    *

      Open /boot/grub/menu.lst with a text editor (e.g., sudo gedit /boot/grub/menu.lst).
    *

      Apply any changes you've made to the kernel boot options to the commented variables (e.g., groot, kopt, defoptions) above.
    *

      Move any manually-added boot options for other operating systems so that they are above the line

      ### BEGIN AUTOMAGIC KERNELS LIST

      or below the line

      ### END DEBIAN AUTOMAGIC KERNELS LIST

    *

      Save the file, and run sudo update-grub from the commandline.
    * Choose "install the package maintainer's version". 

For example, if you added an option i915.modeset=0 to the "kernel" line:

kernel          /vmlinuz-2.6.31-14-generic root=UUID=0e7... ro quiet splash i915.modeset=0

then add this option to kopt:

# kopt=root=UUID=0e7... ro i915.modeset=0

An updated version of the grub package will include information about this problem in the help screen for the menu.lst prompt. (470490)



Really, at some point, IMO it would be advisable to upgrade to grub 2 (but not the awful official way). I like to upgrade to grub 2 using the method in Appendix #2 here:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

But that's just my opinion.

---

