---
title: "Can't boot after upgrade to Lucid"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by JohnCaver on 2010-05-13
Hi,

I have a dual boot system with Win XP and Ubuntu (using grub boot menu).
I recently upgraded my Ubuntu from 9.04 (Jaunty) to 10.04 (Lucid)
and now I cannot boot into Ubuntu - I just get a desktop with no icons or disk activity.
I think this may have something to do with the fact that I answered 'no' when asked whether to replace my menu.1st file, and possibly some others. So my boot menu still refers to 9.04.
Can someone please help me to get it working again?

Thanks

---

### Post by darkod on 2010-05-13
9.04 shouldn't have a direct upgrade to 10.04. You can upgrade to 10.04 from 9.10 or 8.04 LTS.

Anyway, to have a better look please download the script in my signature, move it on desktop for example, and execute it in terminal with:

sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. Post the content of that file and for easier reading wrap it in CODE tags (with the text selected hit the # button in the toolbar above when creating the post).

If your ubuntu doesn't work you can do all of this from live mode.

Also, it sounds like the actual boot process is fine, because it starts ubuntu, but maybe the upgrade went wrong and you don't get your fully working desktop.

---

### Post by JohnCaver on 2010-05-13
Thanks darkod, but how can I run your script if I can't boot into Ubuntu?
Do I need to boot from a live CD and then run it?

---

### Post by darkod on 2010-05-13
Yes, live mode (Try Ubuntu) is enough.

---

### Post by JohnCaver on 2010-05-15
Here are the contents of results.txt:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   123,636,239   123,636,177   7 HPFS/NTFS
/dev/sda2         123,636,240   625,137,344   501,501,105   f W95 Ext d (LBA)
/dev/sda5         123,636,303   274,101,029   150,464,727   7 HPFS/NTFS
/dev/sda6         274,101,093   625,137,344   351,036,252   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   115,121,789   115,121,727  83 Linux
/dev/sdb2         115,121,790   240,107,489   124,985,700   f W95 Ext d (LBA)
/dev/sdb5         115,121,853   177,614,639    62,492,787   b W95 FAT32
/dev/sdb6         177,614,703   236,203,694    58,588,992   b W95 FAT32
/dev/sdb7         236,203,758   240,107,489     3,903,732  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
126 heads, 63 sectors/track, 1973 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    15,661,673    15,661,611   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1                                               ntfs                                     
/dev/sda5                                               ntfs                                     
/dev/sda6                                               ntfs                                     
/dev/sdb1        e42d6b30-5293-4a6b-810d-7c28601b772f   ext3                                     
/dev/sdb5        A8FA-98E7                              vfat       PROGRAMS                      
/dev/sdb6        F8FB-33F3                              vfat       MEDIA                         
/dev/sdb7        9d1e510b-60df-4f9b-ab09-f2ed2d2e1caf   swap                                     
/dev/sdc1        0000-0000                              vfat       UNTITLED                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/bus/usb     /proc/bus/usb            none       (rw,bind)
/dev/sdc1        /media/UNTITLED          vfat       (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

================================ sda1/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=e42d6b30-5293-4a6b-810d-7c28601b772f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e42d6b30-5293-4a6b-810d-7c28601b772f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e42d6b30-5293-4a6b-810d-7c28601b772f ro  single
initrd        /boot/initrd.img-2.6.31-14-generic



title        Ubuntu 9.10, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=e42d6b30-5293-4a6b-810d-7c28601b772f / ext3 defaults,errors=remount-ro,relatime 0 1
# Entry for /dev/sda1 :
UUID=CC8C1FCA8C1FADC8 /media/sda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
# Entry for /dev/sda5 :
UUID=131AB78C05999669 /media/sda5 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
# Entry for /dev/sda6 :
UUID=4C6ADE347556A084 /media/sda6 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
# Entry for /dev/sdb5 :
UUID=A8FA-98E7 /media/sdb5 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sdb6 :
UUID=F8FB-33F3 /media/sdb6 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sdb7 :
UUID=9d1e510b-60df-4f9b-ab09-f2ed2d2e1caf none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  49.9GB: boot/grub/menu.lst
  50.0GB: boot/grub/stage2
  50.0GB: boot/initrd.img-2.6.20-16-generic
  49.9GB: boot/initrd.img-2.6.20-16-generic.bak
  50.0GB: boot/initrd.img-2.6.22-14-generic
  50.0GB: boot/initrd.img-2.6.22-14-generic.bak
  50.0GB: boot/initrd.img-2.6.24-22-generic
  50.0GB: boot/initrd.img-2.6.24-22-generic.bak
  49.9GB: boot/initrd.img-2.6.27-14-generic
  49.9GB: boot/initrd.img-2.6.28-14-generic
  50.0GB: boot/initrd.img-2.6.31-14-generic
  50.0GB: boot/initrd.img-2.6.32-22-generic
  49.9GB: boot/vmlinuz-2.6.20-16-generic
  49.9GB: boot/vmlinuz-2.6.22-14-generic
  49.9GB: boot/vmlinuz-2.6.24-22-generic
  49.9GB: boot/vmlinuz-2.6.27-14-generic
  50.0GB: boot/vmlinuz-2.6.28-14-generic
  49.9GB: boot/vmlinuz-2.6.31-14-generic
  49.9GB: boot/vmlinuz-2.6.32-22-generic
  50.0GB: initrd.img
  49.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

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
000001b0  00 00 00 00 00 00 00 00  f6 fd ff 03 00 00 00 01  |................|
000001c0  01 00 83 fe ff ff 3f 00  00 00 3f 9e dc 06 00 00  |......?...?.....|
000001d0  c1 ff 0f fe ff ff 7e 9e  dc 06 64 21 73 07 00 00  |......~...d!s...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Any help appreciated, thanks.

---

### Post by darkod on 2010-05-15
Yes, the upgrade left grub1 because by default it doesn't upgrade it to grub2. But it should have still worked. I haven't done the upgrade process, but from what I can see it seems when you answered not to update the menu.lst it didn't make an entry for 10.40. Look in the middle of the results file, where the content of /dev/sdb1/boot/grub/menu.lst is:

> 
title        Ubuntu [COLOR=Red]9.10[/COLOR], kernel 2.6.31-14-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e42d6b30-5293-4a6b-810d-7c28601b772f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu [COLOR=Red]9.10[/COLOR], kernel 2.6.31-14-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e42d6b30-5293-4a6b-810d-7c28601b772f ro  single
initrd        /boot/initrd.img-2.6.31-14-generic


No 10.04. This is a characteristic of grub1 and menu.lst, in a lot of situations you need to add stuff manually. But lets first sort the boot process, and we can think about upgrading it to grub2 later, not in the same step because if it fails we don't know what failed exactly.

Above these two entries I quoted, you just need to insert a new entry. The full filename of the kernel you need to use is at the bottom of the results file, in the full list of kernels it can find:

> 
49.9GB: boot/grub/menu.lst
  50.0GB: boot/grub/stage2
  50.0GB: boot/initrd.img-2.6.20-16-generic
  49.9GB: boot/initrd.img-2.6.20-16-generic.bak
  50.0GB: boot/initrd.img-2.6.22-14-generic
  50.0GB: boot/initrd.img-2.6.22-14-generic.bak
  50.0GB: boot/initrd.img-2.6.24-22-generic
  50.0GB: boot/initrd.img-2.6.24-22-generic.bak
  49.9GB: boot/initrd.img-2.6.27-14-generic
  49.9GB: boot/initrd.img-2.6.28-14-generic
  50.0GB: boot/initrd.img-2.6.31-14-generic
  50.0GB: [COLOR=Red]boot/initrd.img-2.6.32-22-generic[/COLOR]
  49.9GB: boot/vmlinuz-2.6.20-16-generic
  49.9GB: boot/vmlinuz-2.6.22-14-generic
  49.9GB: boot/vmlinuz-2.6.24-22-generic
  49.9GB: boot/vmlinuz-2.6.27-14-generic
  50.0GB: boot/vmlinuz-2.6.28-14-generic
  49.9GB: boot/vmlinuz-2.6.31-14-generic
  49.9GB: [COLOR=Red]boot/vmlinuz-2.6.32-22-generic[/COLOR]
  50.0GB: initrd.img
  49.9GB: vmlinuz


So, the entry for 10.04 you need to insert above the 9.10 entries will look like:

title        Ubuntu 10.04, kernel 2.6.32-22-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=e42d6b30-5293-4a6b-810d-7c28601b772f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

You should be able to edit menu.lst from the live mode, open your root partition in Places, it will probably be shown as 60GB filesystem, click on it. Then browse to boot/grub and insert this entry in menu.lst file. Save and close the file.

Reboot and see if you will have the new 10.04 in the grub menu and whether it works fine.

---

### Post by frantid on 2010-05-15
edit:  darkod beat me to it.  :)  if you want to do it in grub.

when you boot into grub, highlight the lucid entry and press "e"

you need to make it look like this:

```
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=e42d6b30-5293-4a6b-810d-7c28601b772f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
```I believe 2.6.32.22 is the default kernel.  then it's "b" to boot.  the directions should be at the bottom of the grub screen.

---

### Post by JohnCaver on 2010-05-16
Thanks - this has got my boot menu sorted out, I now have the 10.04 option.

However, something is still wrong - the OS will not boot properly. I get a mouse pointer, and sometimes a background, but no taskbar or icons. There is short sporadic disk activity.

What should I do now - is a reinstall the best option, and how do I do that?

Thanks again.

---

### Post by deeaa on 2010-05-16
hi everybody 
i face the same prob. but not exactly because 

my menuentries

```
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows 7 (loader) (on /dev/sda2)" {

```

uname -a:
```
Linux mostafa-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux
```

sub of _menu.lst_:

```
## ## End Default Options ##

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		698ae635-d9c3-4d40-975b-b9de76c77ff3
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=698ae635-d9c3-4d40-975b-b9de76c77ff3 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		698ae635-d9c3-4d40-975b-b9de76c77ff3
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=698ae635-d9c3-4d40-975b-b9de76c77ff3 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-16-generic
uuid		698ae635-d9c3-4d40-975b-b9de76c77ff3
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=698ae635-d9c3-4d40-975b-b9de76c77ff3 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-16-generic (recovery mode)
uuid		698ae635-d9c3-4d40-975b-b9de76c77ff3
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=698ae635-d9c3-4d40-975b-b9de76c77ff3 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Chainload into GRUB 2
root		698ae635-d9c3-4d40-975b-b9de76c77ff3
kernel		/boot/grub/core.img

title		Ubuntu 10.04 LTS, memtest86+
uuid		698ae635-d9c3-4d40-975b-b9de76c77ff3
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I tried to : update-grub 
             reinstall kernel 2.6.32-22-generic
             grub-set-default to 0
& every thing I could do


I don't know what is wrong

---

### Post by wilee-nilee on 2010-05-16
@deeaa you need to start your own thread and post the script in darkod's signature at the top of the thread. I would do it shortly since now is the time across the day that the people who can help you are on line.

---

