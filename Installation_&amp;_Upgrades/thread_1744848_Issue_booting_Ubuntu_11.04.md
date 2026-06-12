---
title: "Issue booting Ubuntu 11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Straemer on 2011-04-30
So I have recently upgraded from 10.10 to 11.04 (32-bit), and have not been able to boot Ubuntu since. I believe this may be a kernel issue, as when I first upgraded from 10.04 to 10.10, I was not able to use the 2.6.38 linux kernel (It would hang when booting when it said "Starting up..."). I just used the 2.6.32 kernel instead, and everything worked fine. Now that I have upgraded to 11.04, neither of these kernel versions work. 2.6.38 hangs at the same spot as it did when trying to use it in 10.10, and 2.6.32 freezes up at the Ubuntu loading screen. I have tried burning a CD to reinstall (11.04), however, this seems to not want to load either. (It freezes with a black screen and blinking cursor after quickly displaying ISO LINUX or something along those lines)

I'm on an ASUS F50 with an Intel Core 2 Duo processor, and am Dual-Booting with Windows 7 (Windows will still boot properly). Has anyone experienced similar issues to this?

---

### Post by Rubi1200 on 2011-04-30
Hi and welcome to the forums :-)

Have you tried booting using Recovery Mode?

If you can somehow get the computer booted with a LiveCD (doesn't have to be an Ubuntu CD), do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

NOTE: depending on which distro you use to boot the computer, you may not need to preface that command with sudo. Try with either su or nothing in front of the command.

---

### Post by Straemer on 2011-04-30
I was able to startup in recovery mode (only on the kernel), I tried some fixes posted on the forums (mostly just reinstalling graphics drivers), but these seemed to be unsuccessful. The results of the script are:

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    24,579,449    24,579,387  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     24,580,096   337,149,951   312,569,856   7 HPFS/NTFS
/dev/sda3         337,156,155   625,137,344   287,981,190   5 Extended
/dev/sda5         429,819,138   433,819,259     4,000,122  82 Linux swap / Solaris
/dev/sda6         433,819,323   625,137,344   191,318,022   7 HPFS/NTFS
/dev/sda7         337,156,281   425,931,344    88,775,064  83 Linux
/dev/sda8         425,931,408   429,819,074     3,887,667  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8eb771e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        BC7E9AB97E9A6C40                       ntfs       Why should I name my hard drive?
/dev/sda5        1cc44ccc-1641-4a6a-81ea-08214793152c   swap                                     
/dev/sda6        90948E31948E1A3C                       ntfs       Data                          
/dev/sda7        b70d5bfe-bfa8-4464-9b70-bf69e8ba3690   ext3                                     
/dev/sda8        6f024d41-8c91-431b-ad37-c4e2e7081302   swap                                     
/dev/sdb1        AE3E2CD03E2C937F                       ntfs       THE SPOOL                     
/dev/sdc         F05B-414E                              vfat       THE FLASK                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/THE SPOOL         fuseblk    (rw,nosuid,nodev,allow_other,blksize=512)
/dev/sdc         /media/THE FLASK         vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


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
# kopt=root=UUID=b70d5bfe-bfa8-4464-9b70-bf69e8ba3690 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b70d5bfe-bfa8-4464-9b70-bf69e8ba3690

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

title        Ubuntu 11.04, kernel 2.6.38-8-generic-pae
uuid        b70d5bfe-bfa8-4464-9b70-bf69e8ba3690
kernel        /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=b70d5bfe-bfa8-4464-9b70-bf69e8ba3690 ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic-pae
quiet

title        Ubuntu 11.04, kernel 2.6.38-8-generic-pae (recovery mode)
uuid        b70d5bfe-bfa8-4464-9b70-bf69e8ba3690
kernel        /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=b70d5bfe-bfa8-4464-9b70-bf69e8ba3690 ro  single
initrd        /boot/initrd.img-2.6.38-8-generic-pae

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        b70d5bfe-bfa8-4464-9b70-bf69e8ba3690
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=b70d5bfe-bfa8-4464-9b70-bf69e8ba3690 ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        b70d5bfe-bfa8-4464-9b70-bf69e8ba3690
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=b70d5bfe-bfa8-4464-9b70-bf69e8ba3690 ro  single
initrd        /boot/initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, kernel 2.6.32-30-generic
uuid        b70d5bfe-bfa8-4464-9b70-bf69e8ba3690
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=b70d5bfe-bfa8-4464-9b70-bf69e8ba3690 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-30-generic
quiet

title        Ubuntu 11.04, kernel 2.6.32-30-generic (recovery mode)
uuid        b70d5bfe-bfa8-4464-9b70-bf69e8ba3690
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=b70d5bfe-bfa8-4464-9b70-bf69e8ba3690 ro  single
initrd        /boot/initrd.img-2.6.32-30-generic

title        Ubuntu 11.04, memtest86+
uuid        b70d5bfe-bfa8-4464-9b70-bf69e8ba3690
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=b70d5bfe-bfa8-4464-9b70-bf69e8ba3690 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=6f024d41-8c91-431b-ad37-c4e2e7081302 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 208.8GB: boot/grub/menu.lst
 208.9GB: boot/grub/stage2
 208.6GB: boot/initrd.img-2.6.32-30-generic
 208.5GB: boot/initrd.img-2.6.38-8-generic
 208.5GB: boot/initrd.img-2.6.38-8-generic-pae
 208.4GB: boot/vmlinuz-2.6.32-30-generic
 208.5GB: boot/vmlinuz-2.6.38-8-generic
 208.5GB: boot/vmlinuz-2.6.38-8-generic-pae
 208.5GB: initrd.img
 208.5GB: initrd.img.old
 208.5GB: vmlinuz
 208.5GB: vmlinuz.old
```

---

### Post by Straemer on 2011-05-02
Anyone have anything on this? Or is there another thread that might be helpful?

---

### Post by Straemer on 2011-05-10
I still have not resolved this issue. Can anyone help? I'm tired of having to use windows :(

---

### Post by Straemer on 2011-05-14
Anyone? Please?

---

### Post by Rubi1200 on 2011-05-14
You appear to have vestiges of a Wubi install as well as a mix of legacy-GRUB and GRUB2. Ubuntu versions from 9.10 onwards use GRUB2. You also have 2 swap partitions? Is there a reason for that?

The best advice I can give right now is to purge and reinstall GRUB from the LiveCD using the chroot method described in this fantastic thread by drs305:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Dutch70 on 2011-05-14
Edit: Well crap, that's twice today Rubi :)

The only thing I can tell you is that you've got grub legacy installed and 11.04 uses Grub2, but so does 10.10. 

Also, if you look at sda7 in your boot script, it says...
[COLOR="RoyalBlue"]Boot files/dirs:   /boot/grub/[COLOR="Red"]menu.lst[/COLOR] /etc/fstab[/COLOR]
I'm not sure why it's saying that.

menu.lst is also a part of grub legacy, I don't think its been used since Ubuntu 9.10. 
You may want to try reinstalling grub2.
[[COLOR="Red"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Good luck! I've never been able to upgrade successfully. Although some people say they've never had a problem. 

PS. If all else fails, you may want to try renewing your installation. I've never tried it before so I don't know how well it works, but I'll give you this video.
[[COLOR="Red"]http://www.youtube.com/watch?v=QGnsYuWS0xY[/COLOR]]("http://www.youtube.com/watch?v=QGnsYuWS0xY")

---

### Post by Straemer on 2011-05-14
Thanks for the quick response.

I was able to boot off a livecd and install GRUB2, however Ubuntu 11.04 still won't load. I get stuck at a blank purple screen when loading it from GRUB2. I originally installed Ubuntu from either 9.04 or 9.10, and have just upgraded through the update manager. I would probably be able to revert to 10.04 (that's the livecd I booted off of) however the 11.04 livecd doesn't seem to boot properly either.

---

### Post by Rubi1200 on 2011-05-15
Did you use the full chroot method I linked to? 

A simple reinstall of GRUB will likely not work in your situation.

If needs be, post the results of the boot script again so we can see what, if anything, has changed.

Thanks.

---

### Post by BlowyJellyFish on 2012-04-07
Well, this is an old thread, but I may have found a solution that will work.  I also have an ASUS F50SV, and I just recently upgraded from 10.04 to 12.04.  I ran into the same problem.  After some research, none of which was really helpful, I started playing with BIOS settings.  I found that if I go to Security -> I/O Interface Security Settings and set the New Card Interface to Locked (disabling it), the system boots normally.  I presume that this is the PC card slot, but I am not certain.

I do not use that card slot, so I am not missing anything, but if anyone knows how to fix the problem, the help would be appreciated.

Hope this helps!

---

