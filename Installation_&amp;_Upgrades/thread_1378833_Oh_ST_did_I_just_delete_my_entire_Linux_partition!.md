---
title: "Oh S**T did I just delete my entire Linux partition?!"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by azitizz on 2010-01-11
Hi There, Im wondering if anyoe has a quick answer as to weather upgrading my windows Vista to windows 7 using the upgrade DVD that was sent along with my computer when  bought it (Toshiba Satellite L350) completely wiped out Linux? 
I made the uneducated assumtion that it would only upgrade windows and not touch Linux, however there is no option to boot into linux anymore and when I look in Windows> My Computer, its giving me a much larger hardrive space than previously.
Any way of finding out if my Ubuntu 9.10 is still in there or at least the files etc,that were stored on there still exist?

---

### Post by wlraider70 on 2010-01-11
When you "upgrade" to windows 7 you can either

do a fresh install which clears out all the saved files.
Are all your old windows files there?

the other option is that you upgrade, and just change the system files. 
im not really experienced with grub, but its possible that you upgrade your grub away and the ubuntu is still there you just can boot into it.

I would say if you have vista personal files you have ubuntu if not its gone...

---

### Post by presence1960 on 2010-01-11
Your linux still should be there. Windows overwrote GRUB in the MBR of your hard disk so now you can only boot to windows. it is a simple matter of reinstalling GRUB.

So let's see exactly what is on your machine & your boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by efflandt on 2010-01-11
Boot your 9.10 CD and see what gparted or **sudo fdisk -l** shows for partitions on your hard drive.  Grub would be hosed (no longer in mbr, if you had it in default location), but that can be fixed if Linux is still there.

Or Computer Management in the Administration tools of Windows should show what partitions are on the drive, even if it does not know what they are (might show Linux partitions as healthy, but empty even if they are not really empty).

---

### Post by azitizz on 2010-01-11
> **wlraider70 said:**
> When you "upgrade" to windows 7 you can either

do a fresh install which clears out all the saved files.
Are all your old windows files there?

the other option is that you upgrade, and just change the system files. 
im not really experienced with grub, but its possible that you upgrade your grub away and the ubuntu is still there you just can boot into it.

I would say if you have vista personal files you have ubuntu if not its gone...

Well, that sounds a little hopeful. I just did an upgrade and kept all my old files and settings from Windows Vista and simply upgraded the system to windows 7. It wasnt a clean install.

---

### Post by presence1960 on 2010-01-11
> **azitizz said:**
> Well, that sounds a little hopeful. I just did an upgrade and kept all my old files and settings from Windows Vista and simply upgraded the system to windows 7. It wasnt a clean install.

Let's not guess or deal with maybe. Run the script and we'll see exactly what is on your machine. If your linux partitions are still there it is a simple matter of running two commands from terminal to get GRUB back on MBR and dual booting. But I need the info from the script please.

---

### Post by azitizz on 2010-01-11
Phew, great! Thank you presence1960. I will indeed follow your advice. I have to leave the computer now, but I can go to bed and sleep much better knowing I never wiped everything out. (most of it is backed up but not all)
Ill be back tomorrow to follow through.
Thanks again for the quick replies.!
I also dont have a boot disc with me or a usb starter and I literally have to hit the hay.

---

### Post by presence1960 on 2010-01-11
> **azitizz said:**
> Phew, great! Thank you presence1960. I will indeed follow your advice. I have to leave the computer now, but I can go to bed and sleep much better knowing I never wiped everything out. (most of it is backed up but not all)
Ill be back tomorrow to follow through.
Thanks again for the quick replies.!

no problem once we get that info you should be up & running in 5 minutes!

If you're savvy here is the guide: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
Use the simplest method.

---

### Post by azitizz on 2010-01-12
> **presence1960 said:**
> Your linux still should be there. Windows overwrote GRUB in the MBR of your hard disk so now you can only boot to windows. it is a simple matter of reinstalling GRUB.

So let's see exactly what is on your machine & your boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Hi Im back. I tried running the script you gave but I just get an error message saying "***bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory***"

So I tried efflandt's suggestion in the following post and heres what came up: ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x424dc7a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       14738   116841750    7  HPFS/NTFS
/dev/sda3   *       29294       30402     8899584   17  Hidden HPFS/NTFS
/dev/sda4           14739       29293   116913037+   5  Extended
/dev/sda5           14739       28696   112117603+  83  Linux
/dev/sda6           28697       29293     4795371   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders
Units = cylinders of 2250 * 512 = 1152000 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           4        3487     3917824    b  W95 FAT32

```
It looks to me like theres still linux am I right? What to do to get GRUB back up and running?

---

### Post by presence1960 on 2010-01-12
> **azitizz said:**
> Hi Im back. I tried running the script you gave but I just get an error message saying "***bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory***"

So I tried efflandt's suggestion in the following post and heres what came up: ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x424dc7a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       14738   116841750    7  HPFS/NTFS
/dev/sda3   *       29294       30402     8899584   17  Hidden HPFS/NTFS
/dev/sda4           14739       29293   116913037+   5  Extended
/dev/sda5           14739       28696   112117603+  83  Linux
/dev/sda6           28697       29293     4795371   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders
Units = cylinders of 2250 * 512 = 1152000 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           4        3487     3917824    b  W95 FAT32

```
It looks to me like theres still linux am I right? What to do to get GRUB back up and running?
The script you downloaded needs to be on the desktop when you run that command. I needed that info to see which version of Ubuntu & which version of GRUB you have. So I will provide instructions for legacy GRUB 0.97 & GRUB2 (version 1.97). 

Do this to reinstall GRUB2:

Boot the 9.10 Live CD and choose "try ubuntu without any changes...", when the desktop loads open a terminal and run ```
sudo mount /dev/sda5 /mnt
```
This will mount your ubuntu / partition.
next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
This will put GRUB2 on MBR of sda. Reboot without the Live CD and boot into Ubuntu. When the desktop loads open a terminal and run ```
sudo update-grub
```
to refresh the GRUB menu.

If you have GRUB Legacy (0.97) do this:

1. Boot your computer up with Ubuntu CD & choose "try ubuntu without any changes".
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

You may have to edit menu.lst to add a windows entry to GRUB. If you need to do that post back it will take all of 2 minutes to add it.

---

### Post by azitizz on 2010-01-12
OK, I dont know how I missed the downloading the Boot script but thats what I was missing obviously. Here is the .txt results:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x424dc7a7

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   236,757,547   233,683,500   7 HPFS/NTFS
/dev/sda3    *    470,597,632   488,396,799    17,799,168  17 Hidden HPFS/NTFS
/dev/sda4         236,765,970   470,592,044   233,826,075   5 Extended
/dev/sda5         236,766,033   461,001,239   224,235,207  83 Linux
/dev/sda6         461,001,303   470,592,044     9,590,742  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     7,843,839     7,835,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="ad57245a-5980-814c-93c6-722cc6344bea" TYPE="ext2" 
/dev/sda1: UUID="8C348E52348E3F68" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="1E96BDD596BDADA1" LABEL="S3A6748D007" TYPE="ntfs" 
/dev/sda3: UUID="EC7AEF1B7AEEE176" LABEL="HDDRECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="6afedf78-67f8-408a-b538-9213e79a68a2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="2053c9b7-78a9-493b-bea2-8af55a334bd5" TYPE="swap" 
/dev/sdb1: UUID="0648-C392" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6afedf78-67f8-408a-b538-9213e79a68a2

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=6afedf78-67f8-408a-b538-9213e79a68a2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2053c9b7-78a9-493b-bea2-8af55a334bd5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 121.2GB: boot/grub/menu.lst
 121.2GB: boot/grub/stage2
 121.2GB: boot/initrd.img-2.6.28-16-generic
 121.2GB: boot/initrd.img-2.6.31-14-generic
 121.2GB: boot/initrd.img-2.6.31-15-generic
 121.2GB: boot/initrd.img-2.6.31-16-generic
 121.2GB: boot/initrd.img-2.6.31-17-generic
 121.2GB: boot/vmlinuz-2.6.28-16-generic
 121.2GB: boot/vmlinuz-2.6.31-14-generic
 121.2GB: boot/vmlinuz-2.6.31-15-generic
 121.2GB: boot/vmlinuz-2.6.31-16-generic
 121.2GB: boot/vmlinuz-2.6.31-17-generic
 121.2GB: initrd.img
 121.2GB: initrd.img.old
 121.2GB: vmlinuz
 121.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```
I have Ubuntu 9.10 on a USB stick as it was easier to make without using a CD it seemed.
Thanks for the help.

---

### Post by presence1960 on 2010-01-12
> **azitizz said:**
> OK, I dont know how I missed the downloading the Boot script but thats what I was missing obviously. Here is the .txt results:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x424dc7a7

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   236,757,547   233,683,500   7 HPFS/NTFS
/dev/sda3    *    470,597,632   488,396,799    17,799,168  17 Hidden HPFS/NTFS
/dev/sda4         236,765,970   470,592,044   233,826,075   5 Extended
/dev/sda5         236,766,033   461,001,239   224,235,207  83 Linux
/dev/sda6         461,001,303   470,592,044     9,590,742  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     7,843,839     7,835,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="ad57245a-5980-814c-93c6-722cc6344bea" TYPE="ext2" 
/dev/sda1: UUID="8C348E52348E3F68" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="1E96BDD596BDADA1" LABEL="S3A6748D007" TYPE="ntfs" 
/dev/sda3: UUID="EC7AEF1B7AEEE176" LABEL="HDDRECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="6afedf78-67f8-408a-b538-9213e79a68a2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="2053c9b7-78a9-493b-bea2-8af55a334bd5" TYPE="swap" 
/dev/sdb1: UUID="0648-C392" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6afedf78-67f8-408a-b538-9213e79a68a2

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=6afedf78-67f8-408a-b538-9213e79a68a2 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		6afedf78-67f8-408a-b538-9213e79a68a2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=6afedf78-67f8-408a-b538-9213e79a68a2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2053c9b7-78a9-493b-bea2-8af55a334bd5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 121.2GB: boot/grub/menu.lst
 121.2GB: boot/grub/stage2
 121.2GB: boot/initrd.img-2.6.28-16-generic
 121.2GB: boot/initrd.img-2.6.31-14-generic
 121.2GB: boot/initrd.img-2.6.31-15-generic
 121.2GB: boot/initrd.img-2.6.31-16-generic
 121.2GB: boot/initrd.img-2.6.31-17-generic
 121.2GB: boot/vmlinuz-2.6.28-16-generic
 121.2GB: boot/vmlinuz-2.6.31-14-generic
 121.2GB: boot/vmlinuz-2.6.31-15-generic
 121.2GB: boot/vmlinuz-2.6.31-16-generic
 121.2GB: boot/vmlinuz-2.6.31-17-generic
 121.2GB: initrd.img
 121.2GB: initrd.img.old
 121.2GB: vmlinuz
 121.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```
I have Ubuntu 9.10 on a USB stick as it was easier to make without using a CD it seemed.
Thanks for the help.
Use the instructions for GRUB Legacy 0.97 because you have a menu.lst

I am not sure if that will work with a 9.10 Live CD. If it does not download and burn a 9.04 Live CD.

---

### Post by azitizz on 2010-01-12
> **presence1960 said:**
> Use the instructions for GRUB Legacy 0.97 because you have a menu.lst

I am not sure if that will work with a 9.10 Live CD. If it does not download and burn a 9.04 Live CD.

Ooops, So I jumped the gun and went ahead and followed the instructions for GRUB 2. Now it wont boot to anything but a terminal like screen. I tried following the instructions for GRUB Legacy 0.97 but as soon as I do the first step: typ in sudo grub, it gives me an error msg saying: "command not found."
 Is there any way to "undo whatever I did with the GRUB 2 install (if thats indeed the problem? Because as it stands I cant download a live 9.04 CD (or perhaps I can from the live 9.10 USB Image Im using? if so it will take a while as my connection isnt very fast)

---

### Post by presence1960 on 2010-01-13
> **azitizz said:**
> Ooops, So I jumped the gun and went ahead and followed the instructions for GRUB 2. Now it wont boot to anything but a terminal like screen. I tried following the instructions for GRUB Legacy 0.97 but as soon as I do the first step: typ in sudo grub, it gives me an error msg saying: "command not found."
 Is there any way to "undo whatever I did with the GRUB 2 install (if thats indeed the problem? Because as it stands I cant download a live 9.04 CD (or perhaps I can from the live 9.10 USB Image Im using? if so it will take a while as my connection isnt very fast)

The 9.10 Live CD does not contain GRUB Legacy 0.97. You are going to need a 9.04 Live CD to set up GRUB 0.97

IMHO one of the mistakes of upgrading to 9.10 is the option to keep Legacy GRUB.

---

### Post by azitizz on 2010-01-13
Ahhhhh! Thank you! it works, I can acess ubuntu as I could before now. Thank you! I see that under "other operating systems" in teh boot menu it only says windows Vista even though I upgraded to Windows 7. Not sure if that has anything to do withanything but Ill try and log in now to see what happens in windows.
Again Thank you so much for the help
Michael

---

### Post by presence1960 on 2010-01-13
You can change the title of windows in GRUB menu. Boot into Ubuntu, open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll down to
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```
 change the title only for example:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
[COLOR="Red"]title		Windows 7[/COLOR]
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```

Click Save on top toolbar. Close file. next time you boot it will give windows 7 as option to boot.

---

### Post by nirvana21 on 2010-01-29
Hi, I am in a similar situation to the original poster. The other day I was playing a game in Windows and my motherboard died. Windows was than corrupt and unrecoverable so I reinstalled it on a different partition. When I did this is it overwrote my GRUB bootloader. What I think complicates this situation is that I am running a RAID 0 array of 2 disks. 

I have tried to fix it myself from various threads including this one. I tried doing:
```
grub
find /boot/grub/stage1
```
This gives me a file not found error.

I believe I should reinstall grub 0.97 because I already have a menu.lst. I could upgrade to grub 2 if you guys think I should. Anyway, I did ran that script and here is the output. Thank you for your help in advance!:D

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/mapper/pdc_fgibjjhd
pdc_fgibjjhd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_fgibjjhd5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

pdc_fgibjjhd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_fgibjjhd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

pdc_fgibjjhd3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: pdc_fgibjjhd ___________________ _____________________________________________________

Disk /dev/mapper/pdc_fgibjjhd: 1280.0 GB, 1280000000000 bytes
255 heads, 63 sectors/track, 155617 cylinders, total 2500000000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb13aab78

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_fgibjjhd1                 63 1,250,001,584 1,250,001,522   5 Extended
/dev/mapper/pdc_fgibjjhd5                126 1,226,675,204 1,226,675,079  83 Linux
/dev/mapper/pdc_fgibjjhd6      1,226,675,268 1,250,001,584    23,326,317  82 Linux swap / Solaris
/dev/mapper/pdc_fgibjjhd2   *  1,250,002,944 2,189,996,864   939,993,921   7 HPFS/NTFS
/dev/mapper/pdc_fgibjjhd3      2,189,998,080 2,499,997,695   309,999,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_fgibjjhd2 CE38CD6138CD48E3                       ntfs                                     
/dev/mapper/pdc_fgibjjhd3 30C05D7FC05D4BEA                       ntfs                                     
/dev/mapper/pdc_fgibjjhd5 e5971498-1bdb-4af2-88eb-2b0f8d4f6451   ext3                                     
/dev/mapper/pdc_fgibjjhd6 40686571-77a1-41bf-99f4-e4c8d25d6eec   swap                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb2                                               promise_fasttrack_raid_member                               

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_fgibjjhd
pdc_fgibjjhd2
pdc_fgibjjhd3
pdc_fgibjjhd5
pdc_fgibjjhd6

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/mapper/pdc_fgibjjhd5 /media/e5971498-1bdb-4af2-88eb-2b0f8d4f6451 ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/mapper/pdc_fgibjjhd3 /media/30C05D7FC05D4BEA  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


====================== pdc_fgibjjhd5/boot/grub/menu.lst: ======================

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
# kopt=root=/dev/mapper/pdc_fgibjjhd5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-17-generic root=/dev/mapper/pdc_fgibjjhd5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-17-generic root=/dev/mapper/pdc_fgibjjhd5 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-16-generic root=/dev/mapper/pdc_fgibjjhd5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-16-generic root=/dev/mapper/pdc_fgibjjhd5 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/mapper/pdc_fgibjjhd5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/mapper/pdc_fgibjjhd5 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/mapper/pdc_fgibjjhd5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/mapper/pdc_fgibjjhd5 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/mapper/pdc_fgibjjhd1
title		Windows Vista (loader) OLD?
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=========================== pdc_fgibjjhd5/etc/fstab: ===========================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/pdc_fgibjjhd5 during installation
UUID=e5971498-1bdb-4af2-88eb-2b0f8d4f6451 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/mapper/pdc_fgibjjhd6 during installation
UUID=40686571-77a1-41bf-99f4-e4c8d25d6eec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=============== pdc_fgibjjhd5: Location of files loaded by Grub: ===============


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-11-generic
    .0GB: boot/initrd.img-2.6.28-15-generic
    .0GB: boot/initrd.img-2.6.28-16-generic
    .0GB: boot/initrd.img-2.6.28-17-generic
    .0GB: boot/vmlinuz-2.6.28-11-generic
    .0GB: boot/vmlinuz-2.6.28-15-generic
    .0GB: boot/vmlinuz-2.6.28-16-generic
    .0GB: boot/vmlinuz-2.6.28-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on pdc_fgibjjhd1



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/pdc_fgibjjhd1: No such file or directory
hexdump: /dev/mapper/pdc_fgibjjhd1: No such file or directory
```

So I have 2 Windows partitions, 1 Ubuntu, and the swap all the same RAID array.

---

### Post by meierfra. on 2010-01-29
Try this

```

sudo grub --no-curses
```

and at the grub prompt:

```

device (hd0) /dev/mapper/pdc_fgibjjhd
find /boot/grub/stage1  # this should return (hd0,4)
root (hd0,4)
setup (hd0)
quit

```

---

### Post by nirvana21 on 2010-01-29
Excellent, it works perfect! Thank you very much meierfra.!

---

### Post by meierfra. on 2010-01-29
> Excellent, it works perfect! 
Great. 
Only yesterday I upgraded the boot info script so what it can handle fakeraid.  So I was pleased to see that the script was able to read all  your partitions. (Still needs a little tweaking: the script tried to read your extended partition and threw out error messages)

---

