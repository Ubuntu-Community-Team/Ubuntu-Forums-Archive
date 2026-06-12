---
title: "What's my 'Mount Point? (upgrade multi-boot)"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2009-12-30
How do I tell which partition is CURRENTLY my ROOT, and HOME partitions?

I chose 'Specify partitions manually', Install to the partition that NOW has Ubuntu, format to ext4,

BUT...

what is my current Mount Point?  '/' ?  '/boot' ?  '/home'  ?

I'm trying to keep the GRUB loader as it is now...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141814&d=1262217472[/IMG]

---

### Post by presence1960 on 2009-12-30
you need to know that info before you start the install. The installer will not tell you any of that. Once you know what your / is, /home is etc (such as /home is sda2 and / is sda1) then you can highlight those partitions and use the window in your screenshot to configure the new install like this:

**_for / _**
Use as: ext3 or ext4
tick the format box
mount point : use the drop down box to select /

**_for /home_**
Use as : ext3 or ext4
***leave format box unticked*** or you will format your /home partition and lose all data
mount point : use drop down box to select /home

Again you need to know which partition is what prior to using the partitioner when installing or you may experience data loss.

**Note:** Above I only used sda1 and sda2 as examples, I was not referring to your partition table in the screenshot!

---

### Post by Moozillaaa on 2009-12-30
> **presence1960 said:**
> you need to know that info before you start the install. !

So if I don't know now, is there any way to find out?

---

### Post by presence1960 on 2009-12-30
> **Moozillaaa said:**
> So if I don't know now, is there any way to find out?

If you currently have a working Ubuntu on your machine do this: Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

If you don't currently have a working Ubuntu installed then do this: Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

That will give us plenty of info about your setup.

---

### Post by Moozillaaa on 2009-12-30
Code TAGS??? 

Don't you like all those little smiley faces? :lolflag:

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => HP/Gateway is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 27459018 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #4 for 
                       /boot/grub/grub.conf.
    Operating System:  Fedora release 10 (Cambridge) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 132472595 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  PCLinuxOS release 2007 
                       (PCLinuxOS) for i586 Kernel 2.6.18.8.tex5 on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b36bdea

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    25,607,609    25,607,547   7 HPFS/NTFS
/dev/sda2          50,122,800   173,003,984   122,881,185  83 Linux
/dev/sda3         173,003,985   234,436,544    61,432,560   5 Extended
/dev/sda5         173,004,048   189,374,219    16,370,172  83 Linux
/dev/sda6         226,853,928   234,436,544     7,582,617  82 Linux swap / Solaris
/dev/sda7         189,374,283   197,551,304     8,177,022  82 Linux swap / Solaris
/dev/sda8         197,551,368   226,853,864    29,302,497  83 Linux
/dev/sda4          25,607,610    50,122,799    24,515,190  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x393115b2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   128,327,219   128,327,157   7 HPFS/NTFS
/dev/sdb2         217,288,704   234,432,511    17,143,808   7 HPFS/NTFS
/dev/sdb3         128,327,220   169,341,164    41,013,945   5 Extended
/dev/sdb5         128,327,283   169,341,164    41,013,882  83 Linux
/dev/sdb4         169,341,165   203,125,859    33,784,695  83 Linux


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="D6AC129BF4974A14" TYPE="ntfs" 
sda2: UUID="cbf87cd3-0a1f-40cd-8fe8-dbc4adc13ba5" TYPE="ext3" 
sda6: UUID="5cc048de-889c-4a1c-ab56-45c1e2933d6d" TYPE="swap" 
sda7: UUID="ad886fc1-dcb3-4c66-b627-2b59da7500eb" TYPE="swap" 
sda4: LABEL="/" UUID="e167cb3e-f1fc-4852-804a-a22457aece41" SEC_TYPE="ext2" TYPE="ext3" 
sdb1: UUID="FEFEB4A2FEB4549D" TYPE="ntfs" 
sdb2: UUID="10FCA6F2FCA6D0F0" LABEL="HP_RECOVERY" TYPE="ntfs" 
sdb5: UUID="0b8d1aab-414a-4f4e-9e53-8a515ad426e6" TYPE="ext2" 
sdb4: UUID="b41368bf-9c87-48fc-ab6f-191cadc42e45" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw,relatime)
/dev/sdb2 on /media/HP_RECOVERY type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /home/chuckbhp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chuckbhp)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sda2/boot/grub/menu.lst: ===========================

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
#      password --md5 **WOULDNTYALIKETOKNOW???**
# password** IBETYOUWOULD!!!**

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
# kopt=root=UUID=cbf87cd3-0a1f-40cd-8fe8-dbc4adc13ba5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=quiet splash noapic irqpoll noirqdebug

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

title        Ubuntu 8.04.2, kernel 2.6.24-21-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=cbf87cd3-0a1f-40cd-8fe8-dbc4adc13ba5 ro quiet splash noapic irqpoll noirqdebug
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=cbf87cd3-0a1f-40cd-8fe8-dbc4adc13ba5 ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.2, kernel 2.6.24-19-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cbf87cd3-0a1f-40cd-8fe8-dbc4adc13ba5 ro quiet splash noapic irqpoll noirqdebug
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cbf87cd3-0a1f-40cd-8fe8-dbc4adc13ba5 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

title           FC8
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.26.8-57.fc8
initrd          /boot/initrd-2.6.26.8-57.fc8.img

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        XPPro
root        (hd0,0)
savedefault
makeactive
chainloader    +1

title           Windows Vista
root            (hd1,0)
savedefault
makeactive
chainloader     +1

title           PCLOS
kernel          (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb5  acpi=on resume=/dev/sda7 splash=silent vga=788
initrd          (hd1,4)/boot/initrd.img

title           PCLOS GRUBloader
root            (hd1,4)
configfile      /boot/grub/menu.lst





=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=cbf87cd3-0a1f-40cd-8fe8-dbc4adc13ba5 / ext3 defaults,errors=remount-ro,relatime 0 1
# Entry for /dev/sda5 :
UUID=5d2bf2d9-24c2-466f-9ee3-1dfd2e97c30e none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/sdb2 /media/HP_RECOVERY ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/disk ntfs-3g defaults,locale=en_UTF-8 0 0


=================== sda2: Location of files loaded by Grub: ===================


  26.9GB: boot/grub/menu.lst
  25.8GB: boot/grub/stage2
  28.5GB: boot/initrd.img-2.6.24-21-generic
  25.8GB: boot/initrd.img-2.6.24-21-generic.bak
  80.8GB: boot/initrd.img-2.6.28-17-generic
  25.8GB: boot/vmlinuz-2.6.24-21-generic
  80.8GB: boot/vmlinuz-2.6.28-17-generic
  80.8GB: initrd.img
  80.8GB: vmlinuz

=============================== sda4/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sda5               swap                    swap    defaults        0 0

=================== sda4: Location of files loaded by Grub: ===================


  14.0GB: boot/grub/stage2
  16.5GB: boot/initrd-2.6.26.8-57.fc8.img
  16.2GB: boot/initrd-2.6.27.19-170.2.35.fc10.i686.img
  16.6GB: boot/initrd-2.6.27.21-170.2.56.fc10.i686.img
  16.5GB: boot/vmlinuz-2.6.26.8-57.fc8
  16.2GB: boot/vmlinuz-2.6.27.19-170.2.35.fc10.i686
  16.3GB: boot/vmlinuz-2.6.27.21-170.2.56.fc10.i686

=========================== sdb5/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,4)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title PCLOS
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb5  acpi=on resume=/dev/sda7 splash=silent vga=788
initrd (hd1,4)/boot/initrd.img

title linux-nonfb
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sdb5  acpi=on resume=/dev/sda7
initrd (hd1,4)/boot/initrd.img

title failsafe
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sdb5  failsafe acpi=on resume=/dev/sda7
initrd (hd1,4)/boot/initrd.img

title XPPro
root (hd0,0)
makeactive
chainloader +1

title Vista
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title HP Vista Recovery
root (hd1,1)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

=============================== sdb5/etc/fstab: ===============================

## fstab created by Livecd-install 

none    /proc    proc    defaults    0 0
none    /dev/pts    devpts    mode=0620    0 0
none    /proc/bus/usb    usbfs    defaults    0 0

# cdrom: TSSTcorpCD/DVDW TS-L632M
#    /dev/hda    /mnt/cdrom    auto    user,exec,ro,noauto    0 0

# /dev/sda1, size=25607547, type=7: NTFS (primary)
/dev/sda1    /mnt/win_c    ntfs    user,exec,ro,noauto,nls=utf8,umask=0    0 0

# /dev/sda2, size=122881185, type=131: Journalised FS: ext3 (primary)
/dev/sda2    /mnt/sda2    ext3    user,exec,rw,noauto    0 0

# /dev/sda4, size=24515190, type=131: Journalised FS: ext3 (primary)
/dev/sda4    /mnt/sda4    ext3    user,exec,rw,noauto    0 0

# /dev/sda5, size=16370172, type=131: Linux native (extended)
/dev/sda5    /mnt/sda5    ext2    user,exec,rw,noauto    0 0

# /dev/sda6, size=7582617, type=130: Linux swap (extended)
/dev/sda6 swap swap defaults 0 0

# /dev/sda7, size=8177022, type=130: Linux swap (extended)
/dev/sda7 swap swap defaults 0 0

# /dev/sda8, size=29302497, type=131: Linux native (extended)
/dev/sda8    /mnt/sda8    ext2    user,exec,rw,noauto    0 0

# /dev/sdb1, size=128319425, type=7: NTFS (primary)
/dev/sdb1    /mnt/win_d    ntfs    user,exec,ro,noauto,nls=utf8,umask=0    0 0

# /dev/sdb2, size=17143808, type=7: NTFS (primary)
/dev/sdb2    /mnt/win_e    ntfs    user,exec,ro,noauto,nls=utf8,umask=0    0 0

# /dev/sdb5, size=41013882, type=131: Linux native (extended)
/dev/sdb5 / ext2 noatime 1 1

=================== sdb5: Location of files loaded by Grub: ===================


  67.7GB: boot/grub/menu.lst
  67.8GB: boot/grub/stage2
  67.7GB: boot/initrd-2.6.18.8.tex5.img
  67.7GB: boot/initrd.img
  67.7GB: boot/vmlinuz
  67.7GB: boot/vmlinuz-2.6.18.8.tex5
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  6b 58 d3 77 44 4c 00 bd  06 f7 0c 71 bf b6 3f 77  |kX.wDL.....q..?w|
00000010  5e 32 79 8e 08 3a 92 2f  06 61 e2 e8 94 51 3b 0f  |^2y..:./.a...Q;.|
00000020  c6 57 5a 19 4f b4 a3 df  5b 68 66 0e ad 22 6b 67  |.WZ.O...[hf.."kg|
00000030  f6 1c ff 70 16 36 08 ca  c2 e1 2e 7a 36 b6 30 8b  |...p.6.....z6.0.|
00000040  45 38 c6 c8 5c c8 dc 76  e3 70 09 bc c6 ff ee 8d  |E8..\..v.p......|
00000050  43 78 0e f5 5f e6 e2 58  18 ef f3 2c 40 50 63 29  |Cx.._..X...,@Pc)|
00000060  48 04 b2 00 6f e1 2f 45  5d e4 4d c7 22 0c 31 5a  |H...o./E].M.".1Z|
00000070  f3 b3 87 f6 fe e7 27 75  13 33 b0 e9 a2 9b 23 f3  |......'u.3....#.|
00000080  09 e8 b9 d7 b9 17 81 cc  8e e3 22 90 34 d2 09 2c  |..........".4..,|
00000090  7a 8f bd 8c db f0 41 79  7b 38 8b 6e ab 73 67 a0  |z.....Ay{8.n.sg.|
000000a0  9d d9 24 a4 99 38 6e 20  a4 3a 75 4b b1 ff 02 3b  |..$..8n .:uK...;|
000000b0  bb 9b ca 65 9a e6 7f b4  9a 86 7c c4 5b 61 34 02  |...e......|.[a4.|
000000c0  ba 51 f8 2e 9d fc b6 21  99 77 fa ec 02 92 d0 ab  |.Q.....!.w......|
000000d0  08 4d 57 d7 07 1e 2d 80  fc 03 18 a5 f7 2e 0c 80  |.MW...-.........|
000000e0  f4 68 bd 97 af e2 98 8e  4b 89 4b bd 37 cb 52 40  |.h......K.K.7.R@|
000000f0  24 3d 19 c4 41 18 45 71  1c 0d 70 0a 06 5d 82 e3  |$=..A.Eq..p..]..|
00000100  20 f5 61 1b 9a 4e 3e be  fa 1c 1c 79 e2 cc 23 a2  | .a..N>....y..#.|
00000110  f0 ef da af 79 d2 ce 70  01 0b 9a e9 19 0a 20 73  |....y..p...... s|
00000120  e8 ac ea 17 90 e8 68 e0  7e 66 aa c5 d5 d1 ad 0e  |......h.~f......|
00000130  20 c4 a9 b1 4e 95 bd c6  7d 41 08 bc ca 78 89 cd  | ...N...}A...x..|
00000140  8b 96 6e eb 7f 42 cd b6  77 33 3f 46 f1 82 93 46  |..n..B..w3?F...F|
00000150  e0 82 34 92 71 44 e5 64  84 d1 d6 53 28 fe 60 a8  |..4.qD.d...S(.`.|
00000160  74 db 12 59 b1 5b 7b 75  e0 02 42 78 84 04 73 7b  |t..Y.[{u..Bx..s{|
00000170  27 24 7a d3 f6 f9 ab 66  35 a8 86 88 7b c9 c8 6c  |'$z....f5...{..l|
00000180  2f 4b e1 66 3e 45 cc ec  f7 74 10 6b c1 b5 cb 1a  |/K.f>E...t.k....|
00000190  c7 a0 69 af 5d 6f e1 a3  0d f2 12 60 70 54 fb f1  |..i.]o.....`pT..|
000001a0  d5 31 c1 a8 cb a4 33 c4  fe 9a b7 10 43 7c b6 84  |.1....3.....C|..|
000001b0  9f d3 c8 67 8a 3e 6a d2  83 90 48 ff 55 13 5d 0f  |...g.>j...H.U.].|
000001c0  ec 68 6c b9 bd 6b fd 58  4b d6 19 bb d7 97 7a 43  |.hl..k.XK.....zC|
000001d0  64 26 6d 17 56 06 64 2e  30 96 06 d1 57 46 44 e0  |d&m.V.d.0...WFD.|
000001e0  c1 8b 75 89 47 00 5c eb  af 92 9b 8c c9 c5 de 91  |..u.G.\.........|
000001f0  55 fc f1 2e 43 77 93 24  99 bf 56 7d d5 3b f1 5b  |U...Cw.$..V}.;.[|
00000200

Unknown BootLoader  on sda8

00000000  1e ae 81 2d ad e3 0e 40  a4 7d 98 53 3d 83 39 6f  |...-...@.}.S=.9o|
00000010  a1 d7 78 b0 17 7c b7 a4  77 a9 d6 42 b6 21 24 1a  |..x..|..w..B.!$.|
00000020  d1 b2 2a d4 68 83 e4 fd  e0 cf 7c a8 ca 21 37 2d  |..*.h.....|..!7-|
00000030  8d b1 50 dc b3 e4 87 c0  2e e5 2f f3 71 d2 6b 1c  |..P......./.q.k.|
00000040  ba 3b 87 7f dd 1d 25 12  de a7 4e 58 46 a2 50 c5  |.;....%...NXF.P.|
00000050  20 a2 42 c5 ff 9a 5f 75  67 59 0e e9 9b 5f 39 51  | .B..._ugY..._9Q|
00000060  87 07 87 59 ac 5e 1f 0d  d5 e8 7c b3 85 45 a9 72  |...Y.^....|..E.r|
00000070  4b 92 72 72 4a 62 9f b4  1b 5a b6 f0 3c 63 e1 ee  |K.rrJb...Z..<c..|
00000080  0d 2a f6 5c 76 00 4e 5b  f1 51 4d f0 95 18 4f 5e  |.*.\v.N[.QM...O^|
00000090  9c c4 b9 5e 6b 6c 7a 55  4f e5 94 25 93 6d 01 c3  |...^klzUO..%.m..|
000000a0  db 7a 0d 97 90 bb e8 32  77 01 7c fe 6a 39 9b 5c  |.z.....2w.|.j9.\|
000000b0  08 48 32 b6 f2 6e f7 7a  bc 4a 66 9c b8 23 d4 64  |.H2..n.z.Jf..#.d|
000000c0  b8 a9 74 99 ba 90 29 be  c4 ea af 14 36 a7 88 9e  |..t...).....6...|
000000d0  80 50 ca a4 a6 32 c5 b7  30 d7 d6 00 46 8b b4 1d  |.P...2..0...F...|
000000e0  75 f9 32 9f 5b b9 34 69  20 4d 34 ba ae 6a 3e 82  |u.2.[.4i M4..j>.|
000000f0  4d c6 35 72 17 f4 35 60  17 d8 08 24 cf c8 5e 12  |M.5r..5`...$..^.|
00000100  09 20 62 7f e1 ba ab 16  00 ab 9d 13 1e ce b6 0c  |. b.............|
00000110  f1 ea 63 1c d8 5b b9 d7  c1 97 1c c5 20 db 3f 59  |..c..[...... .?Y|
00000120  15 f3 6f e9 8d 08 99 3f  96 88 96 84 e7 d6 92 e4  |..o....?........|
00000130  09 b5 88 33 eb 37 49 be  06 fc 4b 59 50 69 f6 f4  |...3.7I...KYPi..|
00000140  65 b0 2e ae 78 58 56 81  88 04 ce 76 7c ef f5 3b  |e...xXV....v|..;|
00000150  95 cc bc c0 43 12 d4 d2  20 81 07 2c b3 10 b2 79  |....C... ..,...y|
00000160  88 9b c7 1e 03 7f 31 04  82 b7 e5 8e d8 08 03 21  |......1........!|
00000170  c9 9f 32 66 61 c1 ee ab  cb e5 48 b4 43 e8 0f 85  |..2fa.....H.C...|
00000180  48 33 f0 39 66 13 18 fd  97 dd 5d 4b 57 ca 44 4e  |H3.9f.....]KW.DN|
00000190  ce 10 6e 7d 83 4c 4c f2  dc 62 e4 99 60 11 05 96  |..n}.LL..b..`...|
000001a0  6d 0b e4 4f a9 81 33 e8  c2 7b 47 01 f1 83 16 ca  |m..O..3..{G.....|
000001b0  8b 87 eb a0 d4 1b ad ae  ab da b8 0f c5 12 97 65  |...............e|
000001c0  ee e4 91 10 a7 f8 09 77  4b 8f 99 09 d6 92 16 b9  |.......wK.......|
000001d0  59 56 7f 1b 60 54 10 4d  9f 1c 59 ab d0 16 56 81  |YV..`T.M..Y...V.|
000001e0  02 70 23 92 8b f8 27 be  42 25 40 46 24 0a 3f d6  |.p#...'.B%@F$.?.|
000001f0  64 8e a4 cf a7 7a be fc  96 b4 e6 79 7e 7f 45 81  |d....z.....y~.E.|
00000200
```

---

### Post by Moozillaaa on 2009-12-31
Not sure if this info tells me what my new partition assignments will be...

---

### Post by presence1960 on 2009-12-31
> **Moozillaaa said:**
> Not sure if this info tells me what my new partition assignments will be...

Between the pic & the script output this is what I see:
sda1-XP
sda2-Ubuntu 9.04
sda3- extended: sda5-unknown sda6-swap sda8-unknown
sda4-Fedora

sdb1-Vista
sdb2-Vista
sdb3-extended: sdb5-pclinux
sdb4- ext3 storage

So if you are installing karmic I would put it over sda2 9.04. So sda2 will be / mountpoint. Tick the format box so it formats sda2 prior to installing. You don't need any separate /boot etc partitions. They will be included in sda2

sdb4 appears to be a data partition. You can leave that be. or if you want to convert it to a separate /home partition you can highlight that partition and right click->change. In the window that appears **_DO NOT tick the format box_** & choose mount point /home
This will auto mount that partition as /home every time you boot

Or you can leave it alone and mount it when you need to. This will be better if you intend to share that partition between all the Linux OSs.

---

### Post by Moozillaaa on 2009-12-31
Great - thanks!

Do they have 'Thanks' scores in this forum? I'm not seeing it???


Edit:
What info defined sda2 as my root partition, as well as 'home'?
And sda4 I think is a wiped SuSE 11.1 install... That would make it look like a 'data' partition?

---

### Post by Moozillaaa on 2009-12-31
"There were no users or operating systems suitable for importing from." 

No problem - I've backed up the partition, but why IS this? Perhaps because I'm going from 32 bit to 64 bit?

AND,
step 8 - it's preparing 2 partitions as swap...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141932&d=1262293081[/IMG]

---

### Post by presence1960 on 2009-12-31
> **Moozillaaa said:**
> "There were no users or operating systems suitable for importing from." 

No problem - I've backed up the partition, but why IS this? Perhaps because I'm going from 32 bit to 64 bit?

AND,
**_step 8 - it's preparing 2 partitions as swap..._**

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141932&d=1262293081[/IMG]
That's because you have sda6 and sda7 as swap.  It aiuto detects existing swap partitions and configures them for use with the new installation.

---

