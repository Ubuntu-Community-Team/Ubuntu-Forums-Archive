---
title: "dual boot newby - messed up paritioning? can't update"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by tptmrk on 2009-12-28
Trying to dual boot with Windows XP and Ubuntu 9.04.  I read up a bunch of posts and guides and thought I had a clue.  I physically switched my drives and wanted to put Ubuntu on the master and keep XP on the slave.  During installation i picked the option for dual booting. Ubuntu booted and the Update Manager ran. When clicking Install Updates on the Update Manager it says:

"The upgrade needs a total of 489M free space on disk '/'. Please free at least an additional 489M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

There was no trash and I ran running 'sudo apt-get clean'. Poking around on this forum I found that I should run sudo fdisk -l and see what it says.  

Disk /dev/sda: 250.0 GB, 250059350016 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30075   241577406    7  HPFS/NTFS
/dev/sda2           30076       30401     2618595    5  Extended
/dev/sda5           30076       30379     2441848+  83  Linux
/dev/sda6           30380       30401      176683+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

I understand that it kept most of sda NTFS and I believe I can either run GParted to somehow make the whole thing formatted for Linux or I can do a clean install. 
Will either/both of these options solve the problem?
If it's better or easier to reinstall, will selecting the option to format the whole sda drive still allow me to dual boot with XP?
If going with GParted (there is nothing on sda's ntfs i need to keep) and I just want the whole thing Linux how should I set up the partitions?

Thanks for the help.

---

### Post by raymondh on 2009-12-28
What is on sdb1?  Where is your XP install? If XP is on sdb1, what is on sda1?

Neverthless, you will have to take space from sda1 (shrink it) and then enlarge sda2 and then sda5 ... in that order. Enlarging (in this case) is grabbing the left border and dragging that border to the left.

XP's disk utility will not shrink.  You can use gparted from the liveCD and in live session.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Back-up your files.  Defrag windows (sda1) twice, if you have the time.

---

### Post by tptmrk on 2009-12-28
sdb1 is the disk with Windows XP

sda used to have a bunch of audio files that have been backed up. I don't need anything that was on sda1.  Can I get rid of it or make it super small? Or is that where necessary boot info is?

It gave me the option to move things over from Windows and I said ok. I just went through and deleted all the documents in the home folder that were taking up tons of space on the sda drive.  It sounds like sda5 is basically the "disk '/'" that needs more space.

---

### Post by presence1960 on 2009-12-28
My friend Raymond is not logged in I see. Before you go removing or deleting partitions let's see exactly what you have on that rig.

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by tptmrk on 2009-12-29
hehehe... I tried gparted from a Live Session: shrunk sda1, couldn't figure out how to make the next partition bigger, and ended up with creating another partition in that space!

Seriously, I *just* installed this... would it be better to just run the install again and make a couple different selections along the way? (I'm still not sure if I can tell it to just use the entire sda disk and still have it set up a dual boot using the XP installed on sdb)

```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a5bc77b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    21,253,994    21,253,932   7 HPFS/NTFS
/dev/sda2         483,154,875   488,392,064     5,237,190   5 Extended
/dev/sda5         483,154,938   488,038,634     4,883,697  83 Linux
/dev/sda6         488,038,698   488,392,064       353,367  82 Linux swap / Solaris
/dev/sda3          21,253,995   483,154,874   461,900,880  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91499149

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3670EF4C70EF1183" LABEL="DRV2_VOL1" TYPE="ntfs" 
/dev/sda3: UUID="58d17f83-3ef3-4ad9-865d-d9d169d2aa59" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="0d08d4e4-b7d1-4d27-a6c0-a34f788da949" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="2ede78d0-622d-4ecc-b2c0-284faffa9883" TYPE="swap" 
/dev/sdb1: UUID="0AD86509D864F3FB" TYPE="ntfs" 

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
# kopt=root=UUID=0d08d4e4-b7d1-4d27-a6c0-a34f788da949 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0d08d4e4-b7d1-4d27-a6c0-a34f788da949

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        0d08d4e4-b7d1-4d27-a6c0-a34f788da949
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0d08d4e4-b7d1-4d27-a6c0-a34f788da949 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        0d08d4e4-b7d1-4d27-a6c0-a34f788da949
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0d08d4e4-b7d1-4d27-a6c0-a34f788da949 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        0d08d4e4-b7d1-4d27-a6c0-a34f788da949
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional Edition
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


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
UUID=0d08d4e4-b7d1-4d27-a6c0-a34f788da949 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2ede78d0-622d-4ecc-b2c0-284faffa9883 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 249.0GB: boot/grub/menu.lst
 249.0GB: boot/grub/stage2
 249.0GB: boot/initrd.img-2.6.28-11-generic
 248.6GB: boot/vmlinuz-2.6.28-11-generic
 249.0GB: initrd.img
 248.6GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional Edition" /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by presence1960 on 2009-12-29
You have 2 options.

1. Delete the sda1 partition using gparted from the Live CD. Next you want to right click on sda2 (from gparted) and choose Resize/Move. Then grab the left border with pointer and drag it to the left adding space to the extended partition sda2. Click Apply (green check mark @ top toolbar). Let that run it may take a while to complete.

When that completes right click sda5 and choose Resize/Move and add that space to sda5, then click the Apply green check mark again.

2. Since your Ubuntu is on sda and windows is on sdb if you don't mind reinstalling you can reinstall using the use entire disk option. Just make sure you select the proper disk (sda) in the drop down box.

---

### Post by raymondh on 2009-12-29
> **presence1960 said:**
> You have 2 options.

1. Delete the sda1 partition using gparted from the Live CD. Next you want to right click on sda2 (from gparted) and choose Resize/Move. Then grab the left border with pointer and drag it to the left adding space to the extended partition sda2. Click Apply (green check mark @ top toolbar). Let that run it may take a while to complete.

When that completes right click sda5 and choose Resize/Move and add that space to sda5, then click the Apply green check mark again.

2. Since your Ubuntu is on sda and windows is on sdb if you don't mind reinstalling you can reinstall using the use entire disk option. Just make sure you select the proper disk (sda) in the drop down box.

+1.  Thanks Presence1960 :)

---

