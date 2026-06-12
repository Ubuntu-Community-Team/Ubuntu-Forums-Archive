---
title: "Cannot Restore GRUB"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by RikkiUW on 2009-12-24
Hey all,

On my laptop I had Ubuntu 9.10 and Windows Vista and GRUB worked fine. I decided to upgrade Vista to Windows 7, figuring I could use Super Grub Disk to restore the GRUB no problem, but now I cannot get it to work. Auto grub disk (on a USB stick) has a screen with something like "findf /boot/grub/stage1", and it just stays there. I left it for nearly an hour and it didn't say anything else. I tried different options on the regular disk with similar results. Eventually I came across a tutorial to restore it using a live CD, so I burned a 9.10 and booted from the disk and tried to run "sudo grub" but it says "grub: command not found". I've tried a few similar things with no success.

I'm tempted to do a complete reformat, but I'd really rather avoid it as I've finally got everything set up the way I want it...

Any suggestions?
Thanks,
--Rikki

---

### Post by Herman on 2009-12-24
The commands you're trying to use would have worked for GRUB Legacy, which is the 'old' GRUB, GRUB 0.97.
Ubuntu 9.10 'Karmic Koala' uses GRUB 1.97 as its default boot loader.
The files for GRUB and the commands you can use have changed quite a lot.

You should not need to reformat.
Try following the same advice I gave in the following thread:                          [Computer won't boot to 9.10; No Grub Menu]("http://ubuntuforums.org/showthread.php?t=1306900").

---

### Post by RikkiUW on 2010-01-20
> **Herman said:**
> The commands you're trying to use would have worked for GRUB Legacy, which is the 'old' GRUB, GRUB 0.97.
Ubuntu 9.10 'Karmic Koala' uses GRUB 1.97 as its default boot loader.
The files for GRUB and the commands you can use have changed quite a lot.

You should not need to reformat.
Try following the same advice I gave in the following thread:                          [Computer won't boot to 9.10; No Grub Menu]("http://ubuntuforums.org/showthread.php?t=1306900").

Hey, sorry it took my so long to reply. The commands in the other post didn't work. Even when I specified the path to the device.map file it says:

grub-setup: error: cannot stat /media/mountpoint/boot/grub/boot.img

Don't know if it means anything but the mountpoint didn't show up when I went into the folder, only when I used ls /media. Do you know what could be wrong?

---

### Post by Leppie on 2010-01-20
depending a bit on your system, you should only need the following:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```
if you do not have ubuntu installed into partition sda5, amend the mount command accordingly.
alternatively, [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt

---

### Post by darkod on 2010-01-20
> **Leppie said:**
> depending a bit on your system, you should only need the following:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```if you do not have ubuntu installed into partition sda5, amend the mount command accordingly.
alternatively, [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt

+1

And in future I would try to avoid Super Grub. With ubuntu it also matters if you are using 9.04 or earlier with grub1, or 9.10 with grub2. And you can always reinstall the corresponding grub version with the correct cd version.

No need for Super Grub which can potentially mess things up even though some people advocate it.

---

### Post by RikkiUW on 2010-01-20
> **Leppie said:**
> depending a bit on your system, you should only need the following:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```
if you do not have ubuntu installed into partition sda5, amend the mount command accordingly.
alternatively, [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt

I ran the commands as you typed them (I ran fdisk, sda5 is correct), and restarted and now have an sh:grub> prompt, instead of a list of OSes. How can I restore the list of OSes and update it to remove the old Vista entry and add a new Windows 7 one?

Thanks,
--Rikki

---

### Post by darkod on 2010-01-20
> **RikkiUW said:**
> I ran the commands as you typed them (I ran fdisk, sda5 is correct), and restarted and now have an sh:grub> prompt, instead of a list of OSes. How can I restore the list of OSes and update it to remove the old Vista entry and add a new Windows 7 one?

Thanks,
--Rikki

I don't want to jump to conclusions, but if you tried installing super grub too, it might have already created some mess.
It's time to run the script as suggested, you can also find it in my signature. Run it and copy the content of the generated results.txt file here. It will show your boot files and will help figure out what happened and what to do.

---

### Post by presence1960 on 2010-01-20
Don't get worried. When faced with boot problems I recommend running the boot info script darko said to run. The script will reveal quite a lot about your setup & boot process. Running commands or trying things without knowing the exact nature of a problem often makes the problem worse.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by RikkiUW on 2010-01-20
Thanks guys. Here it is:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a2945ba

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920       286,719       204,800   7 HPFS/NTFS
/dev/sda3             286,720   209,797,119   209,510,400   7 HPFS/NTFS
/dev/sda4         446,382,090   488,392,064    42,009,975   5 Extended
/dev/sda5         446,382,153   486,544,589    40,162,437  83 Linux
/dev/sda6         486,544,653   488,392,064     1,847,412  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: UUID="78D2A44CD2A41084" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda3: UUID="943CBD893CBD6740" TYPE="ntfs" 
/dev/sda5: UUID="9105da31-ca66-4c0b-8486-022dbcdc5c84" TYPE="ext3" 
/dev/sda6: UUID="e9801b84-baa1-4ab7-b189-fc4c83bc6872" TYPE="swap" 

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
/dev/sda5 on /media/9105da31-ca66-4c0b-8486-022dbcdc5c84 type ext3 (rw,nosuid,nodev,uhelper=devkit)


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
# kopt=root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9105da31-ca66-4c0b-8486-022dbcdc5c84

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

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.27-7-generic
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.10, memtest86+
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e9801b84-baa1-4ab7-b189-fc4c83bc6872 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 228.5GB: boot/grub/core.img
 228.5GB: boot/grub/menu.lst
 228.5GB: boot/grub/stage2
 228.5GB: boot/initrd.img-2.6.27-7-generic
 228.5GB: boot/initrd.img-2.6.28-16-generic
 228.5GB: boot/initrd.img-2.6.31-15-generic
 228.5GB: boot/initrd.img-2.6.31-16-generic
 228.5GB: boot/vmlinuz-2.6.27-7-generic
 228.5GB: boot/vmlinuz-2.6.28-16-generic
 228.5GB: boot/vmlinuz-2.6.31-15-generic
 228.5GB: boot/vmlinuz-2.6.31-16-generic
 228.5GB: initrd.img
 228.5GB: initrd.img.old
 228.5GB: vmlinuz
 228.5GB: vmlinuz.old
```

---

### Post by Leppie on 2010-01-20
you are missing the configuration file for the grub menu.

reboot, let the system get to the grub prompt.
issue the following commands to boot into your ubuntu install:
```
set root=(hd0,5)
insmod ext2
insmod linux
linux /vmlinuz root=/dev/sda5 ro        
initrd /initrd.img        
boot
```once in the system, you need to generate the grub.cfg file:
```
sudo update-grub
```check that at least 1 ubuntu entry is being generated, your windows should be detected automagically as well ;)

---

### Post by presence1960 on 2010-01-20
> **RikkiUW said:**
> Thanks guys. Here it is:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a2945ba

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920       286,719       204,800   7 HPFS/NTFS
/dev/sda3             286,720   209,797,119   209,510,400   7 HPFS/NTFS
/dev/sda4         446,382,090   488,392,064    42,009,975   5 Extended
/dev/sda5         446,382,153   486,544,589    40,162,437  83 Linux
/dev/sda6         486,544,653   488,392,064     1,847,412  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: UUID="78D2A44CD2A41084" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda3: UUID="943CBD893CBD6740" TYPE="ntfs" 
/dev/sda5: UUID="9105da31-ca66-4c0b-8486-022dbcdc5c84" TYPE="ext3" 
/dev/sda6: UUID="e9801b84-baa1-4ab7-b189-fc4c83bc6872" TYPE="swap" 

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
/dev/sda5 on /media/9105da31-ca66-4c0b-8486-022dbcdc5c84 type ext3 (rw,nosuid,nodev,uhelper=devkit)


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
# kopt=root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9105da31-ca66-4c0b-8486-022dbcdc5c84

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

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.27-7-generic
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.10, memtest86+
uuid		9105da31-ca66-4c0b-8486-022dbcdc5c84
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9105da31-ca66-4c0b-8486-022dbcdc5c84 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e9801b84-baa1-4ab7-b189-fc4c83bc6872 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 228.5GB: boot/grub/core.img
 228.5GB: boot/grub/menu.lst
 228.5GB: boot/grub/stage2
 228.5GB: boot/initrd.img-2.6.27-7-generic
 228.5GB: boot/initrd.img-2.6.28-16-generic
 228.5GB: boot/initrd.img-2.6.31-15-generic
 228.5GB: boot/initrd.img-2.6.31-16-generic
 228.5GB: boot/vmlinuz-2.6.27-7-generic
 228.5GB: boot/vmlinuz-2.6.28-16-generic
 228.5GB: boot/vmlinuz-2.6.31-15-generic
 228.5GB: boot/vmlinuz-2.6.31-16-generic
 228.5GB: initrd.img
 228.5GB: initrd.img.old
 228.5GB: vmlinuz
 228.5GB: vmlinuz.old
```

Well your problem seems to be you have Legacy GRUB 0.97 but put GRUB2 (v. 1.97) on your MBR. This is why I always insist on the boot info script being run prior to trying to fix a problem, if we had done that from jumpstreet then you wouldn't have been given instructions to restore GRUB2 because we would have seen you had GRUB 0.97

You will need a 9.04 Live CD as the 9.10 Live CD does not support GRUB 0.97. Boot the 9.04 Live CD and choose "try ubuntu without any changes", when the desktop loads open a terminal and do this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
5. Type "root (hd0,4)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by Leppie on 2010-01-20
> **presence1960 said:**
> Well your problem seems to be you have Legacy GRUB 0.97 but put GRUB2 (v. 1.97) on your MBR. This is why I always insist on the boot info script being run prior to trying to fix a problem, if we had done that from jumpstreet then you wouldn't have been given instructions to restore GRUB2 because we would have seen you had GRUB 0.97
as he installed karmic, i think he should have grub2 (as the mbr indicates). i think the menu.lst was generated by playing around with the supergrub disk.

---

### Post by presence1960 on 2010-01-20
> **Leppie said:**
> as he installed karmic, i think he should have grub2 (as the mbr indicates). i think the menu.lst was generated by playing around with the supergrub disk.

```
=================== sda5: Location of files loaded by Grub: ===================


 228.5GB: boot/grub/core.img
 228.5GB: boot/grub/menu.lst
 228.5GB: boot/grub/stage2
 [COLOR="Red"]228.5GB: boot/initrd.img-2.6.27-7-generic
 228.5GB: boot/initrd.img-2.6.28-16-generic[/COLOR]
 228.5GB: boot/initrd.img-2.6.31-15-generic
 228.5GB: boot/initrd.img-2.6.31-16-generic
 [COLOR="Red"]228.5GB: boot/vmlinuz-2.6.27-7-generic
 228.5GB: boot/vmlinuz-2.6.28-16-generic[/COLOR]
 228.5GB: boot/vmlinuz-2.6.31-15-generic
 228.5GB: boot/vmlinuz-2.6.31-16-generic
 228.5GB: initrd.img
 228.5GB: initrd.img.old
 228.5GB: vmlinuz
 228.5GB: vmlinuz.old
```

I seriously doubt that- look in red above at the kernels on his machine. They are not karmic kernels. he probably got to karmic via a dist-upgrade and kept Legacy GRUB as is usually the case with dist-upgrades. Plus he has a GRUB stage 2 file which is Legacy GRUB.

---

### Post by Leppie on 2010-01-20
> **presence1960 said:**
> I seriously doubt that- look in red above at the kernels on his machine. They are not karmic kernels. he probably got to karmic via a dist-upgrade and kept Legacy GRUB as is usually the case with dist-upgrades. Plus he has a GRUB stage 2 file which is Legacy GRUB.
haha, you may very well be right. didn't check the installed kernels... #-o
anyway, my guess is then he has both installed (grub2 didn't install into the mbr on it's own ;))

---

### Post by presence1960 on 2010-01-20
> **Leppie said:**
> haha, you may very well be right. didn't check the installed kernels... #-o
anyway, my guess is then he has both installed (grub2 didn't install into the mbr on it's own ;))

He followed the advice in post # 2 and restored GRUB 2 but since his ubuntu was set up for Legacy GRUB booting resulted in a grub> sh prompt

He can keep Legacy GRUB and fix it the way I proposed or upgrade to GRUB2 by following the how-to here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by RikkiUW on 2010-01-20
Yeah I originally had 8.10 then upgraded to 9.04 and then to 9.10, without reformatting. What you're saying makes sense presence1960, I'll give it a try tomorow and get back to you.

Thanks,
--Rikki

---

### Post by Leppie on 2010-01-20
> **presence1960 said:**
> He followed the advice in post # 2 and restored GRUB 2 but since his ubuntu was set up for Legacy GRUB booting resulted in a grub> sh prompt

He can keep Legacy GRUB and fix it the way I proposed or upgrade to GRUB2 by following the how-to here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
you're right there :)
i would go with grub2, powerful stuff ;)

---

### Post by presence1960 on 2010-01-20
> **Leppie said:**
> you're right there :)
i would go with grub2, powerful stuff ;)

That's why I believe two sets of eyes are better than one set! As long as the OP gets his rig running I am happy regardless of whose advice solves the problem. Usually in Linux there is more than one method to accomplish the same task. On a few occasions I missed the obvious and thank the heavens meierfra was there to see what I did not! I would really feel bad if I made someone's problems worse.

---

### Post by Leppie on 2010-01-20
> **presence1960 said:**
> That's why I believe two sets of eyes are better than one set! As long as the OP gets his rig running I am happy regardless of whose advice solves the problem. Usually in Linux there is more than one method to accomplish the same task. On a few occasions I missed the obvious and thank the heavens meierfra was there to see what I did not! I would really feel bad if I made someone's problems worse.

i totally agree on this with you :guitar:
it wouldn't be very cool believing to help sby while you're actually messing things up..

---

### Post by RikkiUW on 2010-01-21
Okay, GRUB is restored, but how do I change the Vista entry to a Windows 7 entry? Also, There are so many different options I want to remove the older ones, and I thought I could by deleting thier entries in menu.lst but it's locked, apparently I don't have permission. Is there another way I'm supposed to do it? If not, how do I give myself permission to edit it?

Thanks for all the help so far,
--Rikki

---

### Post by presence1960 on 2010-01-21
> **RikkiUW said:**
> Okay, GRUB is restored, but how do I change the Vista entry to a Windows 7 entry? Also, There are so many different options I want to remove the older ones, and I thought I could by deleting thier entries in menu.lst but it's locked, apparently I don't have permission. Is there another way I'm supposed to do it? If not, how do I give myself permission to edit it?

Thanks for all the help so far,
--Rikki

From ubuntu open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst
That will give you root priviledge running gedit to edit menu.lst

I would leave 2.6.31-16 and 2.6.31-15- they are karmic kernels. it is suggested to leave two kernels in case one borks then you can use the other to boot Ubuntu.

You remove the others from the file. This will not actually uninstall them but remove them from the GRUB menu. 

Next scroll down to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```
 and change it to:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows 7
rootnoverify	(hd0,2)
chainloader	+1

```
 Click save on top toolbar & close file. This will edit your GRUB menu at boot.

If you want to actually uninstall those kernels not needed from the older versions go to Synaptic Package manager @ System > Administration > Synaptic Package manager amd mark for Complete Removal the following:

linux-image-2.6.28-16
linux-image-2.6.27-7
linux-headers-2.6.28-16
linux-headers-2.6.27-7
If the above also has a trailing -generic remove those also.
Click Apply and they will be uninstalled and the packages removed from cache.

---

### Post by RikkiUW on 2010-01-21
Okay, made changes, but when I try to boot into windows 7 it says:

Starting up...
BOOTMGR is missing
Press Ctrl+Alt+Del to restart

How do I fix this? Also, could/should I remove the entry for Grub 2 chainloader? it doesn't work, I'm guessing it's a leftover from trying to restore Grub2.

Someone recommended switching to Grub2. What are the differences? Given that I'm not exactly an advanced user would I see any advantages?

Thanks,
--Rikki

---

### Post by darkod on 2010-01-21
> **RikkiUW said:**
> Okay, made changes, but when I try to boot into windows 7 it says:

Starting up...
BOOTMGR is missing
Press Ctrl+Alt+Del to restart

How do I fix this?

Thanks,
--Rikki

Presence, if the OP is using grub1, shouldn't the line read:

rootnoverify (hd0,1)

Because it's actually /dev/sda2 that is the win7 boot partition with the boot files.

---

### Post by RikkiUW on 2010-01-21
Yeah, that works, thanks. Also, could/should I remove the entry for Grub 2 chainloader? it doesn't work, I'm guessing it's a leftover from trying to restore Grub2.

Someone recommended switching to Grub2. What are the differences? Given that I'm not exactly an advanced user would I see any advantages?

---

### Post by darkod on 2010-01-21
> **RikkiUW said:**
> Yeah, that works, thanks. Also, could/should I remove the entry for Grub 2 chainloader? it doesn't work, I'm guessing it's a leftover from trying to restore Grub2.

Someone recommended switching to Grub2. What are the differences? Given that I'm not exactly an advanced user would I see any advantages?

In your results file in post #9 I can't see anything about chainloading to grub2. You don't seem to have any chainloading (except to win7 bootloader) and that's the way to do it anyway. Jumping from grub to grub makes little sense and only in special situations.

Since you sorted out the issue you might as well keep grub1. And maybe with the newly released 10.04 LTS in April if you plan to do clean install (recommended over distro upgrade), it will come with grub2 anyway.

---

### Post by RikkiUW on 2010-01-21
> **darkod said:**
> In your results file in post #9 I can't see anything about chainloading to grub2. You don't seem to have any chainloading (except to win7 bootloader) and that's the way to do it anyway. Jumping from grub to grub makes little sense and only in special situations.

I know it doesn't make sense, but I see an option in the GRUB saying "chainload into GRUB 2, but it doesn't work when I try it because GRUB 2 isn't installed. This is what that part of menu.lst looks like:

```
title        Chainload into GRUB 2
root         9105da31-ca66....
kernel       /boot/grub/core.img
```

> **darkod said:**
> Since you sorted out the issue you might as well keep grub1. And maybe with the newly released 10.04 LTS in April if you plan to do clean install (recommended over distro upgrade), it will come with grub2 anyway.

Fair enough, I'll do that.

---

### Post by darkod on 2010-01-21
> **RikkiUW said:**
> I know it doesn't make sense, but I see an option in the GRUB saying "chainload into GRUB 2, but it doesn't work when I try it because GRUB 2 isn't installed. This is what that part of menu.lst looks like:

```
title        Chainload into GRUB 2
root         9105da31-ca66....
kernel       /boot/grub/core.img
```

Fair enough, I'll do that.

I missed that in the results (or it isn't shown from what ever reason). Yes, it should be safe to delete that group of lines starting with 'title' from menu.lst.

---

### Post by RikkiUW on 2010-01-21
Brilliant! Looks like all of my Grub problems are fixed. Thanks a lot to all who helped!

--Rikki

---

### Post by presence1960 on 2010-01-21
Thanks for helping out Darko while I was away. sda2 is the System Reserved boot partition for windows 7 and that is where GRUB should point to boot 7. Good catch.

---

