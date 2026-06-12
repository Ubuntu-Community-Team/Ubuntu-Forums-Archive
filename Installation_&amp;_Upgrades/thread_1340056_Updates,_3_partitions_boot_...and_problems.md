---
title: "Updates, 3 partitions boot ...and problems"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by m10sang10 on 2009-11-28
Hi Gentleman,
 I have a PC, it Boot with 1-Ubuntu 9.04 (the S.O' grub, boot the 3 partitions) 2-W XP  3-Kubuntu 9.04 

Well,when I was making the update of kubuntu 9.04 to kubuntu 9.10 from INTERNET, apparently all was OK BUT when I started it doesn't work ,I suppose that my problem is the grub in Ubuntu 9.04 but really I am not sure about and because of that I am asking for your gentile help.

Truly yours

Marco

---

### Post by presence1960 on 2009-11-28
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by m10sang10 on 2009-11-28
Thanks for answer

This One?

Marco.

---

### Post by presence1960 on 2009-11-28
> **m10sang10 said:**
> Thanks for answer

This One?

Marco.
Not what we need. Download the script, place it on desktop & then run the command I posted in terminal. This will produce a file on your desktop. Open that file copy all contents and paste back here in the forum. Once pasted highlight all text and click # at the top in the toolbar. Then submit your post.

---

### Post by m10sang10 on 2009-11-28
```
Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Recovery:Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf197424e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     8,920,799     8,920,737   b W95 FAT32
/dev/sda2    *      8,920,800   156,295,439   147,374,640   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7c87d160

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   108,727,919   108,727,857   7 HPFS/NTFS
/dev/sdb3         108,727,920   160,826,714    52,098,795   5 Extended
/dev/sdb5         141,500,583   159,911,009    18,410,427  83 Linux
/dev/sdb6         159,911,073   160,826,714       915,642  82 Linux swap / Solaris
/dev/sdb7         108,728,046   140,038,604    31,310,559  83 Linux
/dev/sdb8         140,038,668   141,500,519     1,461,852  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="HP_RECOVERY" UUID="7799-5D9F" TYPE="vfat" 
/dev/sda2: UUID="FED8A01BD89FCFEF" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sdb1: UUID="D0D07941D0792EBA" LABEL="HP CREATION" TYPE="ntfs" 
/dev/sdb5: UUID="b2e3b840-3202-4767-aa83-7fafee9ec654" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="13c32503-eafa-4c62-a2e0-f6e669f3fd62" TYPE="swap" 
/dev/sdb7: UUID="612a7f6b-fb11-4770-b186-6d14ad374b2d" TYPE="ext3" 
/dev/sdb8: UUID="f2c84fbf-7df2-4734-8817-7a52a2a6bb29" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marco/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marco)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda2/BOOT.INI: ================================

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn /NOGUIBOOT /BOOTLOGO


=========================== sdb5/boot/grub/menu.lst: ===========================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue


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
# kopt=root=UUID=b2e3b840-3202-4767-aa83-7fafee9ec654 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b2e3b840-3202-4767-aa83-7fafee9ec654

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

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		b2e3b840-3202-4767-aa83-7fafee9ec654
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=b2e3b840-3202-4767-aa83-7fafee9ec654 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		b2e3b840-3202-4767-aa83-7fafee9ec654
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=b2e3b840-3202-4767-aa83-7fafee9ec654 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.27-7-generic
uuid		b2e3b840-3202-4767-aa83-7fafee9ec654
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b2e3b840-3202-4767-aa83-7fafee9ec654 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b2e3b840-3202-4767-aa83-7fafee9ec654
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b2e3b840-3202-4767-aa83-7fafee9ec654 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.10, memtest86+
uuid		b2e3b840-3202-4767-aa83-7fafee9ec654
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=b2e3b840-3202-4767-aa83-7fafee9ec654 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=13c32503-eafa-4c62-a2e0-f6e669f3fd62 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  72.9GB: boot/grub/menu.lst
  72.8GB: boot/grub/stage2
  72.8GB: boot/initrd.img-2.6.27-7-generic
  77.9GB: boot/initrd.img-2.6.31-15-generic
  72.8GB: boot/vmlinuz-2.6.27-7-generic
  72.8GB: boot/vmlinuz-2.6.31-15-generic
  77.9GB: initrd.img
  72.8GB: vmlinuz

=========================== sdb7/boot/grub/menu.lst: ===========================

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
default		5

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue



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
# kopt=root=UUID=612a7f6b-fb11-4770-b186-6d14ad374b2d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=612a7f6b-fb11-4770-b186-6d14ad374b2d

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		612a7f6b-fb11-4770-b186-6d14ad374b2d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=612a7f6b-fb11-4770-b186-6d14ad374b2d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		612a7f6b-fb11-4770-b186-6d14ad374b2d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=612a7f6b-fb11-4770-b186-6d14ad374b2d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic


title		Ubuntu 8.10, memtest86+
uuid		612a7f6b-fb11-4770-b186-6d14ad374b2d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b2e3b840-3202-4767-aa83-7fafee9ec654 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b2e3b840-3202-4767-aa83-7fafee9ec654 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb7
UUID=612a7f6b-fb11-4770-b186-6d14ad374b2d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb8
UUID=f2c84fbf-7df2-4734-8817-7a52a2a6bb29 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


  70.0GB: boot/grub/menu.lst
  70.0GB: boot/grub/stage2
  70.0GB: boot/initrd.img-2.6.27-11-generic
  70.0GB: boot/initrd.img-2.6.28-16-generic
  70.0GB: boot/vmlinuz-2.6.27-11-generic
  70.0GB: boot/vmlinuz-2.6.28-16-generic
  70.0GB: initrd.img
  70.0GB: vmlinuz
```

---

### Post by presence1960 on 2009-11-28
This what I would do:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)(hd1,6)". 
5. Type "root (hd1,4)
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

When rebooting go into BIOS and set your sdb disk (82.3 GB) as first in the hard disk boot order. Save changes to CMOS and continue booting. Boot into Ubuntu 9.10. When the desktop loads open a terminal and run ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst. If you don't have gedit use whatever text editor you have in the command.

Scroll down to here:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +1
```

and change to:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title         Windows Recovery
rootnoverify  (hd1,0)
map           (hd0) (hd1)
map           (hd1) (hd0)
chainloader   +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title         Microsoft Windows XP Home Edition
rootnoverify  (hd1,1)
map           (hd0) (hd1)
map           (hd1) (hd0)
chainloader   +1

title          Ubuntu 9.04
rootnoverify   (hd0,6)
chainloader    +1
```

Click Save on toolbar, close file and reboot. Try booting all your OSs from the grub menu. report back.

---

### Post by m10sang10 on 2009-11-28
Thanks for answer!

I am going to try it
But some question , will be it changing my grub to grub 2? (because I don't want it yet) and will be it booting of my ubuntu 9.04 yet?

Thanks in advance

---

### Post by presence1960 on 2009-11-28
> **m10sang10 said:**
> Thanks for answer!

I am going to try it
But some question , will be it changing my grub to grub 2? (because I don't want it yet) and will be it booting of my ubuntu 9.04 yet?

Thanks in advance

you will still have legacy grub not grub2. Your GRUB on sdb is pointing to wrong partition, this will fix that.

---

### Post by m10sang10 on 2009-11-29
Thanks for answer
I was doing it;

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1".

But here I got:
Error 15: File not found
What could I do?
Thanks in advance

---

### Post by presence1960 on 2009-11-29
sorry that grub command should be this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4) (hd1,6)". 
5. Type "root (hd1,6)"
6. Type "setup (hd1)"
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

---

### Post by presence1960 on 2009-11-29
I think your best bet is to install GRUB 2, it will detect all your OSs automatically. I just looked at your 9.04 menu.lst and it only has 8.10 kernels. And then you are going to have to edit your windows entry as well.
See [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") for installing GRUB 2. You want to install it to /dev/sdb then reboot & make sdb boot first in the hard disk boot order in BIOS.

---

### Post by m10sang10 on 2009-11-29
Thanks for answer presence1960:
Sorry I didn't explain myseft well,
I didn't get response like "(hd1,4) (hd1,6)". I got; Error 15: File not found

I thought put grub 2 but in my other PC with 6 O.S. I had a problem  editing the Grub 2 (not with legacy Grub)I had to go back to legacy.

Thanks in advance.

---

### Post by presence1960 on 2009-11-29
> **m10sang10 said:**
> Thanks for answer presence1960:
Sorry I didn't explain myseft well,
I didn't get response like "(hd1,4) (hd1,6)". I got; Error 15: File not found

I thought put grub 2 but in my other PC with 6 O.S. I had a problem  editing the Grub 2 (not with legacy Grub)I had to go back to legacy.

Thanks in advance.

That means you have no GRUB stage1 file. You will have to install GRUB from the 9.04 Live CD. See [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") for instructions. Your root device will be /dev/sdb7

---

