---
title: "Ubuntu 9.10 Stalls on Bootup"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by entelechi on 2010-01-18
Hello,

I am a code ignorant Ubuntu newb that has been using ubuntu for about a year. I have been able to solve any issue prior to this with simple web searches but I cannot find any solution to my current problem. Ubuntu would boot fine untill I upgraded to 9.10. Initially it would load up to the logo prior to the flash screen and just stall. It would boot up after a few reboots. Now it gets stuck at the logo screen a refuses to boot up. I can't find a similar problem anywhere on the web. If there is and the problem has been solved, please refer me to the url. Otherwise, any ideas? Agian I have tried virtually every other solution. Also, I have not been able to exactly match my problem with others. Booting into recovery mode yields the 'filesystem failed to mount' response.


Computer Specs:

MSI X58 Eclipse SLI LGA 1366 Intel X58 ATX Intel Motherboard

(CORSAIR XMS3 6GB (3 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666) Triple Channel Kit Desktop Memory Model TR3X6G1333C9) x2

LG Black Super Multi Blu-ray Disc Burner & HD DVD-ROM Drive SATA Model 

Creative Sound Blaster X-Fi Elite Pro 70SB055A00000 7.1 Channels PCI Interface Sound Card (Black/Silver) (Eng) - Retail (N82E16829102015)

Intel Core i7 920 Nehalem 2.66GHz LGA 1366 130W Quad-Core Processor Model BX80601920 - Retail (N82E16819115202)

Western Digital Caviar Black WD1001FALS 1TB 7200 RPM SATA 3.0Gb/s Hard Drive

IKONIK Vulcan 1200W IP-IK20A-AAAA 1200W ATX12V V2.3 / EPS12V V2.91 SLI Ready CrossFire Ready 80 PLUS BRONZE Certified Modular Active PFC Power Supply

---

### Post by tachuela on 2010-01-18
Post:
```
sudo fdisk -lu
```

---

### Post by entelechi on 2010-01-18
UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY.

I have performed this operation with no avail.

fsck yields:

/dev/sda1 contains a file system with errors, check forced.

Mind you that none of this occured prior to Ubuntu 9.10. Also, XP boots fine on the same macine with a different hard drive. Ideas?

Also, sometimes the graphic is messed up when it stalls.

---

### Post by efflandt on 2010-01-18
It sounds like either something may have corrupted your hard drive or it is failing.  Corrupted graphics, stalls, and failed fsck do not sound promising.

Back up anything you have not already backed up, and check it with the WD diagnostic utility from [http://www.wdc.com/](http://www.wdc.com/) which you will need if it is covered under warranty.

---

### Post by entelechi on 2010-01-18
This all started with the upgrade to Karmic Koala. I have run the disk check and it came back as being fine. Could it be in the partition size? I have it set as the entire disk. What is the proper partition size for Ubuntu v9.10? Why does it fail to load only occasionally? I can read the data from the windows partition. I really don't think the disk is corrupted. The flash screen seems to have given others some problems booting. I think that is what is causing the malfunction...

---

### Post by presence1960 on 2010-01-18
Did you do a dist-upgrade or a clean install of 9.10?

While you are at it we need to see more specific info about your setup and boot process. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by entelechi on 2010-01-19
Thank you for the response. I tried the above proceedure and command but it yielded the 'no such file or directory' response. Am I doing something wrong?

It finally decided to boot up after running the disk check utility. This is why this error is so unusual because it is selective if it boots up or does not. Again, it stalls immediately prior to the flash screen and that is what is new to 9.10. The error did not occur prior to the 9.10 dist-upgrade from 9.4. Is there anyway to disable the flash intro? Any insights would be useful.

Thanks again.

---

### Post by a2z on 2010-01-19
I'd like to add that I to am experiencing this exact same problem. I just did a sudo apt-get update about an hour ago. When I rebooted I get the same error. Something went wrong with the most recent upgrade.
Everything worked great as per my last post earlier today.(prior to the upgrade)
HELP!:popcorn:

a2z
Oh, I'm online via booted  jaunty cd

---

### Post by presence1960 on 2010-01-19
> **entelechi said:**
> Thank you for the response. I tried the above proceedure and command but it yielded the 'no such file or directory' response. Am I doing something wrong?

It finally decided to boot up after running the disk check utility. This is why this error is so unusual because it is selective if it boots up or does not. Again, it stalls immediately prior to the flash screen and that is what is new to 9.10. The error did not occur prior to the 9.10 dist-upgrade from 9.4. Is there anyway to disable the flash intro? Any insights would be useful.

Thanks again.

After you downloaded the boot info script did you move it to the desktop? Then run that command from terminal!

---

### Post by a2z on 2010-01-19
here's mine

```


============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #5 for /grub/stage2 and /grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd
 => No known boot loader is installed in the MBR of /dev/sde
 => No known boot loader is installed in the MBR of /dev/sdf
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 974695680.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sde1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

sde2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x25fd25fd

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   974,695,679   974,695,617  83 Linux
/dev/sda2         974,695,680   975,788,099     1,092,420   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xba7572fd

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    21,478,904    21,478,842  83 Linux
/dev/sdb2          21,478,905    60,548,984    39,070,080   5 Extended
/dev/sdb5          21,478,968    60,548,984    39,070,017  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 34.4 GB, 34359738368 bytes
64 heads, 32 sectors/track, 32768 cylinders, total 67108864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c6b7369

Partition  Boot         Start           End          Size  Id System

/dev/sdc1     ? 1,936,028,272 3,787,887,330 1,851,859,059  68 Unknown
/dev/sdc2     ? 1,330,184,192 1,869,160,479   538,976,288  79 Unknown
/dev/sdc3     ?   538,989,391 1,937,352,302 1,398,362,912  53 OnTrack DM6 Aux3
/dev/sdc4     ? 1,394,627,663 1,394,648,999        21,337  49 Unknown

/dev/sdc1 ends after the last sector of /dev/sdc
/dev/sdc1 overlaps with /dev/sdc3
/dev/sdc2 ends after the last sector of /dev/sdc
/dev/sdc2 overlaps with /dev/sdc3
/dev/sdc2 overlaps with /dev/sdc4
/dev/sdc3 ends after the last sector of /dev/sdc
/dev/sdc3 overlaps with /dev/sdc4
/dev/sdc4 ends after the last sector of /dev/sdc

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 33.6 GB, 33567958528 bytes
255 heads, 63 sectors/track, 4081 cylinders, total 65562419 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f00736b

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    65,561,264    65,561,202  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 34.4 GB, 34359738368 bytes
64 heads, 32 sectors/track, 32768 cylinders, total 67108864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c6b7369

Partition  Boot         Start           End          Size  Id System

/dev/sde1     ? 1,936,028,272 3,787,887,330 1,851,859,059  68 Unknown
/dev/sde2     ? 1,330,184,192 1,869,160,479   538,976,288  79 Unknown
/dev/sde3     ?   538,989,391 1,937,352,302 1,398,362,912  53 OnTrack DM6 Aux3
/dev/sde4     ? 1,394,627,663 1,394,648,999        21,337  49 Unknown

/dev/sde1 ends after the last sector of /dev/sde
/dev/sde1 overlaps with /dev/sde3
/dev/sde2 ends after the last sector of /dev/sde
/dev/sde2 overlaps with /dev/sde3
/dev/sde2 overlaps with /dev/sde4
/dev/sde3 ends after the last sector of /dev/sde
/dev/sde3 overlaps with /dev/sde4
/dev/sde4 ends after the last sector of /dev/sde

Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 34.4 GB, 34359738368 bytes
64 heads, 32 sectors/track, 32768 cylinders, total 67108864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c6b7369

Partition  Boot         Start           End          Size  Id System

/dev/sdf1     ? 1,936,028,272 3,787,887,330 1,851,859,059  68 Unknown
/dev/sdf2     ? 1,330,184,192 1,869,160,479   538,976,288  79 Unknown
/dev/sdf3     ?   538,989,391 1,937,352,302 1,398,362,912  53 OnTrack DM6 Aux3
/dev/sdf4     ? 1,394,627,663 1,394,648,999        21,337  49 Unknown

/dev/sdf1 ends after the last sector of /dev/sdf
/dev/sdf1 overlaps with /dev/sdf3
/dev/sdf2 ends after the last sector of /dev/sdf
/dev/sdf2 overlaps with /dev/sdf3
/dev/sdf2 overlaps with /dev/sdf4
/dev/sdf3 ends after the last sector of /dev/sdf
/dev/sdf3 overlaps with /dev/sdf4
/dev/sdf4 ends after the last sector of /dev/sdf

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="bd337a60-4000-4859-97fe-cb5286adfb27" TYPE="ext4" 
/dev/sda2: LABEL="" UUID="A7F9-E9A0" TYPE="vfat" 
/dev/sdb1: UUID="5ceb94e8-3325-4b30-ac59-814fb0f14cc3" TYPE="ext3" 
/dev/sdb5: UUID="ef945356-05aa-45ed-8de3-c2551abfe10f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc: UUID="2022-62E3" TYPE="vfat" 
/dev/sdd1: LABEL="Movies" UUID="c142f5aa-2b4b-4cf2-a065-9b44100d6642" TYPE="ext4" 
/dev/sde: UUID="2022-62E3" TYPE="vfat" 
/dev/sdf: UUID="2022-62E3" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sde on /media/2022-62E3 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=lower,dmask=0077,utf8=1,flush)
/dev/sdc on /media/2022-62E3_ type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=lower,dmask=0077,utf8=1,flush)
/dev/sdf on /media/2022-62E3__ type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=lower,dmask=0077,utf8=1,flush)
/dev/sda1 on /media/bd337a60-4000-4859-97fe-cb5286adfb27 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1 on /media/5ceb94e8-3325-4b30-ac59-814fb0f14cc3 type ext3 (rw,nosuid,nodev,uhelper=devkit)


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
# kopt=root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5ceb94e8-3325-4b30-ac59-814fb0f14cc3

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
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.28-17-generic
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.10, memtest86+
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=ef945356-05aa-45ed-8de3-c2551abfe10f /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=c1de03fa-eb25-4e4e-9c59-a4edd850adc5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-17-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.28-17-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 20 30 00  |.X.MSWIN4.1.. 0.|
00000010  02 00 00 00 00 f0 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 00 04 f8 3f 00 00  00 00 00 00 02 00 00 00  |.....?..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e3 62 22 20 4e  4f 20 4e 41 4d 45 20 20  |..).b" NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa 33 c9 8e d1 bc  |  FAT32   .3....|
00000060  f8 7b 8e c1 bd 78 00 c5  76 00 1e 56 16 55 bf 22  |.{...x..v..V.U."|
00000070  05 89 7e 00 89 4e 02 b1  0b fc f3 a4 8e d9 bd 00  |..~..N..........|
00000080  7c c6 45 fe 0f 8b 46 18  88 45 f9 38 4e 40 7d 25  ||.E...F..E.8N@}%|
00000090  8b c1 99 bb 00 07 e8 97  00 72 1a 83 eb 3a 66 a1  |.........r...:f.|
000000a0  1c 7c 66 3b 07 8a 57 fc  75 06 80 ca 02 88 56 02  |.|f;..W.u.....V.|
000000b0  80 c3 10 73 ed bf 02 00  83 7e 16 00 75 45 8b 46  |...s.....~..uE.F|
000000c0  1c 8b 56 1e b9 03 00 49  40 75 01 42 bb 00 7e e8  |..V....I@u.B..~.|
000000d0  5f 00 73 26 b0 f8 4f 74  1d 8b 46 32 33 d2 b9 03  |_.s&..Ot..F23...|
000000e0  00 3b c8 77 1e 8b 76 0e  3b ce 73 17 2b f1 03 46  |.;.w..v.;.s.+..F|
000000f0  1c 13 56 1e eb d1 73 0b  eb 27 83 7e 2a 00 77 03  |..V...s..'.~*.w.|
00000100  e9 fd 02 be 7e 7d ac 98  03 f0 ac 84 c0 74 17 3c  |....~}.......t.<|
00000110  ff 74 09 b4 0e bb 07 00  cd 10 eb ee be 81 7d eb  |.t............}.|
00000120  e5 be 7f 7d eb e0 98 cd  16 5e 1f 66 8f 04 cd 19  |...}.....^.f....|
00000130  41 56 66 6a 00 52 50 06  53 6a 01 6a 10 8b f4 60  |AVfj.RP.Sj.j...`|
00000140  80 7e 02 0e 75 04 b4 42  eb 1d 91 92 33 d2 f7 76  |.~..u..B....3..v|
00000150  18 91 f7 76 18 42 87 ca  f7 76 1a 8a f2 8a e8 c0  |...v.B...v......|
00000160  cc 02 0a cc b8 01 02 8a  56 40 cd 13 61 8d 64 10  |........V@..a.d.|
00000170  5e 72 0a 40 75 01 42 03  5e 0b 49 75 b4 c3 03 18  |^r.@u.B.^.Iu....|
00000180  01 27 0d 0a 49 6e 76 61  6c 69 64 20 73 79 73 74  |.'..Invalid syst|
00000190  65 6d 20 64 69 73 6b ff  0d 0a 44 69 73 6b 20 49  |em disk...Disk I|
000001a0  2f 4f 20 65 72 72 6f 72  ff 0d 0a 52 65 70 6c 61  |/O error...Repla|
000001b0  63 65 20 74 68 65 20 64  69 73 6b 2c 20 61 6e 64  |ce the disk, and|
000001c0  20 74 68 65 6e 20 70 72  65 73 73 20 61 6e 79 20  | then press any |
000001d0  6b 65 79 0d 0a 00 00 00  49 4f 20 20 20 20 20 20  |key.....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7e 01  |SYSMSDOS   SYS~.|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

Unknown MBR on /dev/sdd

00000000  cb 58 90 00 53 40 4f 53  35 2e 30 00 02 20 22 00  |.X..S@OS5.0.. ".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  33 66 e8 03 7f 3e 00 00  00 00 00 00 02 00 00 00  |3f...>..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 40 62 1c 14 46  4f 20 4e 41 4c 44 20 20  |..)@b..FO NALD  |
00000050  20 20 00 41 54 33 32 20  20 20 33 c9 8e d1 b4 f4  |  .AT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f e7 e2 86  cd c0 ed 06 41 66 0f 97  |....?.......Af..|
00000090  c9 66 f7 c1 66 89 46 e8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 75 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.u2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b0 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cc 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d ea e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 46 3b 46 f8 0f 82  4a 00 66 62 00 66 50 06  |f`F;F...J.fb.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0e 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 ba aa 55 8a 56 40 cd  13 0e 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 34  |.............F.4|
00000120  42 8a 52 40 8b f4 cd 03  b0 f9 66 58 66 58 66 58  |B.R@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8a d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e0 c0 e4 06 0a  cc b8 01 02 c9 13 26 61  |V@............&a|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 04 81 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 08 52 64  |..............Rd|
000001b0  6d 6f 76 65 20 24 69 73  6b 73 00 6f 72 20 00 01  |move $isks.or ..|
000001c0  01 00 83 fe ff ff 3f 00  00 00 72 62 e8 03 00 00  |......?...rb....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sde

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 20 30 00  |.X.MSWIN4.1.. 0.|
00000010  02 00 00 00 00 f0 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 00 04 f8 3f 00 00  00 00 00 00 02 00 00 00  |.....?..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e3 62 22 20 4e  4f 20 4e 41 4d 45 20 20  |..).b" NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa 33 c9 8e d1 bc  |  FAT32   .3....|
00000060  f8 7b 8e c1 bd 78 00 c5  76 00 1e 56 16 55 bf 22  |.{...x..v..V.U."|
00000070  05 89 7e 00 89 4e 02 b1  0b fc f3 a4 8e d9 bd 00  |..~..N..........|
00000080  7c c6 45 fe 0f 8b 46 18  88 45 f9 38 4e 40 7d 25  ||.E...F..E.8N@}%|
00000090  8b c1 99 bb 00 07 e8 97  00 72 1a 83 eb 3a 66 a1  |.........r...:f.|
000000a0  1c 7c 66 3b 07 8a 57 fc  75 06 80 ca 02 88 56 02  |.|f;..W.u.....V.|
000000b0  80 c3 10 73 ed bf 02 00  83 7e 16 00 75 45 8b 46  |...s.....~..uE.F|
000000c0  1c 8b 56 1e b9 03 00 49  40 75 01 42 bb 00 7e e8  |..V....I@u.B..~.|
000000d0  5f 00 73 26 b0 f8 4f 74  1d 8b 46 32 33 d2 b9 03  |_.s&..Ot..F23...|
000000e0  00 3b c8 77 1e 8b 76 0e  3b ce 73 17 2b f1 03 46  |.;.w..v.;.s.+..F|
000000f0  1c 13 56 1e eb d1 73 0b  eb 27 83 7e 2a 00 77 03  |..V...s..'.~*.w.|
00000100  e9 fd 02 be 7e 7d ac 98  03 f0 ac 84 c0 74 17 3c  |....~}.......t.<|
00000110  ff 74 09 b4 0e bb 07 00  cd 10 eb ee be 81 7d eb  |.t............}.|
00000120  e5 be 7f 7d eb e0 98 cd  16 5e 1f 66 8f 04 cd 19  |...}.....^.f....|
00000130  41 56 66 6a 00 52 50 06  53 6a 01 6a 10 8b f4 60  |AVfj.RP.Sj.j...`|
00000140  80 7e 02 0e 75 04 b4 42  eb 1d 91 92 33 d2 f7 76  |.~..u..B....3..v|
00000150  18 91 f7 76 18 42 87 ca  f7 76 1a 8a f2 8a e8 c0  |...v.B...v......|
00000160  cc 02 0a cc b8 01 02 8a  56 40 cd 13 61 8d 64 10  |........V@..a.d.|
00000170  5e 72 0a 40 75 01 42 03  5e 0b 49 75 b4 c3 03 18  |^r.@u.B.^.Iu....|
00000180  01 27 0d 0a 49 6e 76 61  6c 69 64 20 73 79 73 74  |.'..Invalid syst|
00000190  65 6d 20 64 69 73 6b ff  0d 0a 44 69 73 6b 20 49  |em disk...Disk I|
000001a0  2f 4f 20 65 72 72 6f 72  ff 0d 0a 52 65 70 6c 61  |/O error...Repla|
000001b0  63 65 20 74 68 65 20 64  69 73 6b 2c 20 61 6e 64  |ce the disk, and|
000001c0  20 74 68 65 6e 20 70 72  65 73 73 20 61 6e 79 20  | then press any |
000001d0  6b 65 79 0d 0a 00 00 00  49 4f 20 20 20 20 20 20  |key.....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7e 01  |SYSMSDOS   SYS~.|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

Unknown MBR on /dev/sdf

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 20 30 00  |.X.MSWIN4.1.. 0.|
00000010  02 00 00 00 00 f0 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 00 04 f8 3f 00 00  00 00 00 00 02 00 00 00  |.....?..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e3 62 22 20 4e  4f 20 4e 41 4d 45 20 20  |..).b" NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa 33 c9 8e d1 bc  |  FAT32   .3....|
00000060  f8 7b 8e c1 bd 78 00 c5  76 00 1e 56 16 55 bf 22  |.{...x..v..V.U."|
00000070  05 89 7e 00 89 4e 02 b1  0b fc f3 a4 8e d9 bd 00  |..~..N..........|
00000080  7c c6 45 fe 0f 8b 46 18  88 45 f9 38 4e 40 7d 25  ||.E...F..E.8N@}%|
00000090  8b c1 99 bb 00 07 e8 97  00 72 1a 83 eb 3a 66 a1  |.........r...:f.|
000000a0  1c 7c 66 3b 07 8a 57 fc  75 06 80 ca 02 88 56 02  |.|f;..W.u.....V.|
000000b0  80 c3 10 73 ed bf 02 00  83 7e 16 00 75 45 8b 46  |...s.....~..uE.F|
000000c0  1c 8b 56 1e b9 03 00 49  40 75 01 42 bb 00 7e e8  |..V....I@u.B..~.|
000000d0  5f 00 73 26 b0 f8 4f 74  1d 8b 46 32 33 d2 b9 03  |_.s&..Ot..F23...|
000000e0  00 3b c8 77 1e 8b 76 0e  3b ce 73 17 2b f1 03 46  |.;.w..v.;.s.+..F|
000000f0  1c 13 56 1e eb d1 73 0b  eb 27 83 7e 2a 00 77 03  |..V...s..'.~*.w.|
00000100  e9 fd 02 be 7e 7d ac 98  03 f0 ac 84 c0 74 17 3c  |....~}.......t.<|
00000110  ff 74 09 b4 0e bb 07 00  cd 10 eb ee be 81 7d eb  |.t............}.|
00000120  e5 be 7f 7d eb e0 98 cd  16 5e 1f 66 8f 04 cd 19  |...}.....^.f....|
00000130  41 56 66 6a 00 52 50 06  53 6a 01 6a 10 8b f4 60  |AVfj.RP.Sj.j...`|
00000140  80 7e 02 0e 75 04 b4 42  eb 1d 91 92 33 d2 f7 76  |.~..u..B....3..v|
00000150  18 91 f7 76 18 42 87 ca  f7 76 1a 8a f2 8a e8 c0  |...v.B...v......|
00000160  cc 02 0a cc b8 01 02 8a  56 40 cd 13 61 8d 64 10  |........V@..a.d.|
00000170  5e 72 0a 40 75 01 42 03  5e 0b 49 75 b4 c3 03 18  |^r.@u.B.^.Iu....|
00000180  01 27 0d 0a 49 6e 76 61  6c 69 64 20 73 79 73 74  |.'..Invalid syst|
00000190  65 6d 20 64 69 73 6b ff  0d 0a 44 69 73 6b 20 49  |em disk...Disk I|
000001a0  2f 4f 20 65 72 72 6f 72  ff 0d 0a 52 65 70 6c 61  |/O error...Repla|
000001b0  63 65 20 74 68 65 20 64  69 73 6b 2c 20 61 6e 64  |ce the disk, and|
000001c0  20 74 68 65 6e 20 70 72  65 73 73 20 61 6e 79 20  | then press any |
000001d0  6b 65 79 0d 0a 00 00 00  49 4f 20 20 20 20 20 20  |key.....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7e 01  |SYSMSDOS   SYS~.|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

Unknown BootLoader  on sdc1


Unknown BootLoader  on sdc2


Unknown BootLoader  on sdc3


Unknown BootLoader  on sdc4


Unknown BootLoader  on sde1


Unknown BootLoader  on sde2


Unknown BootLoader  on sde3


Unknown BootLoader  on sde4


Unknown BootLoader  on sdf1


Unknown BootLoader  on sdf2


Unknown BootLoader  on sdf3


Unknown BootLoader  on sdf4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sde1: No such file or directory
hexdump: /dev/sde1: No such file or directory
hexdump: /dev/sde2: No such file or directory
hexdump: /dev/sde2: No such file or directory
hexdump: /dev/sde3: No such file or directory
hexdump: /dev/sde3: No such file or directory
hexdump: /dev/sde4: No such file or directory
hexdump: /dev/sde4: No such file or directory
hexdump: /dev/sdf1: No such file or directory
hexdump: /dev/sdf1: No such file or directory
hexdump: /dev/sdf2: No such file or directory
hexdump: /dev/sdf2: No such file or directory
hexdump: /dev/sdf3: No such file or directory
hexdump: /dev/sdf3: No such file or directory
hexdump: /dev/sdf4: No such file or directory
hexdump: /dev/sdf4: No such file or directory
```

---

### Post by presence1960 on 2010-01-19
> **a2z said:**
> here's mine

```


============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #5 for /grub/stage2 and /grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd
 => No known boot loader is installed in the MBR of /dev/sde
 => No known boot loader is installed in the MBR of /dev/sdf
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 974695680.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sde1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

sde2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x25fd25fd

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   974,695,679   974,695,617  83 Linux
/dev/sda2         974,695,680   975,788,099     1,092,420   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xba7572fd

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    21,478,904    21,478,842  83 Linux
/dev/sdb2          21,478,905    60,548,984    39,070,080   5 Extended
/dev/sdb5          21,478,968    60,548,984    39,070,017  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 34.4 GB, 34359738368 bytes
64 heads, 32 sectors/track, 32768 cylinders, total 67108864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c6b7369

Partition  Boot         Start           End          Size  Id System

/dev/sdc1     ? 1,936,028,272 3,787,887,330 1,851,859,059  68 Unknown
/dev/sdc2     ? 1,330,184,192 1,869,160,479   538,976,288  79 Unknown
/dev/sdc3     ?   538,989,391 1,937,352,302 1,398,362,912  53 OnTrack DM6 Aux3
/dev/sdc4     ? 1,394,627,663 1,394,648,999        21,337  49 Unknown

/dev/sdc1 ends after the last sector of /dev/sdc
/dev/sdc1 overlaps with /dev/sdc3
/dev/sdc2 ends after the last sector of /dev/sdc
/dev/sdc2 overlaps with /dev/sdc3
/dev/sdc2 overlaps with /dev/sdc4
/dev/sdc3 ends after the last sector of /dev/sdc
/dev/sdc3 overlaps with /dev/sdc4
/dev/sdc4 ends after the last sector of /dev/sdc

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 33.6 GB, 33567958528 bytes
255 heads, 63 sectors/track, 4081 cylinders, total 65562419 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f00736b

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    65,561,264    65,561,202  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 34.4 GB, 34359738368 bytes
64 heads, 32 sectors/track, 32768 cylinders, total 67108864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c6b7369

Partition  Boot         Start           End          Size  Id System

/dev/sde1     ? 1,936,028,272 3,787,887,330 1,851,859,059  68 Unknown
/dev/sde2     ? 1,330,184,192 1,869,160,479   538,976,288  79 Unknown
/dev/sde3     ?   538,989,391 1,937,352,302 1,398,362,912  53 OnTrack DM6 Aux3
/dev/sde4     ? 1,394,627,663 1,394,648,999        21,337  49 Unknown

/dev/sde1 ends after the last sector of /dev/sde
/dev/sde1 overlaps with /dev/sde3
/dev/sde2 ends after the last sector of /dev/sde
/dev/sde2 overlaps with /dev/sde3
/dev/sde2 overlaps with /dev/sde4
/dev/sde3 ends after the last sector of /dev/sde
/dev/sde3 overlaps with /dev/sde4
/dev/sde4 ends after the last sector of /dev/sde

Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 34.4 GB, 34359738368 bytes
64 heads, 32 sectors/track, 32768 cylinders, total 67108864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c6b7369

Partition  Boot         Start           End          Size  Id System

/dev/sdf1     ? 1,936,028,272 3,787,887,330 1,851,859,059  68 Unknown
/dev/sdf2     ? 1,330,184,192 1,869,160,479   538,976,288  79 Unknown
/dev/sdf3     ?   538,989,391 1,937,352,302 1,398,362,912  53 OnTrack DM6 Aux3
/dev/sdf4     ? 1,394,627,663 1,394,648,999        21,337  49 Unknown

/dev/sdf1 ends after the last sector of /dev/sdf
/dev/sdf1 overlaps with /dev/sdf3
/dev/sdf2 ends after the last sector of /dev/sdf
/dev/sdf2 overlaps with /dev/sdf3
/dev/sdf2 overlaps with /dev/sdf4
/dev/sdf3 ends after the last sector of /dev/sdf
/dev/sdf3 overlaps with /dev/sdf4
/dev/sdf4 ends after the last sector of /dev/sdf

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="bd337a60-4000-4859-97fe-cb5286adfb27" TYPE="ext4" 
/dev/sda2: LABEL="" UUID="A7F9-E9A0" TYPE="vfat" 
/dev/sdb1: UUID="5ceb94e8-3325-4b30-ac59-814fb0f14cc3" TYPE="ext3" 
/dev/sdb5: UUID="ef945356-05aa-45ed-8de3-c2551abfe10f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc: UUID="2022-62E3" TYPE="vfat" 
/dev/sdd1: LABEL="Movies" UUID="c142f5aa-2b4b-4cf2-a065-9b44100d6642" TYPE="ext4" 
/dev/sde: UUID="2022-62E3" TYPE="vfat" 
/dev/sdf: UUID="2022-62E3" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sde on /media/2022-62E3 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=lower,dmask=0077,utf8=1,flush)
/dev/sdc on /media/2022-62E3_ type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=lower,dmask=0077,utf8=1,flush)
/dev/sdf on /media/2022-62E3__ type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=lower,dmask=0077,utf8=1,flush)
/dev/sda1 on /media/bd337a60-4000-4859-97fe-cb5286adfb27 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1 on /media/5ceb94e8-3325-4b30-ac59-814fb0f14cc3 type ext3 (rw,nosuid,nodev,uhelper=devkit)


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
# kopt=root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5ceb94e8-3325-4b30-ac59-814fb0f14cc3

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
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.28-17-generic
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.10, memtest86+
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=ef945356-05aa-45ed-8de3-c2551abfe10f /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=c1de03fa-eb25-4e4e-9c59-a4edd850adc5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-17-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.28-17-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 20 30 00  |.X.MSWIN4.1.. 0.|
00000010  02 00 00 00 00 f0 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 00 04 f8 3f 00 00  00 00 00 00 02 00 00 00  |.....?..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e3 62 22 20 4e  4f 20 4e 41 4d 45 20 20  |..).b" NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa 33 c9 8e d1 bc  |  FAT32   .3....|
00000060  f8 7b 8e c1 bd 78 00 c5  76 00 1e 56 16 55 bf 22  |.{...x..v..V.U."|
00000070  05 89 7e 00 89 4e 02 b1  0b fc f3 a4 8e d9 bd 00  |..~..N..........|
00000080  7c c6 45 fe 0f 8b 46 18  88 45 f9 38 4e 40 7d 25  ||.E...F..E.8N@}%|
00000090  8b c1 99 bb 00 07 e8 97  00 72 1a 83 eb 3a 66 a1  |.........r...:f.|
000000a0  1c 7c 66 3b 07 8a 57 fc  75 06 80 ca 02 88 56 02  |.|f;..W.u.....V.|
000000b0  80 c3 10 73 ed bf 02 00  83 7e 16 00 75 45 8b 46  |...s.....~..uE.F|
000000c0  1c 8b 56 1e b9 03 00 49  40 75 01 42 bb 00 7e e8  |..V....I@u.B..~.|
000000d0  5f 00 73 26 b0 f8 4f 74  1d 8b 46 32 33 d2 b9 03  |_.s&..Ot..F23...|
000000e0  00 3b c8 77 1e 8b 76 0e  3b ce 73 17 2b f1 03 46  |.;.w..v.;.s.+..F|
000000f0  1c 13 56 1e eb d1 73 0b  eb 27 83 7e 2a 00 77 03  |..V...s..'.~*.w.|
00000100  e9 fd 02 be 7e 7d ac 98  03 f0 ac 84 c0 74 17 3c  |....~}.......t.<|
00000110  ff 74 09 b4 0e bb 07 00  cd 10 eb ee be 81 7d eb  |.t............}.|
00000120  e5 be 7f 7d eb e0 98 cd  16 5e 1f 66 8f 04 cd 19  |...}.....^.f....|
00000130  41 56 66 6a 00 52 50 06  53 6a 01 6a 10 8b f4 60  |AVfj.RP.Sj.j...`|
00000140  80 7e 02 0e 75 04 b4 42  eb 1d 91 92 33 d2 f7 76  |.~..u..B....3..v|
00000150  18 91 f7 76 18 42 87 ca  f7 76 1a 8a f2 8a e8 c0  |...v.B...v......|
00000160  cc 02 0a cc b8 01 02 8a  56 40 cd 13 61 8d 64 10  |........V@..a.d.|
00000170  5e 72 0a 40 75 01 42 03  5e 0b 49 75 b4 c3 03 18  |^r.@u.B.^.Iu....|
00000180  01 27 0d 0a 49 6e 76 61  6c 69 64 20 73 79 73 74  |.'..Invalid syst|
00000190  65 6d 20 64 69 73 6b ff  0d 0a 44 69 73 6b 20 49  |em disk...Disk I|
000001a0  2f 4f 20 65 72 72 6f 72  ff 0d 0a 52 65 70 6c 61  |/O error...Repla|
000001b0  63 65 20 74 68 65 20 64  69 73 6b 2c 20 61 6e 64  |ce the disk, and|
000001c0  20 74 68 65 6e 20 70 72  65 73 73 20 61 6e 79 20  | then press any |
000001d0  6b 65 79 0d 0a 00 00 00  49 4f 20 20 20 20 20 20  |key.....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7e 01  |SYSMSDOS   SYS~.|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

Unknown MBR on /dev/sdd

00000000  cb 58 90 00 53 40 4f 53  35 2e 30 00 02 20 22 00  |.X..S@OS5.0.. ".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  33 66 e8 03 7f 3e 00 00  00 00 00 00 02 00 00 00  |3f...>..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 40 62 1c 14 46  4f 20 4e 41 4c 44 20 20  |..)@b..FO NALD  |
00000050  20 20 00 41 54 33 32 20  20 20 33 c9 8e d1 b4 f4  |  .AT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f e7 e2 86  cd c0 ed 06 41 66 0f 97  |....?.......Af..|
00000090  c9 66 f7 c1 66 89 46 e8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 75 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.u2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b0 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cc 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d ea e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 46 3b 46 f8 0f 82  4a 00 66 62 00 66 50 06  |f`F;F...J.fb.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0e 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 ba aa 55 8a 56 40 cd  13 0e 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 34  |.............F.4|
00000120  42 8a 52 40 8b f4 cd 03  b0 f9 66 58 66 58 66 58  |B.R@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8a d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e0 c0 e4 06 0a  cc b8 01 02 c9 13 26 61  |V@............&a|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 04 81 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 08 52 64  |..............Rd|
000001b0  6d 6f 76 65 20 24 69 73  6b 73 00 6f 72 20 00 01  |move $isks.or ..|
000001c0  01 00 83 fe ff ff 3f 00  00 00 72 62 e8 03 00 00  |......?...rb....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sde

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 20 30 00  |.X.MSWIN4.1.. 0.|
00000010  02 00 00 00 00 f0 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 00 04 f8 3f 00 00  00 00 00 00 02 00 00 00  |.....?..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e3 62 22 20 4e  4f 20 4e 41 4d 45 20 20  |..).b" NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa 33 c9 8e d1 bc  |  FAT32   .3....|
00000060  f8 7b 8e c1 bd 78 00 c5  76 00 1e 56 16 55 bf 22  |.{...x..v..V.U."|
00000070  05 89 7e 00 89 4e 02 b1  0b fc f3 a4 8e d9 bd 00  |..~..N..........|
00000080  7c c6 45 fe 0f 8b 46 18  88 45 f9 38 4e 40 7d 25  ||.E...F..E.8N@}%|
00000090  8b c1 99 bb 00 07 e8 97  00 72 1a 83 eb 3a 66 a1  |.........r...:f.|
000000a0  1c 7c 66 3b 07 8a 57 fc  75 06 80 ca 02 88 56 02  |.|f;..W.u.....V.|
000000b0  80 c3 10 73 ed bf 02 00  83 7e 16 00 75 45 8b 46  |...s.....~..uE.F|
000000c0  1c 8b 56 1e b9 03 00 49  40 75 01 42 bb 00 7e e8  |..V....I@u.B..~.|
000000d0  5f 00 73 26 b0 f8 4f 74  1d 8b 46 32 33 d2 b9 03  |_.s&..Ot..F23...|
000000e0  00 3b c8 77 1e 8b 76 0e  3b ce 73 17 2b f1 03 46  |.;.w..v.;.s.+..F|
000000f0  1c 13 56 1e eb d1 73 0b  eb 27 83 7e 2a 00 77 03  |..V...s..'.~*.w.|
00000100  e9 fd 02 be 7e 7d ac 98  03 f0 ac 84 c0 74 17 3c  |....~}.......t.<|
00000110  ff 74 09 b4 0e bb 07 00  cd 10 eb ee be 81 7d eb  |.t............}.|
00000120  e5 be 7f 7d eb e0 98 cd  16 5e 1f 66 8f 04 cd 19  |...}.....^.f....|
00000130  41 56 66 6a 00 52 50 06  53 6a 01 6a 10 8b f4 60  |AVfj.RP.Sj.j...`|
00000140  80 7e 02 0e 75 04 b4 42  eb 1d 91 92 33 d2 f7 76  |.~..u..B....3..v|
00000150  18 91 f7 76 18 42 87 ca  f7 76 1a 8a f2 8a e8 c0  |...v.B...v......|
00000160  cc 02 0a cc b8 01 02 8a  56 40 cd 13 61 8d 64 10  |........V@..a.d.|
00000170  5e 72 0a 40 75 01 42 03  5e 0b 49 75 b4 c3 03 18  |^r.@u.B.^.Iu....|
00000180  01 27 0d 0a 49 6e 76 61  6c 69 64 20 73 79 73 74  |.'..Invalid syst|
00000190  65 6d 20 64 69 73 6b ff  0d 0a 44 69 73 6b 20 49  |em disk...Disk I|
000001a0  2f 4f 20 65 72 72 6f 72  ff 0d 0a 52 65 70 6c 61  |/O error...Repla|
000001b0  63 65 20 74 68 65 20 64  69 73 6b 2c 20 61 6e 64  |ce the disk, and|
000001c0  20 74 68 65 6e 20 70 72  65 73 73 20 61 6e 79 20  | then press any |
000001d0  6b 65 79 0d 0a 00 00 00  49 4f 20 20 20 20 20 20  |key.....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7e 01  |SYSMSDOS   SYS~.|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

Unknown MBR on /dev/sdf

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 20 30 00  |.X.MSWIN4.1.. 0.|
00000010  02 00 00 00 00 f0 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 00 04 f8 3f 00 00  00 00 00 00 02 00 00 00  |.....?..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e3 62 22 20 4e  4f 20 4e 41 4d 45 20 20  |..).b" NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa 33 c9 8e d1 bc  |  FAT32   .3....|
00000060  f8 7b 8e c1 bd 78 00 c5  76 00 1e 56 16 55 bf 22  |.{...x..v..V.U."|
00000070  05 89 7e 00 89 4e 02 b1  0b fc f3 a4 8e d9 bd 00  |..~..N..........|
00000080  7c c6 45 fe 0f 8b 46 18  88 45 f9 38 4e 40 7d 25  ||.E...F..E.8N@}%|
00000090  8b c1 99 bb 00 07 e8 97  00 72 1a 83 eb 3a 66 a1  |.........r...:f.|
000000a0  1c 7c 66 3b 07 8a 57 fc  75 06 80 ca 02 88 56 02  |.|f;..W.u.....V.|
000000b0  80 c3 10 73 ed bf 02 00  83 7e 16 00 75 45 8b 46  |...s.....~..uE.F|
000000c0  1c 8b 56 1e b9 03 00 49  40 75 01 42 bb 00 7e e8  |..V....I@u.B..~.|
000000d0  5f 00 73 26 b0 f8 4f 74  1d 8b 46 32 33 d2 b9 03  |_.s&..Ot..F23...|
000000e0  00 3b c8 77 1e 8b 76 0e  3b ce 73 17 2b f1 03 46  |.;.w..v.;.s.+..F|
000000f0  1c 13 56 1e eb d1 73 0b  eb 27 83 7e 2a 00 77 03  |..V...s..'.~*.w.|
00000100  e9 fd 02 be 7e 7d ac 98  03 f0 ac 84 c0 74 17 3c  |....~}.......t.<|
00000110  ff 74 09 b4 0e bb 07 00  cd 10 eb ee be 81 7d eb  |.t............}.|
00000120  e5 be 7f 7d eb e0 98 cd  16 5e 1f 66 8f 04 cd 19  |...}.....^.f....|
00000130  41 56 66 6a 00 52 50 06  53 6a 01 6a 10 8b f4 60  |AVfj.RP.Sj.j...`|
00000140  80 7e 02 0e 75 04 b4 42  eb 1d 91 92 33 d2 f7 76  |.~..u..B....3..v|
00000150  18 91 f7 76 18 42 87 ca  f7 76 1a 8a f2 8a e8 c0  |...v.B...v......|
00000160  cc 02 0a cc b8 01 02 8a  56 40 cd 13 61 8d 64 10  |........V@..a.d.|
00000170  5e 72 0a 40 75 01 42 03  5e 0b 49 75 b4 c3 03 18  |^r.@u.B.^.Iu....|
00000180  01 27 0d 0a 49 6e 76 61  6c 69 64 20 73 79 73 74  |.'..Invalid syst|
00000190  65 6d 20 64 69 73 6b ff  0d 0a 44 69 73 6b 20 49  |em disk...Disk I|
000001a0  2f 4f 20 65 72 72 6f 72  ff 0d 0a 52 65 70 6c 61  |/O error...Repla|
000001b0  63 65 20 74 68 65 20 64  69 73 6b 2c 20 61 6e 64  |ce the disk, and|
000001c0  20 74 68 65 6e 20 70 72  65 73 73 20 61 6e 79 20  | then press any |
000001d0  6b 65 79 0d 0a 00 00 00  49 4f 20 20 20 20 20 20  |key.....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7e 01  |SYSMSDOS   SYS~.|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

Unknown BootLoader  on sdc1


Unknown BootLoader  on sdc2


Unknown BootLoader  on sdc3


Unknown BootLoader  on sdc4


Unknown BootLoader  on sde1


Unknown BootLoader  on sde2


Unknown BootLoader  on sde3


Unknown BootLoader  on sde4


Unknown BootLoader  on sdf1


Unknown BootLoader  on sdf2


Unknown BootLoader  on sdf3


Unknown BootLoader  on sdf4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sde1: No such file or directory
hexdump: /dev/sde1: No such file or directory
hexdump: /dev/sde2: No such file or directory
hexdump: /dev/sde2: No such file or directory
hexdump: /dev/sde3: No such file or directory
hexdump: /dev/sde3: No such file or directory
hexdump: /dev/sde4: No such file or directory
hexdump: /dev/sde4: No such file or directory
hexdump: /dev/sdf1: No such file or directory
hexdump: /dev/sdf1: No such file or directory
hexdump: /dev/sdf2: No such file or directory
hexdump: /dev/sdf2: No such file or directory
hexdump: /dev/sdf3: No such file or directory
hexdump: /dev/sdf3: No such file or directory
hexdump: /dev/sdf4: No such file or directory
hexdump: /dev/sdf4: No such file or directory
```

Your sdc, sdd & sde disks are jacked up and unmountable! What is on them?

But we can probably get your 9.10 Ubuntu working. You will need the 9.04 (not 9.10) Live CD because you still have Legacy GRUB 0.97. Boot the 9.04 Live CD. Choose "try Ubuntu without any changes", when the desktop loads open a terminal and do this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)"
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Reboot & go into BIOS. Set the sdb disk (34 GB) as first hard disk to boot in the hard disk boot order. Save changes to CMOS & continue booting into Ubuntu.

Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll down to this:

#```
## END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

And remove:

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

Click Save on top toolbar & close file. reboot .

---

### Post by a2z on 2010-01-19
> **presence1960 said:**
> Your sdc, sdd & sde disks are jacked up and unmountable! What is on them?

But we can probably get your 9.10 Ubuntu working. You will need the 9.04 (not 9.10) Live CD because you still have Legacy GRUB 0.97. Boot the 9.04 Live CD. Choose "try Ubuntu without any changes", when the desktop loads open a terminal and do this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)"
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Reboot & go into BIOS. Set the sdb disk (34 GB) as first hard disk to boot in the hard disk boot order. Save changes to CMOS & continue booting into Ubuntu.

Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll down to this:

#```
## END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

And remove:

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

Click Save on top toolbar & close file. reboot .

I have a few programs and some videos I been working on. 
I realize when my 34g drive starts to get full, I transfer them to the 500g.(sometimes not fast enough)
I think overloading this drive is what caused my problems to start the time before I tried karmic. Things deteriorated quickly from there.
I'll give this a try. Thanks for your help. If all else fails, I'm prepared to do a clean install. I think...:P

---

### Post by entelechi on 2010-01-19
After some more rebooting drama, here's mine. If it is the same as above, just say same. Otherwise, what do I do?

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf448f448

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,935,430,874 1,935,430,812  83 Linux
/dev/sda2       1,935,430,875 1,953,520,064    18,089,190   5 Extended
/dev/sda5       1,935,430,938 1,953,520,064    18,089,127  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="f331fd2b-7858-40df-9322-25342bcad207" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="03c59455-7a13-4c30-a0c6-2de2459e08c3" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
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
# kopt=root=UUID=f331fd2b-7858-40df-9322-25342bcad207 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f331fd2b-7858-40df-9322-25342bcad207

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
uuid		f331fd2b-7858-40df-9322-25342bcad207
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f331fd2b-7858-40df-9322-25342bcad207 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		f331fd2b-7858-40df-9322-25342bcad207
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f331fd2b-7858-40df-9322-25342bcad207 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		f331fd2b-7858-40df-9322-25342bcad207
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f331fd2b-7858-40df-9322-25342bcad207 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		f331fd2b-7858-40df-9322-25342bcad207
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f331fd2b-7858-40df-9322-25342bcad207 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, memtest86+
uuid		f331fd2b-7858-40df-9322-25342bcad207
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f331fd2b-7858-40df-9322-25342bcad207 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=03c59455-7a13-4c30-a0c6-2de2459e08c3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```

---

### Post by a2z on 2010-01-19
The command didn't turn up anything!
All it did was open a blank page.

```
gksu gedit /boot/grub/menu.lst
```

Any ideas?

---

### Post by entelechi on 2010-01-19
> **a2z said:**
> I have a few programs and some videos I been working on. 
I realize when my 34g drive starts to get full, I transfer them to the 500g.(sometimes not fast enough)
I think overloading this drive is what caused my problems to start the time before I tried karmic. Things deteriorated quickly from there.
I'll give this a try. Thanks for your help. If all else fails, I'm prepared to do a clean install. I think...:P

My drive is also almost full. Even when it was mostly empty, the same error occurred. From my vantage point, it was something in the 9.10 upgrade that caused the malfunction.

---

### Post by presence1960 on 2010-01-19
> **a2z said:**
> The command didn't turn up anything!
All it did was open a blank page.

```
gksu gedit /boot/grub/menu.lst
```

Any ideas?

You must have done something wrong for here is what should be in that file. This is from the output of your script:

=========================== sdb1/boot/grub/menu.lst: ===========================

```
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
# kopt=root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5ceb94e8-3325-4b30-ac59-814fb0f14cc3

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
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.28-17-generic
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=5ceb94e8-3325-4b30-ac59-814fb0f14cc3 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.10, memtest86+
uuid		5ceb94e8-3325-4b30-ac59-814fb0f14cc3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c0e49ee8-45a7-4a14-8178-84ce11930cf0 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

---

### Post by a2z on 2010-01-19
> **entelechi said:**
> My drive is also almost full. Even when it was mostly empty, the same error occurred. From my vantage point, it was something in the 9.10 upgrade that caused the malfunction.

I tend to agree. No worries though. Things get fixed fast around here :)

---

### Post by a2z on 2010-01-19
> **presence1960 said:**
> You must have done something wrong [/CODE]

I did it 3 or 4 times. Regular terminal, root terminal, copy and paste ect. I'll try again though incase I missed something

Thanks

---

### Post by presence1960 on 2010-01-19
> **a2z said:**
> I did it 3 or 4 times. Regular terminal, root terminal, copy and paste ect. I'll try again though incase I missed something

Thanks

you aren't running that from the Live Cd are you?

---

### Post by presence1960 on 2010-01-19
> **entelechi said:**
> After some more rebooting drama, here's mine. If it is the same as above, just say same. Otherwise, what do I do?

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf448f448

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,935,430,874 1,935,430,812  83 Linux
/dev/sda2       1,935,430,875 1,953,520,064    18,089,190   5 Extended
/dev/sda5       1,935,430,938 1,953,520,064    18,089,127  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="f331fd2b-7858-40df-9322-25342bcad207" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="03c59455-7a13-4c30-a0c6-2de2459e08c3" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
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
# kopt=root=UUID=f331fd2b-7858-40df-9322-25342bcad207 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f331fd2b-7858-40df-9322-25342bcad207

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
uuid		f331fd2b-7858-40df-9322-25342bcad207
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f331fd2b-7858-40df-9322-25342bcad207 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		f331fd2b-7858-40df-9322-25342bcad207
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f331fd2b-7858-40df-9322-25342bcad207 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		f331fd2b-7858-40df-9322-25342bcad207
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f331fd2b-7858-40df-9322-25342bcad207 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		f331fd2b-7858-40df-9322-25342bcad207
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f331fd2b-7858-40df-9322-25342bcad207 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, memtest86+
uuid		f331fd2b-7858-40df-9322-25342bcad207
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f331fd2b-7858-40df-9322-25342bcad207 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=03c59455-7a13-4c30-a0c6-2de2459e08c3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```

Your output from the script looks good to me. I really don't like the option where you have the choice of keeping legacy GRUB. In my opinion that is a mistake in most cases. Off the top of my head I can't remember the procedure to put GRUB2 in it's place. After my daughter is asleep I will look that up.

---

### Post by entelechi on 2010-01-19
I would really like to be able to read code language...

It is a gap in my knowledge that is really starting to bug me...

---

### Post by a2z on 2010-01-19
> **presence1960 said:**
> you aren't running that from the Live Cd are you?

yea, I recon I am. ubunty@ubuntu
I did however try to change where it would look by cd .. several times too.
Oh, maybe cd to the 40g drive
brb

---

### Post by entelechi on 2010-01-20
It booted up on the first time today but had no sound then it stalled again. I tried starting it in recovery mode but it yielded 

Bug: soft lockup - CPU#6 stuck for 61s! [modprobe:795]

Now I am trying to boot from the live CD and spit out some error about the audio. Now it won't boot from the live CD and I get the error message:

Bug: soft lockup - CPU#1 stuck for 61s! [modprobe:1572]

I built my own system and had manually ensable ALSA because I am using a Creative sound card. Could this be the cause of the error? I am at a loss here...

---

### Post by entelechi on 2010-01-20
> **presence1960 said:**
> Your output from the script looks good to me. I really don't like the option where you have the choice of keeping legacy GRUB. In my opinion that is a mistake in most cases. Off the top of my head I can't remember the procedure to put GRUB2 in it's place. After my daughter is asleep I will look that up.

Installing Grub2 solved it when I removed the sound card. After reinstalling the sound card, it stalls. There must be some interaction with the boot sequence and the sound card with ALSA enabled. Any ideas?

Or maybe my computer has been hacked by some unscrupulous peeping toms...

---

### Post by mitchauer on 2010-01-20
I can't even get 9.10 32 bit or 64 bit to install it hangs up just as described above. When I put a live disc in it gets almost to the desktop and stops. No trouble with 9.04.

---

### Post by brownld on 2010-01-22
I have just downloaded and installed ubuntu 9.10.  This is a fresh install.  In fact I started over at least once and went so far as to run fixmbr on the Windows harddisk (the primary IDE drive), so there is no question about grub versus grub2.  The Live CD boots just fine and the install works.  After the install the machine sits in bootloader for a full ten minutes (I used a stopwatch several times to be sure).  I repartition and format each partition during the install, so there is no good reason for there to be a file system problem.  The grub menu does show up (after 10 minutes) and it works.  So far in this thread the closest I come to an explanation might be the splash image, if there is one in the grub chain.  Otherwise, it is the same problem but no good explanation.  One other quirk in my system is the primary drive is IDE, but the drive I am installing Ubuntu on is a SATA hard drive on the second SATA chain, and the first SATA chain is occupied by a DVD burner.

I did, in an earlier life of this machine, have Debian installed.  Grub worked just fine in this configuration.

---

### Post by tachuela on 2010-01-22
[http://ubuntuforums.org/showthread.php?t=366838&highlight=Dualboot+hardrives](http://ubuntuforums.org/showthread.php?t=366838&highlight=Dualboot+hardrives)

---

### Post by presence1960 on 2010-01-22
> **brownld said:**
> I have just downloaded and installed ubuntu 9.10.  This is a fresh install.  In fact I started over at least once and went so far as to run fixmbr on the Windows harddisk (the primary IDE drive), so there is no question about grub versus grub2.  The Live CD boots just fine and the install works.  After the install the machine sits in bootloader for a full ten minutes (I used a stopwatch several times to be sure).  I repartition and format each partition during the install, so there is no good reason for there to be a file system problem.  The grub menu does show up (after 10 minutes) and it works.  So far in this thread the closest I come to an explanation might be the splash image, if there is one in the grub chain.  Otherwise, it is the same problem but no good explanation.  One other quirk in my system is the primary drive is IDE, but the drive I am installing Ubuntu on is a SATA hard drive on the second SATA chain, and the first SATA chain is occupied by a DVD burner.

I did, in an earlier life of this machine, have Debian installed.  Grub worked just fine in this configuration.
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by paulgir on 2010-01-22
Hi guys
I've just attempted to install 9.04 on a separate drive (sdb1) to XP.
Boot stops with an Error 17
I've attempted to fix  grub with Super Grub disk with no luck.

My boot info results:

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b159b15

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,846,935   570,307,499   406,460,565   7 HPFS/NTFS
/dev/sda3         570,307,500   976,768,064   406,460,565   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x988d3358

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    52,436,159    52,436,097  83 Linux
/dev/sdb2          52,436,160    94,381,874    41,945,715  83 Linux
/dev/sdb3          94,381,875   976,768,064   882,386,190   5 Extended
/dev/sdb5          94,381,938    98,574,839     4,192,902  82 Linux swap / Solaris
/dev/sdb6          98,574,903   517,999,859   419,424,957  83 Linux
/dev/sdb7         517,999,923   976,768,064   458,768,142  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01296a69

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sdc2         163,846,935   326,119,499   162,272,565   7 HPFS/NTFS
/dev/sdc3         326,119,500   488,392,064   162,272,565   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C8E4918CE4917CFE" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda2: UUID="9E78DC3F78DC17BB" LABEL="PAULS DATA 200GB" TYPE="ntfs" 
/dev/sda3: UUID="763C238B3C234609" LABEL="Ubuntu 200 GB" TYPE="ntfs" 
/dev/sdb1: UUID="ffb63e7e-d405-4fb0-a4a2-01cbca46c894" TYPE="ext4" 
/dev/sdb2: LABEL="Home" UUID="75c3e6d3-b8bd-49bf-b91b-316521c7e106" TYPE="ext4" 
/dev/sdb5: TYPE="swap" UUID="13290cb9-9e19-4753-890a-38be5eda33b4" 
/dev/sdb5: UUID="13290cb9-9e19-4753-890a-38be5eda33b4" TYPE="swap" 
/dev/sdb6: LABEL="Data 1" UUID="c39aab0e-2160-473c-a9ca-208685c56ca9" TYPE="ext4" 
/dev/sdb7: LABEL="Data 2" UUID="365832c8-5b12-4895-80fd-cf3228e5952b" TYPE="ext4" 
/dev/sdc1: UUID="F05CEC815CEC4446" LABEL="SYSTEM IMAGE 80Gb" TYPE="ntfs" 
/dev/sdc2: UUID="741470F41470BB26" LABEL="BACKUP 80GB" TYPE="ntfs" 
/dev/sdc3: UUID="D62898132897F0AB" LABEL="SYSTEM IMAGE 80GB" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb2 on /home type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/paul/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paul)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=paul)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=C:\wubildr.mbr

[operating systems]

C:\wubildr.mbr = "Ubuntu"

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
# kopt=root=UUID=ffb63e7e-d405-4fb0-a4a2-01cbca46c894 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ffb63e7e-d405-4fb0-a4a2-01cbca46c894

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
uuid		ffb63e7e-d405-4fb0-a4a2-01cbca46c894
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ffb63e7e-d405-4fb0-a4a2-01cbca46c894 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ffb63e7e-d405-4fb0-a4a2-01cbca46c894
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ffb63e7e-d405-4fb0-a4a2-01cbca46c894 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ffb63e7e-d405-4fb0-a4a2-01cbca46c894
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=ffb63e7e-d405-4fb0-a4a2-01cbca46c894 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=75c3e6d3-b8bd-49bf-b91b-316521c7e106 /home           ext4    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=13290cb9-9e19-4753-890a-38be5eda33b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   1.8GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
   1.7GB: boot/initrd.img-2.6.28-11-generic
   1.8GB: boot/vmlinuz-2.6.28-11-generic
   1.7GB: initrd.img
   1.8GB: vmlinuz
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
000001b0  00 00 00 00 00 00 00 00  69 6a 29 01 00 00 00 01  |........ij).....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 d8 1a c4 09 00 fe  |......?.........|
000001d0  ff ff 07 fe ff ff 17 1b  c4 09 35 15 ac 09 00 fe  |..........5.....|
000001e0  ff ff 07 fe ff ff 4c 30  70 13 35 15 ac 09 00 00  |......L0p.5.....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by paulgir on 2010-01-22
Since the previous post,I reinstalled 9.04 on sdb1, but this time I installed Grub on sdb instead of sda.
I now get the Grub boot menu with the correct options and can boot Ubuntu 9.04
If I select Windows XP I get "Error 13 invalid or unsupported format".

Any ideas how to fix this?

---

### Post by presence1960 on 2010-01-22
> **paulgir said:**
> Since the previous post,I reinstalled 9.04 on sdb1, but this time I installed Grub on sdb instead of sda.
I now get the Grub boot menu with the correct options and can boot Ubuntu 9.04
If I select Windows XP I get "Error 13 invalid or unsupported format".

Any ideas how to fix this?

Boot into Ubuntu. Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst 

When the file opens scroll down to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

```

Change it to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title         Windows NT/2000/XP
rootnoverify  (hd1,0)
map           (hd0) (hd1)
map           (hd1) (hd0)
chainloader   +1

```

You can edit the title line to reflect your version of windows ( title   Windows XP Professional, for example)

Click Save on top toolbar and close file. Reboot & try booting windows.

---

### Post by paulgir on 2010-01-22
Thanks for the reply,
I will keep it for future reference.

I managed to get XP up and running.
I reinstalled 9.04 for a 3rd time,this time installing the bootloader to sda1 (where I think XP is installed).
The first installation attempt had the default location for the bootloader as hd0.The second installation attempt I put the bootloader in sdb.
Then I selected sda as the 1st drive to boot after CDROM.

I also selected sdb as 2nd hd to boot,but I think this is irrelevant.

Now when I boot up I get the grub menu with:
Ubuntu
Ubuntu recovery
Memtest
Other OS:
XP

If I select Ubuntu it boots straight to 9.04
If I select XP I get another Grub menu wich is exactly the same as the WUBI install I thought I deleted,with 2 choices:
ubuntu 
XP

If I select XP windows boots successfully.
If I select Ubuntu the boot hangs.

I would like to remove the 2nd (non-functioning) Ubuntu option,any suggestions where I would find this?

Perhaps there is a residual grub from WUBI?
I deleted all the files on the partition WUBI was installed to (different partition to Windows) as I could not use the uninstaller for WUBI.It was not there for some reason.

Thanks for the help.
I will post an updated boot info results file.

---

### Post by presence1960 on 2010-01-22
You can get rid of the wubi entry in boot.ini.

Go Control Panel > System > Advanced > and one of those buttons there (I believe startup & recovery) will have an Edit button. If you click Edit it will open boot.ini in notepad. Remove the reference to wubi. Be careful to only remove wubi's reference. This will get rid of the ubuntu entry when choose windows from GRUB. When boot.ini takes over it will go straight to windows.

---

### Post by paulgir on 2010-01-22
Cool! That worked fine.
I don't get the 2nd OS options menu now.

I've attached the latest Boot Info output in case it has useful info for you.

---

### Post by presence1960 on 2010-01-23
> **paulgir said:**
> Cool! That worked fine.
I don't get the 2nd OS options menu now.

I've attached the latest Boot Info output in case it has useful info for you.

Glad you got it working! Enjoy Ubuntu.

The reason you got that ubuntu entry when you chose windows is you had a prior install of wubi. Wubi boots from the windows bootloader (in XP- boot.ini). So when you booted your machine windows bootloader took over giving you the two options. When you chose Ubuntu it passed off to GRUB and presented the GRUB menu. Now even though you removed wubi that entry in boot.ini remains until you edit it. Uninstalling wubi does not edit boot.ini.

You now have GRUB on MBR. When you choose windows from the GRUB menu it passes off to boot.ini. So whatever is in boot.ini will presented as a choice at that point.

---

### Post by paulgir on 2010-01-23
I had the WUBI install for over a year and a dual boot of 7.10 prior to that.
I could be considered a convert.:D

---

### Post by alta285 on 2010-01-23
I've been also having similar problems with Ubuntu 9.10 stalling on me. I am not sure if it's exactly the same problem as everyone else because it eventually boots after about 1 minute or so but it's just frustrating having to wait since that's never happened before. The stalling always happens right before the logon screen appears. 

I've also got Vista installed on the my HD on a different partition. 

I ran the script that you've mentioned and the results are below. 

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe27f7a5c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   623,648,532   623,646,485   7 HPFS/NTFS
/dev/sda2         623,659,365 1,953,520,064 1,329,860,700  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4A8CE8AD8CE8952B" TYPE="ntfs" 
/dev/sda2: UUID="7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/talam/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=talam)


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
# kopt=root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro

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

title        Ubuntu 9.10, kernel 2.6.31-17-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.27-14-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-14-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 9.10, kernel 2.6.24-19-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro quiet splash 
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b ro  single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7f5b1e01-8e8a-4c15-b10d-06f7b1a59c2b /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 319.3GB: boot/grub/menu.lst
 319.3GB: boot/grub/stage2
 319.3GB: boot/initrd.img-2.6.24-19-generic
 319.3GB: boot/initrd.img-2.6.27-14-generic
 319.3GB: boot/initrd.img-2.6.28-16-generic
 319.3GB: boot/initrd.img-2.6.31-14-generic
 319.3GB: boot/initrd.img-2.6.31-15-generic
 319.3GB: boot/initrd.img-2.6.31-16-generic
 319.3GB: boot/initrd.img-2.6.31-17-generic
 319.3GB: boot/vmlinuz-2.6.24-19-generic
 319.3GB: boot/vmlinuz-2.6.27-14-generic
 319.3GB: boot/vmlinuz-2.6.28-16-generic
 319.3GB: boot/vmlinuz-2.6.31-14-generic
 319.3GB: boot/vmlinuz-2.6.31-15-generic
 319.3GB: boot/vmlinuz-2.6.31-16-generic
 319.3GB: boot/vmlinuz-2.6.31-17-generic
 319.3GB: initrd.img
 319.3GB: initrd.img.old
 319.3GB: vmlinuz
 319.3GB: vmlinuz.old
```Any suggestions?

---

### Post by entelechi on 2010-01-31
My problem is still occurring after installing grub2. Ideas?

---

