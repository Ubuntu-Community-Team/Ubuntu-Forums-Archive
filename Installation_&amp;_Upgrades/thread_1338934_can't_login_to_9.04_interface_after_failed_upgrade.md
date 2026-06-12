---
title: "can't login to 9.04 interface after failed upgrade to 9.10"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2009-11-27
Hi all :(
I have had a smooth running Ubuntu 9.04 OS together with XP SP2.
After checking the update manager, i started the upgrade to 9.10 through a reliable broadband connection.
Unfortunately, the laptop was running on battery power and i dozed off briefly.
I remember that the dialog box showed the ETA as 15min or so when i last saw it. Now, the battery must have eventually discharged at some stage and the comp switched off.
Now, when i finally started the comp i was unable to boot into any of the Ubuntu kernels (my XP OS continues to run smoothly). I get the following message-

One or more of the mounts listed in /etc/fstab/ cannot yet be mounted
(Esc for recovery shell)
/:waiting for dev/disk/by-uuid/d0741489-59ed-41ae-a21d-2bee0257cbb9/tmp: waiting for (null)
swap: waiting for UUID= 7702d702-02a9-43fa-a84c-e1c4499dff78

so i am in a bit of spot here. :( any suggestions welcome !
should i try to re-install using the 9.04 installation CD that i have?
thanks!

---

### Post by presence1960 on 2009-11-27
> **AM_SOS said:**
> Hi all :(
I have had a smooth running Ubuntu 9.04 OS together with XP SP2.
After checking the update manager, i started the upgrade to 9.10 through a reliable broadband connection.
Unfortunately, the laptop was running on battery power and i dozed off briefly.
I remember that the dialog box showed the ETA as 15min or so when i last saw it. Now, the battery must have eventually discharged at some stage and the comp switched off.
Now, when i finally started the comp i was unable to boot into any of the Ubuntu kernels (my XP OS continues to run smoothly). I get the following message-

One or more of the mounts listed in /etc/fstab/ cannot yet be mounted
(Esc for recovery shell)
/:waiting for dev/disk/by-uuid/d0741489-59ed-41ae-a21d-2bee0257cbb9/tmp: waiting for (null)
swap: waiting for UUID= 7702d702-02a9-43fa-a84c-e1c4499dff78

so i am in a bit of spot here. :( any suggestions welcome !
should i try to re-install using the 9.04 installation CD that i have?
thanks!

For an in place dist upgrade gone awry you may be able to get it running or you may not. I always do clean installs rather than a dist upgrade to eliminate the chance of something going wrong. There are a lot of threads in here with people having major troubles with dist upgrades.

If you like trying to fix broken OSs then do this so we can get more info about what you have going on there:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

If you aren't willing to dig in & trouble shoot then back up your data & reinstall.

---

### Post by AM_SOS on 2009-11-27
Hey many thanks for all the trouble you are taking here! Though I am busy I would still like to see what I can learn about this OS with your help. I did all that you instructed and the text from the results file is pasted below:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd1d0a7d2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,199,154    51,199,092   7 HPFS/NTFS
/dev/sda2          51,199,155   234,436,544   183,237,390   f W95 Ext d (LBA)
/dev/sda5          51,199,218   112,631,714    61,432,497   7 HPFS/NTFS
/dev/sda6         112,631,778   190,434,509    77,802,732   7 HPFS/NTFS
/dev/sda7         190,434,573   232,508,744    42,074,172  83 Linux
/dev/sda8         232,508,808   234,436,544     1,927,737  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3658AD2F58ACEF35" TYPE="ntfs" 
/dev/sda5: UUID="B0605A89605A5666" TYPE="ntfs" 
/dev/sda6: UUID="A2B46429B463FDE3" TYPE="ntfs" 
/dev/sda7: UUID="d0741489-59ed-41ae-a21d-2bee0257cbb9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="7702d702-02a9-43fa-a84c-e1c4499dff78" 

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


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d0741489-59ed-41ae-a21d-2bee0257cbb9

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
uuid		d0741489-59ed-41ae-a21d-2bee0257cbb9
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		d0741489-59ed-41ae-a21d-2bee0257cbb9
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		d0741489-59ed-41ae-a21d-2bee0257cbb9
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		d0741489-59ed-41ae-a21d-2bee0257cbb9
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d0741489-59ed-41ae-a21d-2bee0257cbb9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d0741489-59ed-41ae-a21d-2bee0257cbb9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-9-generic
uuid		d0741489-59ed-41ae-a21d-2bee0257cbb9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-9-generic (recovery mode)
uuid		d0741489-59ed-41ae-a21d-2bee0257cbb9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic
uuid		d0741489-59ed-41ae-a21d-2bee0257cbb9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid		d0741489-59ed-41ae-a21d-2bee0257cbb9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, memtest86+
uuid		d0741489-59ed-41ae-a21d-2bee0257cbb9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=d0741489-59ed-41ae-a21d-2bee0257cbb9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=7702d702-02a9-43fa-a84c-e1c4499dff78 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  98.9GB: boot/grub/menu.lst
  98.9GB: boot/grub/stage2
  98.6GB: boot/initrd.img-2.6.27-7-generic
  98.7GB: boot/initrd.img-2.6.27-9-generic
  98.9GB: boot/initrd.img-2.6.28-11-generic
  99.0GB: boot/initrd.img-2.6.28-13-generic
 104.5GB: boot/initrd.img-2.6.28-16-generic
  98.6GB: boot/vmlinuz-2.6.27-7-generic
  98.6GB: boot/vmlinuz-2.6.27-9-generic
  98.6GB: boot/vmlinuz-2.6.28-11-generic
  98.7GB: boot/vmlinuz-2.6.28-13-generic
  99.0GB: boot/vmlinuz-2.6.28-16-generic
  98.6GB: boot/vmlinuz-2.6.31-15-generic
 104.5GB: initrd.img
  99.0GB: initrd.img.old
  99.0GB: vmlinuz
  98.7GB: vmlinuz.old
```

---

### Post by presence1960 on 2009-11-27
That error message about not being able to mount had me look at your fstab file. It looks ok to me.

One thing I did notice is that you still have jaunty kernels and no Karmic kernels. Kernel 2.6.28.x are Jaunty kernels. Karmic's are 2.6.31.x

Other than the fact you have GRUB 0.97, which you probably chose to keep during the upgrade, I see nothing out of the ordinary.

Maybe someone else will come along with other insight. Unfortunately dist upgrades are an area I have zero experience in because I always opt for a clean install.

---

### Post by AM_SOS on 2009-11-27
no problem. thanks for trying!
guess i'll just go ahead and re-install the 9.04 version and then run the online update properly.
do you think that any problems with this installation might create problems for my XP ? you see i have imp data stored there.
about backup i am not sure. i once backed up several MB's of songs and then the XP simply refused to even recognise that there was anything burned on the disc. something to do with locking a disc with final a final burn within the existing OS. otherwise, other OSs' don't recognize the first data burnt.
one imp thing- if i re-install 9.04, will the installer automatically install to the existing ubuntu partition? i mean is there a chance that it will try to install itself in the XP partitions?
i have 3 XP partitions [C, D, E] and only 1 ubuntu partition
thanks!

---

