---
title: "Need a complete Ubuntu wipe!"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by Turbojoe on 2009-12-29
This could be a very long story but I'll try to keep it as short as possible. I had been using Ubuntu 9.10/Win XP and was quite happy. Then I got caught up in the hype and "upgraded" to Windows 7 and lost the boot loader. All hell has broken loose since then. Windows 7 was a waste of money for me. XP worked just fine. (lesson learned) Because I lost the boot loader during the "upgrade" I could only use Windows 7 and no longer boot in to Ubuntu. A friend tried using a partition manager to repair the boot menu and format the Ubuntu partitions so I would have a clean partition to install Ubuntu 9.40. That didn't work. My biggest problem is that my IDE DVD/CD that worked just fine in XP and Ubuntu no longer works with Windows 7 and I can't get past the boot loader created by the external program when trying to boot from the Windows disc. I just got a new ATA DVD from Newegg tonight and now during boot it comes up with: "Grub loading, Please wait Error 22". It just sits there and does nothing. I unplugged the new DVD and it boots normally to Windows. I need it to somehow NOT activate the boot loader. 

Without a working DVD drive I'm in a catch 22. I'm basically stuck with what is on my HD right now and can't make changes other than from online downloads. With the new SATA DVD Grub is coming up and I haven't seen that since I installed Windows 7. 
I **HAVE** to get past the boot process using the new DVD or I'm screwed and I have to toss this HD in the trash. 
I'm not a geek. This is way beyond me at this point. I need a layman's terms way to first completely wipe Ubuntu and **ANY** boot loaders from the hard drive. Then I'll most likely reformat and go back to XP and 9.40. I just need the hard drive "clean" of **ANY AND ALL** boot loaders right now so I can hopefully use my new DVD drive. I've tried every bios setting to no avail. I'm hoping there is a free HD format program out there as I'm out of work and just can't afford a $40.00 program to use only once.

To make a long story short here is what I'd like to accomplish. One partition for Windows XP or maybe Windows 7 
(since I paid for it) and a second partition for Ubuntu 9.40. Hopefully my new DVD drive will work in both OS's. 

Joe

---

### Post by presence1960 on 2009-12-29
> **Turbojoe said:**
> This could be a very long story but I'll try to keep it as short as possible. I had been using Ubuntu 9.10/Win XP and was quite happy. Then I got caught up in the hype and "upgraded" to Windows 7 and lost the boot loader. All hell has broken loose since then. Windows 7 was a waste of money for me. XP worked just fine. (lesson learned) Because I lost the boot loader during the "upgrade" I could only use Windows 7 and no longer boot in to Ubuntu. A friend tried using a partition manager to repair the boot menu and format the Ubuntu partitions so I would have a clean partition to install Ubuntu 9.40. That didn't work. My biggest problem is that my IDE DVD/CD that worked just fine in XP and Ubuntu no longer works with Windows 7 and I can't get past the boot loader created by the external program when trying to boot from the Windows disc. I just got a new ATA DVD from Newegg tonight and now during boot it comes up with: "Grub loading, Please wait Error 22". It just sits there and does nothing. I unplugged the new DVD and it boots normally to Windows. I need it to somehow NOT activate the boot loader. 

Without a working DVD drive I'm in a catch 22. I'm basically stuck with what is on my HD right now and can't make changes other than from online downloads. With the new SATA DVD Grub is coming up and I haven't seen that since I installed Windows 7. 
I **HAVE** to get past the boot process using the new DVD or I'm screwed and I have to toss this HD in the trash. 
I'm not a geek. This is way beyond me at this point. I need a layman's terms way to first completely wipe Ubuntu and **ANY** boot loaders from the hard drive. Then I'll most likely reformat and go back to XP and 9.40. I just need the hard drive "clean" of **ANY AND ALL** boot loaders right now so I can hopefully use my new DVD drive. I've tried every bios setting to no avail. I'm hoping there is a free HD format program out there as I'm out of work and just can't afford a $40.00 program to use only once.

To make a long story short here is what I'd like to accomplish. One partition for Windows XP or maybe Windows 7 
(since I paid for it) and a second partition for Ubuntu 9.40. Hopefully my new DVD drive will work in both OS's. 

Joe
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Turbojoe on 2009-12-30
Whoa! Lots of stuff here. There is at least one and possibly two failed Ubuntu installs that I would like to eliminate but I'm not sure which partitions they are. The last working version was an "ArtistX" distribution. It had some problems as well. I could never get a printer to work with it despite many people here trying to help. I'm not sure why it still shows Windows XP as that was wiped out by the Windows 7 install. 

```

```============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
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

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c066d6c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   195,623,504   195,623,442   7 HPFS/NTFS
/dev/sda2         195,623,505   625,137,344   429,513,840   f W95 Ext d (LBA)
/dev/sda5         195,623,568   391,391,594   195,768,027   7 HPFS/NTFS
/dev/sda6         391,391,658   625,137,344   233,745,687   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0380037f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   525,486,149   525,486,087   7 HPFS/NTFS
/dev/sdb2         525,486,150   976,768,064   451,281,915   5 Extended
/dev/sdb5         651,339,423   967,675,274   316,335,852  83 Linux
/dev/sdb6         967,675,338   976,768,064     9,092,727  82 Linux swap / Solaris
/dev/sdb7         525,486,276   646,118,234   120,631,959  83 Linux
/dev/sdb8         646,118,298   651,339,359     5,221,062  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="70D8F0A8D8F06DAA" LABEL="FILES and Games" TYPE="ntfs" 
sda5: UUID="32E4F2FAE4F2BF63" LABEL="Games and Files" TYPE="ntfs" 
sda6: UUID="5670F53570F51D05" LABEL="Mutimedia" TYPE="ntfs" 
sdb1: UUID="526CCCE36CCCC2C9" LABEL="Windows 7" TYPE="ntfs" 
sdb5: UUID="56f5fb30-6e17-44c4-8e15-7d905c4bf468" SEC_TYPE="ext2" TYPE="ext3" 
sdb6: UUID="4bfdaf59-a217-47d7-9a6e-77ced55bba57" TYPE="swap" 
sdb7: UUID="37cb4071-0504-4347-bdf1-c451f2a1b659" SEC_TYPE="ext2" TYPE="ext3" 
sdb8: UUID="626dea09-4402-4994-9188-c605560f6e10" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
# kopt=root=UUID=56f5fb30-6e17-44c4-8e15-7d905c4bf468 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=56f5fb30-6e17-44c4-8e15-7d905c4bf468

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		56f5fb30-6e17-44c4-8e15-7d905c4bf468
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=56f5fb30-6e17-44c4-8e15-7d905c4bf468 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		56f5fb30-6e17-44c4-8e15-7d905c4bf468
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=56f5fb30-6e17-44c4-8e15-7d905c4bf468 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		56f5fb30-6e17-44c4-8e15-7d905c4bf468
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=56f5fb30-6e17-44c4-8e15-7d905c4bf468 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		56f5fb30-6e17-44c4-8e15-7d905c4bf468
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=56f5fb30-6e17-44c4-8e15-7d905c4bf468 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		56f5fb30-6e17-44c4-8e15-7d905c4bf468
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=56f5fb30-6e17-44c4-8e15-7d905c4bf468 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=4bfdaf59-a217-47d7-9a6e-77ced55bba57 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 352.0GB: boot/grub/menu.lst
 352.0GB: boot/grub/stage2
 352.0GB: boot/initrd.img-2.6.27-11-generic
 352.0GB: boot/initrd.img-2.6.28-16-generic
 352.0GB: boot/vmlinuz-2.6.27-11-generic
 352.1GB: boot/vmlinuz-2.6.28-16-generic
 352.0GB: initrd.img
 352.0GB: initrd.img.old
 352.1GB: vmlinuz
 352.0GB: vmlinuz.old

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
# kopt=root=UUID=37cb4071-0504-4347-bdf1-c451f2a1b659 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=37cb4071-0504-4347-bdf1-c451f2a1b659

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		37cb4071-0504-4347-bdf1-c451f2a1b659
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=37cb4071-0504-4347-bdf1-c451f2a1b659 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		37cb4071-0504-4347-bdf1-c451f2a1b659
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=37cb4071-0504-4347-bdf1-c451f2a1b659 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		37cb4071-0504-4347-bdf1-c451f2a1b659
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=56f5fb30-6e17-44c4-8e15-7d905c4bf468 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=56f5fb30-6e17-44c4-8e15-7d905c4bf468 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=56f5fb30-6e17-44c4-8e15-7d905c4bf468 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=56f5fb30-6e17-44c4-8e15-7d905c4bf468 ro single 
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
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=37cb4071-0504-4347-bdf1-c451f2a1b659 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=626dea09-4402-4994-9188-c605560f6e10 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


 317.4GB: boot/grub/menu.lst
 317.3GB: boot/grub/stage2
 317.4GB: boot/initrd.img-2.6.28-11-generic
 317.3GB: boot/vmlinuz-2.6.28-11-generic
 317.4GB: initrd.img
 317.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 31 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |.1..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 80 fa 33 c0 8e d8  8e d0 bc 00 7c b8 30 08  |....3.......|.0.|
00000040  8e c0 fb b8 00 b8 8e e8  e8 1d 00 b9 03 00 32 f6  |..............2.|
00000050  b8 28 02 2e 8a 16 32 7c  bb 00 01 50 cd 13 72 03  |.(....2|...P..r.|
00000060  58 cd 13 ea 00 01 30 08  60 b9 e8 03 33 db 66 65  |X.....0.`...3.fe|
00000070  c7 07 00 00 00 00 83 c3  04 e2 f3 b4 02 32 ff 33  |.............2.3|
00000080  d2 cd 10 61 c3 60 b4 a0  f6 e4 32 ff d1 e3 03 d8  |...a.`....2.....|
00000090  8a 14 0a d2 74 09 65 89  17 46 83 c3 02 eb f1 61  |....t.e..F.....a|
000000a0  c3 50 61 72 61 67 6f 6e  00 4c 6f 61 64 69 6e 67  |.Paragon.Loading|
000000b0  2e 2e 2e 2e 00 4d 42 52  20 52 65 76 69 73 69 6f  |.....MBR Revisio|
000000c0  6e 20 30 00 ef ee fe ff  ef ee fe ff ef ee fe ff  |n 0.............|
000000d0  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
000000e0  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
000000f0  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000100  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000110  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000120  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000130  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000140  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000150  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000160  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000170  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000180  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000190  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
000001a0  00 00 00 00 00 00 00 00  14 d7 51 6d 7f 03 6c 4d  |..........Qm..lM|
000001b0  02 00 00 00 3b 59 2e 1f  7f 03 80 03 ef ee 80 01  |....;Y..........|
000001c0  01 00 07 fe ff ff 3f 00  00 00 07 48 52 1f 00 fe  |......?....HR...|
000001d0  ff ff 05 fe ff ff 46 48  52 1f fb 03 e6 1a 00 00  |......FHR.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

```

Joe

---

### Post by presence1960 on 2009-12-30
Ok sdb5 looks like it was a good install as you have 3 different kernels in there. I would remove sdb7 with gparted after we get you up and running.

This is what I would do. I would first restore windows 7 bootloader to MBR of sdb. You have an unknown bootloader on sdb. Then check to make sure windows 7 boots. If it does boot then we want to put GRUB on MBR of sdb so you can boot both windows and Ubuntu on sdb5.

You will need your Windows 7 install DVD & the 9.04 Live CD. Boot your machine with the win 7 DVD. Go into BIOS and set the 500 GB (sdb) as first in the hard disk boot order. Save changes to CMOS & continue booting. Follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for windows 7. You have to scroll down some to see instructions for Vista/Windows 7. When completed reboot without the Windows 7 DVD and you should boot right into windows. If you do then move on to installing GRUB to MBR of sdb so you can boot both Ubuntu & Windows7.

Reboot with the Ubuntu 9.04 Live CD/USB. At the menu choose "try Ubuntu without any changes...", when the desktop loads open a terminal (Applications > Accessories > Terminal) and do this:

```
1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4) (hd1,6)". 
3. Type "root (hd1,4)"
4. Type "setup (hd1)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.
```

Boot into Ubuntu. open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll down to this entry for windows:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1
```

Change it to:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title         Windows 7
rootnoverify  (hd0,0)
chainloader   +1
```

Click Save on the toolbar at top. Close file. Reboot & try booting windows 7.

---

### Post by Turbojoe on 2009-12-30
This is awesome. Thanks for your help! I probably won't be able to try this until tomorrow though as I have some things to do tonight. I'll post back with my results. Thanks again.

Joe

---

### Post by presence1960 on 2009-12-30
> **Turbojoe said:**
> This is awesome. Thanks for your help! I probably won't be able to try this until tomorrow though as I have some things to do tonight. I'll post back with my results. Thanks again.

Joe

you are welcome. I am subscribed to this thread so I will receive an email notification if any other posts are made here. I will check back.

According to your script output the Ubuntu on sdb5 looks like a good install that was used a little bit because it has 2 updated kernels. That's why I chose that one to try to get working.

---

### Post by Turbojoe on 2009-12-31
Progress report:

I was able to get through the first part to repair Windows 7. As long as I have the DVD unplugged it now boots straight into Windows without the funky bootloader that was there before. However, if I have the DVD plugged in it stops the boot process and comes up with "grub loading, please wait" then "error 22". The DVD and grub just don't want to work together.

The only way I can get into Ubuntu is with the live CD. When I do that it won't allow me to save changes to the menu.lst file because I don't have administrator permissions when running from the CD. 

I'm lost again....

Joe

---

### Post by presence1960 on 2009-12-31
> **Turbojoe said:**
> Progress report:

I was able to get through the first part to repair Windows 7. As long as I have the DVD unplugged it now boots straight into Windows without the funky bootloader that was there before. However, if I have the DVD plugged in it stops the boot process and comes up with "grub loading, please wait" then "error 22". The DVD and grub just don't want to work together.

The only way I can get into Ubuntu is with the live CD. When I do that it won't allow me to save changes to the menu.lst file because I don't have administrator permissions when running from the CD. 

I'm lost again....

Joe

Did you set sdb (500GB) disk as first to boot in BIOS hard disk boot order before you repaired windows? Did you leave it that way when trying to boot Ubuntu Live CD? Is the DVD an USB external or a SATA or IDE internal DVD drive?

Now that you fixed windows see if you can boot the Live CD and run that script again & post the new results.

---

### Post by presence1960 on 2009-12-31
Ok I just went back to your original post. You said it is a SATA DVD drive. Open your case and switch the DVD to another available SATA controller port.

Hopefully you are not using a SATA PCI card to control your SATA boot devices. If you are using a SATA PCI card you do not want any drives that boot on that card. You want them on the SATA connectors on the motherboard.

---

### Post by Turbojoe on 2009-12-31
> **presence1960 said:**
> Did you set sdb (500GB) disk as first to boot in BIOS hard disk boot order before you repaired windows? Did you leave it that way when trying to boot Ubuntu Live CD? Is the DVD an USB external or a SATA or IDE internal DVD drive?

Now that you fixed windows see if you can boot the Live CD and run that script again & post the new results.

HD is set as first in BIOS. This DVD is brand new as of yesterday and is SATA. I had the exact same issues with the original IDE DVD. 

I'm using the Ubuntu live CD right now to make this post. I'll reboot one more time and double check BIOS just to make certain it saved the change. 

Joe

---

### Post by Turbojoe on 2009-12-31
> **presence1960 said:**
> Ok I just went back to your original post. You said it is a SATA DVD drive. Open your case and switch the DVD to another available SATA controller port.

Hopefully you are not using a SATA PCI card to control your SATA boot devices. If you are using a SATA PCI card you do not want any drives that boot on that card. You want them on the SATA connectors on the motherboard.

My second HD is SATA using the MB connectors (no card). It does not show in the BIOS so I can't control its location in the boot sequence. There are only two SATA ports. Would swapping the HD and DVD on the ports help? The grub error occurred even with the IDE DVD.

Joe

---

### Post by presence1960 on 2009-12-31
> **Turbojoe said:**
> My second HD is SATA using the MB connectors (no card). It does not show in the BIOS so I can't control its location in the boot sequence. There are only two SATA ports. Would swapping the HD and DVD on the ports help? The grub error occurred even with the IDE DVD.

Joe

At this point this does seem to be a hardware issue in my opinion.

Which hard disk is IDE? (ex. 320 GB or 500 GB)

If your SATA is not recognized in BIOS and can not be moved up in the hard disk boot order then that is a major problem if both OSs are installed on that SATA disk. It has to boot before the IDE disk. 

What is the make & model of your machine? I want to look at the manual online to see if we can or can not get BIOS to move those disks around in the boot order.

---

### Post by Turbojoe on 2009-12-31
> **presence1960 said:**
> At this point this does seem to be a hardware issue in my opinion.

Which hard disk is IDE? (ex. 320 GB or 500 GB)

If your SATA is not recognized in BIOS and can not be moved up in the hard disk boot order then that is a major problem if both OSs are installed on that SATA disk. It has to boot before the IDE disk. 

What is the make & model of your machine? I want to look at the manual online to see if we can or can not get BIOS to move those disks around in the boot order.

I had actually forgotten which drive was what size. The 320gb drive is the IDE primary and has both OS's. The SATA disk has no OS. It's used strictly for storage.

The computer was home built. It has an ABIT AN7 MB. It's old but works fine. All these problems started after installing Windows 7. That's when I lost the boot loader and the DVD started fighting with grub. 

Joe

---

### Post by presence1960 on 2009-12-31
Let me find that mobo manual. I'll be back!

---

### Post by presence1960 on 2009-12-31
> **Turbojoe said:**
> I had actually forgotten which drive was what size. The 320gb drive is the IDE primary and has both OS's. The SATA disk has no OS. It's used strictly for storage.

The computer was home built. It has an ABIT AN7 MB. It's old but works fine. All these problems started after installing Windows 7. That's when I lost the boot loader and the DVD started fighting with grub. 

Joe

============================= Boot Info Summary: ```
==============================

=> Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2
in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
=> No known boot loader is installed in the MBR of /dev/sdb
sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda5 starts
at sector 63.
Operating System:
Boot files/dirs:

sda6: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda6 starts
at sector 63.
Operating System:
Boot files/dirs:

[COLOR="Red"]sdb1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe
/ntldr /ntdetect.com
[/COLOR]
sdb2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

[COLOR="Red"]sdb5: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab[/COLOR]

sdb6: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

sdb7: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab

sdb8: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

=========================== Drive/Partition Info: =============================

[COLOR="Red"]Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 320.0 GB, 320072933376 bytes[/COLOR]
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c066d6c

Partition Boot Start End Size Id System

/dev/sda1 * 63 195,623,504 195,623,442 7 HPFS/NTFS
/dev/sda2 195,623,505 625,137,344 429,513,840 f W95 Ext d (LBA)
/dev/sda5 195,623,568 391,391,594 195,768,027 7 HPFS/NTFS
/dev/sda6 391,391,658 625,137,344 233,745,687 7 HPFS/NTFS


[COLOR="Red"]Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 500.1 GB[/COLOR], 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0380037f

Partition Boot Start End Size Id System

/dev/sdb1 * 63 525,486,149 525,486,087 7 HPFS/NTFS
/dev/sdb2 525,486,150 976,768,064 451,281,915 5 Extended
/dev/sdb5 651,339,423 967,675,274 316,335,852 83 Linux
/dev/sdb6 967,675,338 976,768,064 9,092,727 82 Linux swap / Solaris
/dev/sdb7 525,486,276 646,118,234 120,631,959 83 Linux
/dev/sdb8 646,118,298 651,339,359 5,221,062 82 Linux swap / Solaris
```

If the 320 is the IDE then both windows 7 and Ubuntu are on the SATA disk. see red above

---

### Post by Turbojoe on 2009-12-31
Everything had worked so well for so long that obviously I forgot just what was what. I seriously thought the IDE had the OS's though. Windows 7 is turning into more of a nightmare than I want to deal with anymore. I think my best bet is to do a complete re-format and go back to XP/Ubuntu. Life was good then.

Joe

---

### Post by presence1960 on 2009-12-31
> **Turbojoe said:**
> Everything had worked so well for so long that obviously I forgot just what was what. I seriously thought the IDE had the OS's though. Windows 7 is turning into more of a nightmare than I want to deal with anymore. I think my best bet is to do a complete re-format and go back to XP/Ubuntu. Life was good then.

Joe

If you can't move that SATA disk up in the boot order you have no other choice. just install windows first, then Ubuntu on the IDE.

---

### Post by Turbojoe on 2009-12-31
> **presence1960 said:**
> If you can't move that SATA disk up in the boot order you have no other choice. just install windows first, then Ubuntu on the IDE.

I sincerely appreciate all of your help. Since Windows 7 created all my problems it just makes sense to dump it and go back to what worked before. I can think of better things to do than spend a few hours setting everything up again. Oh well. This isn't the first time.....

Joe

---

### Post by presence1960 on 2009-12-31
> **Turbojoe said:**
> I sincerely appreciate all of your help. Since Windows 7 created all my problems it just makes sense to dump it and go back to what worked before. I can think of better things to do than spend a few hours setting everything up again. Oh well. This isn't the first time.....

Joe

I am really sorry. If it is an old board you may not be able to boot from SATA. I have found a link to a manual for your mobo on Abit's site. out of curiosity I will go over it anyway.

---

