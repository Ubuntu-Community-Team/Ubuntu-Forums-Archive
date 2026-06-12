---
title: "Dual Booting Ubuntu 9.10 and Win7"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by Darwin555 on 2010-04-18
Hi,

I've done a good bit of ferreting around in older thread but I can't find any answers to my problem.

Until very recently I was running Ubuntu 9.10 (Karmic Koala) installed on a 20 GB hard disk and Windows XP (SP3) installed on RAID 1 array of 2 x 250 GB disks, very happily along side each other and using GRUB as the bootloader installed on the smaller 20 GB drive.

I have decided to upgrade to Windows 7, and was struggling with the installation failing with the seemingly quite common "Setup was unable to create a new system partition or locate and existing partition" error. Google seaching suggested unplugging my Ubuntu drive and then installing Win 7. This worked fine with the Ubuntu drive unplugged, however with the 20 GB plugged back in I can boot to GRUB, but it still has XP in the menu, and no option for Win 7.

I think I could get around the issue by re-installing Ubuntu, which would place GRUB on the MBR which is now on the 250 GB RAID 1 array, but I would rather have the system as it was before with GRUB and Ubuntu on the 20 GB drive.

I know I need to edit GRUB to remove the XP entry from the menu, but I have no idea how I would get Win 7 into GRUB, and what to do about the MBR which Win 7 put onto the RAID 1 array.

Cheers,

Darwin.

---

### Post by oldfred on 2010-04-18
Welcome to the forums.

I do not use raid but have seen others where it has caused issues. Have you tried the sudo update-grub to see if it finds it. Often the desktop version is not as raid aware as the server install.

If windows is in the MBR you should be able to boot to it.

If the update does not find it post this info:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by Darwin555 on 2010-04-18
Hi,

Thanks for the reply.

After posting I had already tried the sudo update-grub, and that has removed the redundant XP entries from GRUB however it didn't pick up the win 7.

I think the problem is that in BIOS my small Ubuntu drive is the primary drive, so bios looks to the MBR there and finds GRUB, (which I want), but unplugging that allowed win 7 to set the raid as system to drop it's own boot loader in, and then plugging the Ubuntu drive back in it overrides anything on the raid because it (Ubuntu drive) is primary in bios. I suspect (though I have yet to try it, will have a go in a mo), that switching primary drives around in bios would change which system boots.

Boot Info Script does show win 7 as available on 2 drives, which I know is the mirrored version across the array. I'm not too bothered about making the windows drives accessible in Ubuntu, as any work I want to share between the 2 OS's I usually dump on my NAS. I just need to have the option to boot into either system from GRUB.

Thanks,

Darwin.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb8caaef9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   488,278,015   488,071,168   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb8caaef9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   488,278,015   488,071,168   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdffedffe

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    37,383,254    37,383,192  83 Linux
/dev/sdc2          37,383,255    39,102,209     1,718,955   5 Extended
/dev/sdc5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x454c790c

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        66D23B69D23B3C9D                       ntfs       System Reserved               
/dev/sda2        0EC44AF2C44ADB99                       ntfs                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        66D23B69D23B3C9D                       ntfs       System Reserved               
/dev/sdb2        0EC44AF2C44ADB99                       ntfs                                     
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc1        b0b86b7f-8fe4-421b-ba87-12b68794158f   ext3                                     
/dev/sdc5        c89b7c64-93a0-46ed-9578-fd1494806a5d   swap                                     
/dev/sdd1        8EB4F9ADB4F99843                       ntfs       LaCie                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sr1         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=luke)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1        /media/LaCie             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b0b86b7f-8fe4-421b-ba87-12b68794158f

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        b0b86b7f-8fe4-421b-ba87-12b68794158f
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        b0b86b7f-8fe4-421b-ba87-12b68794158f
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        b0b86b7f-8fe4-421b-ba87-12b68794158f
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        b0b86b7f-8fe4-421b-ba87-12b68794158f
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        b0b86b7f-8fe4-421b-ba87-12b68794158f
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        b0b86b7f-8fe4-421b-ba87-12b68794158f
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic
uuid        b0b86b7f-8fe4-421b-ba87-12b68794158f
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
uuid        b0b86b7f-8fe4-421b-ba87-12b68794158f
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, kernel 2.6.27-7-generic
uuid        b0b86b7f-8fe4-421b-ba87-12b68794158f
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-7-generic (recovery mode)
uuid        b0b86b7f-8fe4-421b-ba87-12b68794158f
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.10, memtest86+
uuid        b0b86b7f-8fe4-421b-ba87-12b68794158f
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=b0b86b7f-8fe4-421b-ba87-12b68794158f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=c89b7c64-93a0-46ed-9578-fd1494806a5d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Mount our network drive
//STORAGE.home/public /media/NAS smbfs guest,nounix 0 0

=================== sdc1: Location of files loaded by Grub: ===================


  10.1GB: boot/grub/menu.lst
  10.1GB: boot/grub/stage2
  10.1GB: boot/initrd.img-2.6.27-7-generic
  10.1GB: boot/initrd.img-2.6.28-17-generic
  10.1GB: boot/initrd.img-2.6.31-17-generic
  10.1GB: boot/initrd.img-2.6.31-19-generic
  10.1GB: boot/initrd.img-2.6.31-20-generic
  10.1GB: boot/vmlinuz-2.6.27-7-generic
  10.0GB: boot/vmlinuz-2.6.28-17-generic
  10.1GB: boot/vmlinuz-2.6.31-17-generic
  10.1GB: boot/vmlinuz-2.6.31-19-generic
  10.1GB: boot/vmlinuz-2.6.31-20-generic
  10.1GB: initrd.img
  10.1GB: initrd.img.old
  10.1GB: vmlinuz
  10.1GB: vmlinuz.old
```

---

### Post by oldfred on 2010-04-18
You still have grub legacy (0.97) and it was not as good at finding other systems but it did add two entries for your windows, neither looks correct but the second is close. But your Ubuntu is really the third drive so instead of 1 change to 2. rootnoverify seems to work better than root. sda1 has the boot (active flag) so makeactive should not be required.

Change your second entry to this and see it it boots, if so then delete the first entry:
title        Microsoft Windows XP Professional
[COLOR=Red]rootnoverify [/COLOR]       (hd[COLOR=Red]2[/COLOR],0)
savedefault
map        (hd0) (hd[COLOR=Red]2[/COLOR])
map        (hd[COLOR=Red]2[/COLOR]) (hd0)
chainloader    +1

I am sure the map should be hd2 but I do not remember if the root is before or 
after the map.
It may be still (hd0,0)??

---

### Post by Darwin555 on 2010-04-18
Hi,

An update on this.

I restarted my system after doing sudo update-grub, and despite the result of that shown below suggesting that XP was no longer in the menu, it was still there on restart, so I tried selecting it expecting to get an error telling me that there was no such os, and instead it boots straight into Win 7. So it seems that all I have to do now is edit the entries in menu.lst to show windows xp as windows 7.

```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.28-17-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```


I will let you know if this works.

Cheers,

Darwin.

---

### Post by oldfred on 2010-04-18
Old grub was not good about finding the difference between versions of windows. You may be booting from sdb but with raid does it matter?

---

### Post by Darwin555 on 2010-04-18
when booting to win I always had to use the second entry which I always assumed was something to do with grub and the raid, so instinctively that was the one I chose with my last restart.

Do you think it is worth me making the edits you have suggested or would it just be simpler to edit the name of the entry as I now know it boots into win 7. Also would it be worth updating grub to a newer version or could that cause more problems?

will update the thread as solved if editing menu.lst sorts out the wrong named os.

---

### Post by oldfred on 2010-04-18
If it is working I would not  make the changes, you can change the description. Just change the description as that is just for the menu so you know what you are booting and not used any other way.

---

### Post by Darwin555 on 2010-04-19
Updating menu.lst and then editing the erroneously named windows entries from XP to win 7 has done exactly what I needed it to do.

Thanks for the help.

Darwin.

---

