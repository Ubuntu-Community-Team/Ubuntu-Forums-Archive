---
title: "Grub Error 18 Ubuntu 8.04"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by StunnerAlpha on 2010-01-17
Ey guys, I recently tried installing Ubuntu 8.04 on my Compaq Evo N610c. The installation went smoothly but when booting I get a black screen that says: 
"GRUB loading stage1.5.

GRUB loading, please wait...
Error 18"

I have googled for the solution and it seems that putting the HD in LBA mode is what is required for it to boot properly. However I press F10 to get into the BIOs but I cannot seem to find the menu that allows me to make that change. If anyone could help me with that, that would be great. 

One more thing, I was wondering if installing the latest version of ubuntu would be recommended?

Thanks!

---

### Post by presence1960 on 2010-01-17
[http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors)

see above for GRUB error 18. The only surefire way I know to solve that is make a separate /boot partition within the maximum boundary your BIOS can read or update your BIOS.

Example your BIOS can only read up to the 137 GB limit on your hard disk. Your GRUB files are located at 150GB. You will get GRUB error 18. You can try to update your BIOS and see if that solves the problem or install Ubuntu with  separate /boot partition within the 137 GB area.

How far your BIOS can read on the hard disk is determined by the age of your BIOS. Refer to your motherboard's BIOS documentation or the manufacturer's web site to find that info.

---

### Post by StunnerAlpha on 2010-01-19
Thanks for the response. What you said makes sense and in fact, prior to the reformat there was a Win XP partition of 50 GB and about 250GB as a data partition. I talked with my brother who set up that configuration and he said that he had to do it because of exactly what you are saying, the mobo couldn't recognize a partition of 320GB.

So I decided to install ubuntu server version 9.10 and installed it on a partition that is half the size of the disk about 157GB. Now I have a partition with ubuntu 8.04 and ubuntu server 9.10 about the same size each. When I try loading into grub I get this error message:
"GRUB loading.
error: no such partition
grub rescue> _"

The very last line appears to be a command line prompt. Any pointers on how I would go about getting GRUB to work now? Thanks!

---

### Post by presence1960 on 2010-01-19
> **StunnerAlpha said:**
> Thanks for the response. What you said makes sense and in fact, prior to the reformat there was a Win XP partition of 50 GB and about 250GB as a data partition. I talked with my brother who set up that configuration and he said that he had to do it because of exactly what you are saying, the mobo couldn't recognize a partition of 320GB.

So I decided to install ubuntu server version 9.10 and installed it on a partition that is half the size of the disk about 157GB. Now I have a partition with ubuntu 8.04 and ubuntu server 9.10 about the same size each. When I try loading into grub I get this error message:
"GRUB loading.
error: no such partition
grub rescue> _"

The very last line appears to be a command line prompt. Any pointers on how I would go about getting GRUB to work now? Thanks!
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by StunnerAlpha on 2010-01-19
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type 'ext4'

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2cf22cf1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   311,532,479   311,532,417  83 Linux
/dev/sda2         311,532,480   625,137,344   313,604,865   5 Extended
/dev/sda5         619,129,098   625,137,344     6,008,247  82 Linux swap / Solaris
/dev/sda6         311,532,606   613,120,724   301,588,119  83 Linux
/dev/sda7         613,120,788   619,129,034     6,008,247  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1054 MB, 1054605312 bytes
255 heads, 63 sectors/track, 128 cylinders, total 2059776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0217934c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,059,775     2,059,713   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="61e58ffb-e919-4c6b-a990-e3f9858490db" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="6807d35b-66e5-44d4-9b3f-01426d478857" TYPE="ext4" 
/dev/sda7: TYPE="swap" UUID="3bcc9b3a-e528-47eb-af23-5ecd4d0c84db" 
/dev/sda7: UUID="3bcc9b3a-e528-47eb-af23-5ecd4d0c84db" TYPE="swap" 
/dev/sdb1: LABEL="ATT1GB" UUID="2CCB-7A33" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/ATT1GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=61e58ffb-e919-4c6b-a990-e3f9858490db ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=61e58ffb-e919-4c6b-a990-e3f9858490db ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=61e58ffb-e919-4c6b-a990-e3f9858490db ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=61e58ffb-e919-4c6b-a990-e3f9858490db /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=bc775dbb-fcfe-4c6c-8f84-c405dca16899 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 148.3GB: boot/grub/menu.lst
 148.4GB: boot/grub/stage2
 148.4GB: boot/initrd.img-2.6.24-16-generic
 148.4GB: boot/initrd.img-2.6.24-16-generic.bak
 148.4GB: boot/vmlinuz-2.6.24-16-generic
 148.4GB: initrd.img
 148.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000030  20 20 20 20 20 20 20 20  3c 6c 6f 6e 67 64 65 73  |        <longdes|
00000040  63 3e e0 a4 b5 e0 a4 bf  e0 a4 b6 e0 a4 be e0 a4  |c>..............|
00000050  b2 e0 a5 80 e0 a4 95 e0  a4 b0 e0 a4 a3 20 e0 a4  |............. ..|
00000060  95 e0 a4 b0 e0 a5 80 e0  a4 a4 e0 a4 be 20 e0 a4  |............. ..|
00000070  ae e0 a4 be e0 a4 89 e0  a4 b8 20 e0 a4 9a e0 a4  |.......... .....|
00000080  be e0 a4 95 20 e0 a4 b5  e0 a4 be e0 a4 aa e0 a4  |.... ...........|
00000090  b0 e0 a4 a4 e0 a5 87 e0  a4 b5 e0 a5 87 e0 a4 b3  |................|
000000a0  e0 a5 80 20 e0 a4 b5 e0  a4 be e0 a4 aa e0 a4 b0  |... ............|
000000b0  e0 a4 be e0 a4 9a e0 a5  87 20 e0 a4 a4 e0 a5 8b  |......... ......|
000000c0  20 e0 a4 ae e0 a4 b2 e0  a5 8d e0 a4 9f e0 a5 80  | ...............|
000000d0  e0 a4 aa e0 a5 8d e0 a4  b2 e0 a4 be e0 a4 af e0  |................|
000000e0  a4 b0 2e 20 e0 a4 b9 e0  a5 87 20 e0 a4 ae e0 a5  |... ...... .....|
000000f0  81 e0 a4 b2 e0 a5 8d e0  a4 af 20 e0 a4 aa e0 a5  |.......... .....|
00000100  8d e0 a4 b0 e0 a4 a4 e0  a5 8d e0 a4 af e0 a5 87  |................|
00000110  e0 a4 95 20 e0 a4 b8 e0  a5 8d e0 a4 95 e0 a5 8d  |... ............|
00000120  e0 a4 b0 e0 a5 8b e0 a4  b2 20 e0 a4 98 e0 a4 9f  |......... ......|
00000130  e0 a4 95 20 e0 a4 95 e0  a4 b0 e0 a5 80 e0 a4 a4  |... ............|
00000140  e0 a4 be 20 e0 a4 b5 e0  a4 bf e0 a4 b6 e0 a4 be  |... ............|
00000150  e0 a4 b2 e0 a5 80 e0 a4  95 e0 a4 b0 e0 a4 a3 20  |............... |
00000160  e0 a4 9f e0 a4 aa e0 a5  8d e0 a4 aa e0 a4 be e0  |................|
00000170  a4 9a e0 a5 87 20 e0 a4  b5 e0 a4 b0 e0 a5 8d e0  |..... ..........|
00000180  a4 a3 e0 a4 a8 20 e0 a4  95 e0 a4 b0 e0 a4 a4 e0  |..... ..........|
00000190  a5 87 2e 20 e0 a4 89 e0  a4 a6 e0 a4 be e0 a4 b9  |... ............|
000001a0  e0 a4 b0 e0 a4 a3 e0 a4  be e0 a4 b0 e0 a5 8d e0  |................|
000001b0  a4 a5 2c 20 e0 a4 aa e0  a5 8d e0 a4 b0 e0 a4 a4  |.., ............|
000001c0  e0 a5 8d e0 a4 af e0 a5  87 e0 a4 95 20 e0 a4 b8  |............ ...|
000001d0  e0 a5 8d e0 a4 95 e0 a5  8d e0 a4 b0 e0 a5 8b e0  |................|
000001e0  a4 b2 20 e0 a4 98 e0 a4  9f e0 a4 a8 e0 a4 be 20  |.. ............ |
000001f0  e0 a4 95 e0 a4 b0 e0 a5  80 e0 a4 a4 e0 a4 be 20  |............... |
00000200


=============================== StdErr Messages: ===============================

ls: cannot access /dev/mapper: No such file or directory

```

Thanks! :)

---

### Post by presence1960 on 2010-01-19
```
sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type 'ext4
```'

Your 9.10 server install is messed up, it can't be mounted. You also installed some type of bootloader to sda5 swap. See this:

```
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000030  20 20 20 20 20 20 20 20  3c 6c 6f 6e 67 64 65 73  |        <longdes|
00000040  63 3e e0 a4 b5 e0 a4 bf  e0 a4 b6 e0 a4 be e0 a4  |c>..............|
00000050  b2 e0 a5 80 e0 a4 95 e0  a4 b0 e0 a4 a3 20 e0 a4  |............. ..|
00000060  95 e0 a4 b0 e0 a5 80 e0  a4 a4 e0 a4 be 20 e0 a4  |............. ..|
00000070  ae e0 a4 be e0 a4 89 e0  a4 b8 20 e0 a4 9a e0 a4  |.......... .....|
00000080  be e0 a4 95 20 e0 a4 b5  e0 a4 be e0 a4 aa e0 a4  |.... ...........|
00000090  b0 e0 a4 a4 e0 a5 87 e0  a4 b5 e0 a5 87 e0 a4 b3  |................|
000000a0  e0 a5 80 20 e0 a4 b5 e0  a4 be e0 a4 aa e0 a4 b0  |... ............|
000000b0  e0 a4 be e0 a4 9a e0 a5  87 20 e0 a4 a4 e0 a5 8b  |......... ......|
000000c0  20 e0 a4 ae e0 a4 b2 e0  a5 8d e0 a4 9f e0 a5 80  | ...............|
000000d0  e0 a4 aa e0 a5 8d e0 a4  b2 e0 a4 be e0 a4 af e0  |................|
000000e0  a4 b0 2e 20 e0 a4 b9 e0  a5 87 20 e0 a4 ae e0 a5  |... ...... .....|
000000f0  81 e0 a4 b2 e0 a5 8d e0  a4 af 20 e0 a4 aa e0 a5  |.......... .....|
00000100  8d e0 a4 b0 e0 a4 a4 e0  a5 8d e0 a4 af e0 a5 87  |................|
00000110  e0 a4 95 20 e0 a4 b8 e0  a5 8d e0 a4 95 e0 a5 8d  |... ............|
00000120  e0 a4 b0 e0 a5 8b e0 a4  b2 20 e0 a4 98 e0 a4 9f  |......... ......|
00000130  e0 a4 95 20 e0 a4 95 e0  a4 b0 e0 a5 80 e0 a4 a4  |... ............|
00000140  e0 a4 be 20 e0 a4 b5 e0  a4 bf e0 a4 b6 e0 a4 be  |... ............|
00000150  e0 a4 b2 e0 a5 80 e0 a4  95 e0 a4 b0 e0 a4 a3 20  |............... |
00000160  e0 a4 9f e0 a4 aa e0 a5  8d e0 a4 aa e0 a4 be e0  |................|
00000170  a4 9a e0 a5 87 20 e0 a4  b5 e0 a4 b0 e0 a5 8d e0  |..... ..........|
00000180  a4 a3 e0 a4 a8 20 e0 a4  95 e0 a4 b0 e0 a4 a4 e0  |..... ..........|
00000190  a5 87 2e 20 e0 a4 89 e0  a4 a6 e0 a4 be e0 a4 b9  |... ............|
000001a0  e0 a4 b0 e0 a4 a3 e0 a4  be e0 a4 b0 e0 a5 8d e0  |................|
000001b0  a4 a5 2c 20 e0 a4 aa e0  a5 8d e0 a4 b0 e0 a4 a4  |.., ............|
000001c0  e0 a5 8d e0 a4 af e0 a5  87 e0 a4 95 20 e0 a4 b8  |............ ...|
000001d0  e0 a5 8d e0 a4 95 e0 a5  8d e0 a4 b0 e0 a5 8b e0  |................|
000001e0  a4 b2 20 e0 a4 98 e0 a4  9f e0 a4 a8 e0 a4 be 20  |.. ............ |
000001f0  e0 a4 95 e0 a4 b0 e0 a5  80 e0 a4 a4 e0 a4 be 20  |............... |
00000200

```

You can try to run fsck from the Live CD. Boot the Live CD and choose "try ubuntu without any changes" at the menu. When the desktop loads open a terminal and run ```
sudo e2fsck /dev/sda6 -y -f -v -c
```
let it complete then run in terminal ```
sudo e2fsck /dev/sda5 -y -f -v -c
```

If it can't be fixed I would say install 9.10 over again. Use gparted to delete the sda5 partition and format the sda6 partition. This time don't create another swap partition since you have one on sda7. The installer will recognize the existing swap partition and include it on the install.

---

### Post by StunnerAlpha on 2010-01-19
It is telling me to get a newer version of e2fsck... but I am down to reinstall Ubuntu 9.10. However, I have already tried reinstalling Ubuntu 9.10 and I deleted all partitions but specified a size of 157GB like last time and it says after it finished installing everything and reformatting that there is Ubuntu 8.04 on the system and that it would be safe to put grub as the master boot record, so I allow it. But I do not want two versions of ubuntu installed on my machine so how could I do a clean wipe and start from scratch? And what is gparted and how would I use it? And most of all, thank you very much for all of your help!

---

### Post by presence1960 on 2010-01-19
> **StunnerAlpha said:**
> It is telling me to get a newer version of e2fsck... but I am down to reinstall Ubuntu 9.10. However, I have already tried reinstalling Ubuntu 9.10 and I deleted all partitions but specified a size of 157GB like last time and it says after it finished installing everything and reformatting that there is Ubuntu 8.04 on the system and that it would be safe to put grub as the master boot record, so I allow it. But I do not want two versions of ubuntu installed on my machine so how could I do a clean wipe and start from scratch? And what is gparted and how would I use it? And most of all, thank you very much for all of your help!

The simplest way is to boot into the Ubuntu Live Cd and choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
gksu gparted
```

This will open gparted for you. Then right click on all your partitions and choose delete. When all are set to be deleted click Apply (green check mark on toolbar). This will leave your entire 320 GB disk as unallocated space.

Close gparted and on the desktop you will see an install icon. Use that to install ubuntu. When you get to the partitioner window choose "use entire disk" option. This will set up Ubuntu and you will have no problems with the BIOS reading your boot files.

---

### Post by StunnerAlpha on 2010-01-19
The 9.10 server disk doesn't have a "Try Ubuntu Without Changes" option. So do you think I should just settle with 8.04? I basically just want to create an SVN server. Also, my motherboard won't support an entire 320GB partition, so partitioning the drive into two won't do any harm? Thanks for all the help man.

---

### Post by presence1960 on 2010-01-19
> **StunnerAlpha said:**
> The 9.10 server disk doesn't have a "Try Ubuntu Without Changes" option. So do you think I should just settle with 8.04? I basically just want to create an SVN server. Also, my motherboard won't support an entire 320GB partition, so partitioning the drive into two won't do any harm? Thanks for all the help man.

You can either choose "use entire disk" option from the server install or download gparted Live CD from [here]("http://gparted.sourceforge.net/livecd.php"). Burn that iso as an image to CD and boot from it to delete and/or repartition your hard disk. Then install ubuntu.

---

### Post by meierfra. on 2010-01-19
> Your 9.10 server install is messed up
I don't think so. Your 8.04 CD cannot read   ext4, that's   all.

> You also installed some type of bootloader to sda5 swap. See this:

I don't think so.  I think its  just leftover from whatever used to be the partition and shouldn't  cause any problem. Also you can't run a file system check on a swap partitions. But you can reformat it via

```
sudo swapoff /dev/sda5
sudo mkswap /dev/sda5
sudo swapon /dev/sda5 
```


I don't think you need to reinstall anything.  You just need create a separate  boot partition at the beginning of the hard drive. 

**Even if you do decide to reinstall, you need  to create a separated boot partition  otherwise you will run into problems sooner or later.**

The boot partition needs to be at the beginning of the hard drive, so that it is completely inside the first 137GB of the hard drive.

---

### Post by presence1960 on 2010-01-19
> **meierfra. said:**
> I don't think so. Your 8.04 CD cannot read   ext4, that's   all.



I don't think so.  I think its  just leftover from whatever used to be the partition and shouldn't  cause any problem. Also you can't run a file system check on a swap partitions. But you can reformat it via

```
sudo swapoff /dev/sda5
sudo mkswap /dev/sda5
sudo swapon /dev/sda5 
```


I don't think you need to reinstall anything.  You just need create a separate  boot partition at the beginning of the hard drive. 

**Even if you do decide to reinstall, you need  to create a separated boot partition  otherwise you will run into problems sooner or later.**

The boot partition needs to be at the beginning of the hard drive, so that it is completely insider the first 137GB of the hard drive.

Thanks meierfra, I owe you again! It never clicked with me that the 8.04 Live CD does not support ext4. ](*,):oops:

---

### Post by StunnerAlpha on 2010-01-20
Thanks fellas. I solved the problem. I just ended up burning the gparted iso to disc (since the gparted program on the live cd was having trouble deleting some of the partitions) and wiped the drive then I ran the 8.04 live cd and chose install. I created two partitions, selected 'beginning' for both partitions which were about 158GBs apiece one of which I specified to primary and '/'(root) and the other to logical and '/usr/local' and I created a swap space of about 2GB. It installed and restarted and Ubuntu started up just fine. :) Hope this helps any other having the same issues that I had. Thanks for all the help!

---

### Post by meierfra. on 2010-01-20
> I solved the problem. 

You solved your problem for now.  But I think you got lucky and might run into troubles after kernel updates.  You won't be able to boot if  any of the boot files are place  outside the 137 GB limit.  Would you mind running the boot info script  and posting  the RESULTS.txt again, so that we can have a look at your current setup?

---

### Post by StunnerAlpha on 2010-01-20
Sure thing.

```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2cf22cf1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,496,379   312,496,317  83 Linux
/dev/sda2         312,496,380   316,400,174     3,903,795  82 Linux swap / Solaris
/dev/sda3         316,400,175   625,137,344   308,737,170  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1054 MB, 1054605312 bytes
255 heads, 63 sectors/track, 128 cylinders, total 2059776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0217934c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,059,775     2,059,713   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="726f9365-9c0b-4758-ae2a-6cccb1b7d7cc" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="943297e6-ada6-4558-b2e5-166a0cbec726" 
/dev/sda2: UUID="943297e6-ada6-4558-b2e5-166a0cbec726" TYPE="swap" 
/dev/sda3: UUID="f434d226-a95b-493c-ac51-46d3db411c72" TYPE="ext3" 
/dev/sdb1: LABEL="ATT1GB" UUID="2CCB-7A33" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda3 on /usr/local type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jubbal/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jubbal)
/dev/sdb1 on /media/ATT1GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=726f9365-9c0b-4758-ae2a-6cccb1b7d7cc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=726f9365-9c0b-4758-ae2a-6cccb1b7d7cc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=726f9365-9c0b-4758-ae2a-6cccb1b7d7cc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=726f9365-9c0b-4758-ae2a-6cccb1b7d7cc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=f434d226-a95b-493c-ac51-46d3db411c72 /usr/local      ext3    relatime        0       2
# /dev/sda2
UUID=943297e6-ada6-4558-b2e5-166a0cbec726 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 128.3GB: boot/grub/menu.lst
 128.3GB: boot/grub/stage2
 128.3GB: boot/initrd.img-2.6.24-16-generic
 128.3GB: boot/initrd.img-2.6.24-16-generic.bak
 128.3GB: boot/vmlinuz-2.6.24-16-generic
 128.3GB: initrd.img
 128.3GB: vmlinuz
=============================== StdErr Messages: ===============================

ls: cannot access /dev/mapper: No such file or directory

```

---

### Post by meierfra. on 2010-01-20
That's what I thought. You just got lucky. From your first RESULTS.txt


>  148.3GB: boot/grub/menu.lst
 148.4GB: boot/grub/stage2
 148.4GB: boot/initrd.img-2.6.24-16-generic
 148.4GB: boot/initrd.img-2.6.24-16-generic.bak
 148.4GB: boot/vmlinuz-2.6.24-16-generic
 148.4GB: initrd.img
 148.4GB: vmlinuz

The boot files were outside the 137 GB limits, and you could not boot.

Your new RESULTS.txt:


>  128.3GB: boot/grub/menu.lst
 128.3GB: boot/grub/stage2
 128.3GB: boot/initrd.img-2.6.24-16-generic
 128.3GB: boot/initrd.img-2.6.24-16-generic.bak
 128.3GB: boot/vmlinuz-2.6.24-16-generic
 128.3GB: initrd.img
 128.3GB: vmlinuz

Now the files are within the 137 GB limits and you are able to boot. But who knows    where the kernels will  end up after the next kernel update. 

You could use gparted to shrink your Ubuntu partition to 136 GB.  But since its a  fresh install, you could start from scratch and  create  a 136GB partition for Ubuntu and reinstall (that's faster than shrinking).  If you would like your Ubuntu partition to be larger than 136 GB, just create a 500MB boot partition at the beginning of  the drive. (a boot partition is just a partition with mount point "/boot"). Then your Ubuntu partition can be any size you want to.

---

### Post by StunnerAlpha on 2010-01-20
Oh ok, how would I go about creating a boot partition? :)

---

### Post by meierfra. on 2010-01-20
Use the Gparted LiveCD to partition your hard drive. Start with a deleting everything. Create a 500 MBR ext3 partition and then create the remaining partition just as before. (But you can choose  them any size you want to.) Install Ubuntu just as before, but choose mount point "/boot" for the 500MB ext3 partition.

Let me know if you need more detailed  help.

---

### Post by StunnerAlpha on 2010-01-20
So thats all I have to do and then I can have the ubuntu partition at whatever size I like?

---

### Post by meierfra. on 2010-01-20
> So thats all I have to do and then I can have the ubuntu partition at whatever size I like?

Yes.

---

### Post by StunnerAlpha on 2010-01-20
Aright, done. Does this look good?

```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2cf22cf1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       996,029       995,967  83 Linux
/dev/sda2             996,030     4,996,214     4,000,185  82 Linux swap / Solaris
/dev/sda3           4,996,215   625,137,344   620,141,130  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1054 MB, 1054605312 bytes
255 heads, 63 sectors/track, 128 cylinders, total 2059776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0217934c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,059,775     2,059,713   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="cb3a5885-cc44-41f1-a5f6-75ecca56d5a3" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="be34e81d-3ba0-49fd-84ed-efa9ba122989" 
/dev/sda2: UUID="be34e81d-3ba0-49fd-84ed-efa9ba122989" TYPE="swap" 
/dev/sda3: UUID="fe9efdfe-7dbc-4183-9e0f-57f7ced6c77a" TYPE="ext3" 
/dev/sdb1: LABEL="ATT1GB" UUID="2CCB-7A33" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jubbal/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jubbal)
/dev/sdb1 on /media/ATT1GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


============================= sda1/grub/menu.lst: =============================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=fe9efdfe-7dbc-4183-9e0f-57f7ced6c77a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=fe9efdfe-7dbc-4183-9e0f-57f7ced6c77a ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=fe9efdfe-7dbc-4183-9e0f-57f7ced6c77a ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location of files loaded by Grub: ===================


    .3GB: grub/menu.lst
    .3GB: grub/stage2
    .0GB: initrd.img-2.6.24-16-generic
    .0GB: initrd.img-2.6.24-16-generic.bak
    .0GB: vmlinuz-2.6.24-16-generic

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=fe9efdfe-7dbc-4183-9e0f-57f7ced6c77a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=fe9efdfe-7dbc-4183-9e0f-57f7ced6c77a ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=fe9efdfe-7dbc-4183-9e0f-57f7ced6c77a ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fe9efdfe-7dbc-4183-9e0f-57f7ced6c77a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=cb3a5885-cc44-41f1-a5f6-75ecca56d5a3 /boot           ext3    relatime        0       2
# /dev/sda2
UUID=be34e81d-3ba0-49fd-84ed-efa9ba122989 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


   2.8GB: boot/grub/menu.lst
   2.8GB: boot/grub/stage2
   2.6GB: boot/initrd.img-2.6.24-16-generic
   2.5GB: boot/initrd.img-2.6.24-16-generic.bak
   2.6GB: boot/vmlinuz-2.6.24-16-generic
   2.6GB: initrd.img
   2.6GB: vmlinuz
=============================== StdErr Messages: ===============================

ls: cannot access /dev/mapper: No such file or directory

```

And thanks for all the help! :)

---

