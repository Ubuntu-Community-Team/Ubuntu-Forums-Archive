---
title: "Upgrade from Hardy to Lucid (Dual Boot) - no menu option"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Tetterley on 2010-10-10
Today I upgraded from Hardy Heron 8.4 to Lucid Lynx 10.4 using an option from the desktop.  

Each time I was asked if I wanted to keep the existing locally amended file, I replied "Keep".  I did this because I had trouble getting HH to recognise my touchpad when it was first installed (on laptop - will supply details if later becomes relevant) and I fixed this by altering some stuff so I didn't want to lose what I'd already changed.

One of the things that I didn't change was menu.lst...  Doh!  I now do not get the option to select my new version of Ubuntu and if I select the old versions I get a nasty looking, black screen error (can supply if relevant) .

So, I can press "c" and get a grub> prompt but don't know what to do then (I have no floppy drive or CD version of the software because I downloaded it).

I can press 'e' and edit the current menu items but I'm not sure this is what I want to do either.

I'm hoping that it's just a case of getting menu.lst to regenerate based on the existing underlying installation but not sure this can happen without booting with external software so it could be a case of me sending off for a CD or downloading more stuff?

I'd welcome some guidance from people in the know.
Thank you for any help,
T

---

### Post by mörgæs on 2010-10-10
If you download 10.04 or 10.10 (best is to do this from a torrent) and run as a live CD, is your touchpad recognised out of the box? Chances are that you don't need any of you old customisations.

---

### Post by oldfred on 2010-10-10
After several updates where I used keep I vowed never to do that again. I do try to backup any custom edited config files in /etc so I can go back and add something if needed but in most cases the newer settings are better.

If you cannot boot you have to manually boot, or use a liveCD to manually edit the menu.lst with the new kernels.

Manual boot:

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,3) or sdb3
sh:grub>ls (hd1,3)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,3)/vmlinuz root=/dev/sdb3
sh:grub>initrd (hd1,3)/initrd.img
sh:grub>boot

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

---

### Post by Tetterley on 2010-10-15
> **oldfred said:**
> After several updates where I used keep I vowed never to do that again. I do try to backup any custom edited config files in /etc so I can go back and add something if needed but in most cases the newer settings are better.

If you cannot boot you have to manually boot, or use a liveCD to manually edit the menu.lst with the new kernels.

Manual boot:

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,3) or sdb3
sh:grub>ls (hd1,3)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,3)/vmlinuz root=/dev/sdb3
sh:grub>initrd (hd1,3)/initrd.img
sh:grub>boot

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

OK, the <solved> is a bit hasty I'm afraid...!!  I'm a junior Unix user at work and on the database side of things rather than systems.  At home I am trying to get into Ubuntu because I want to ditch Windows.  So, can you take it a bit more steady for me...

I can't say that I understand your reply.  I'm busily reading the document at the link but so far what I'm getting is that the menu.lst that is causing me problems has been deprecated. 

I'm afraid I don't know how to make a liveCD nor manually boot (from the instructions you gave), all experts were in my shoes once eh?  

Hopefully you'll have a bit of patience with me and try explaining again.

Thanks (and sorry that I'm struggling to fathom it out),
T

p.s. I will never again select "keep"!!

---

### Post by oldfred on 2010-10-15
Whatever system you have installed, you need to have a liveCD, bootable USB, or repair CD to allow getting into your system to make repairs. I have all of those. Several liveCDs of versions of Ubuntu, ISOs on USB keys that are bootable including system rescue, gparted, super grub, parted. You always have to have a way to boot and then some info on how to do repairs.

Download current version and 32bit or 64 bit that you have installed and make CD. If your computer will boot USB flash drives that is also a good alternative.
Also has links to alternative install -text mode & not liveCD, CD & USB install instructions
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

From a liveCD run this and then we can give more specific instructions:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Also lots of good info:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by Tetterley on 2010-10-16
Hi oldfred

I used a 10.10 CD to live boot and ran the script, results below.  As far as I can see, it's as I thought, the operating system upgraded ok to 10.04.1 LTS from 8.04.1 but the menu is pointing to the old installation because I selected 'keep' rather than 'update' menu.lst.

Glad of a pointer to help me change this.

Thanks for your help,
T

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       240,974       240,912  de Dell Utility
/dev/sda2             241,664    21,211,896    20,970,233   7 HPFS/NTFS
/dev/sda3    *     21,213,184   472,697,558   451,484,375   7 HPFS/NTFS
/dev/sda4         472,712,686   625,139,711   152,427,026   f W95 Ext d (LBA)
/dev/sda5         619,898,880   625,139,711     5,240,832  dd Dell Media Direct
/dev/sda6         472,712,688   613,811,519   141,098,832  83 Linux
/dev/sda7         613,811,583   619,884,089     6,072,507  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1981 MB, 1981808640 bytes
1 heads, 1 sectors/track, 3870720 cylinders, total 3870720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               3,552     3,870,719     3,867,168   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D8-070F                              vfat       DellUtility                   
/dev/sda2        E652465652462B9D                       ntfs       RECOVERY                      
/dev/sda3        5CD2494AD2492A1A                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        E44E-B74A                              vfat       MEDIADIRECT                   
/dev/sda6        b8c7e657-08fe-4fcb-bfbf-2dd0585352a1   ext3                                     
/dev/sda7        62a49452-0020-495c-8dfc-dca3d20e3752   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E0FD-1813                              vfat       KINGSTON                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=1024

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b8c7e657-08fe-4fcb-bfbf-2dd0585352a1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=b8c7e657-08fe-4fcb-bfbf-2dd0585352a1 ro quiet i8042.nomux=1 splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=b8c7e657-08fe-4fcb-bfbf-2dd0585352a1 ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=b8c7e657-08fe-4fcb-bfbf-2dd0585352a1 ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=b8c7e657-08fe-4fcb-bfbf-2dd0585352a1 ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=b8c7e657-08fe-4fcb-bfbf-2dd0585352a1 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=b8c7e657-08fe-4fcb-bfbf-2dd0585352a1 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title        Microsoft Windows XP Embedded
root        (hd0,4)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b8c7e657-08fe-4fcb-bfbf-2dd0585352a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=62a49452-0020-495c-8dfc-dca3d20e3752 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 243.6GB: boot/grub/menu.lst
 243.7GB: boot/grub/stage2
 243.6GB: boot/initrd.img-2.6.24-22-generic
 243.7GB: boot/initrd.img-2.6.24-22-generic.bak
 243.7GB: boot/initrd.img-2.6.32-25-generic
 243.6GB: boot/vmlinuz-2.6.24-22-generic
 243.7GB: boot/vmlinuz-2.6.32-25-generic
 243.7GB: initrd.img
 243.7GB: vmlinuz

```

---

### Post by oldfred on 2010-10-16
If you get the grub menu you can manually boot. 

Or you can press e at the grub menu and edit the grub entry:

You will see these:
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=b8c7e657-08fe-4fcb-bfbf-2dd0585352a1 ro quiet i8042.nomux=1 splash
initrd        /boot/initrd.img-2.6.24-22-generic

Change to this (uses links in root to correct newest kernel):
kernel  /vmlinuz root=/dev/sda6 ro
initrd   /initrd.img

control x to boot

Once booted 
sudo update-grub

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by Tetterley on 2010-10-17
Thank you for the pointers oldfred, I got there in the end.  Thought I'd include the following for other novices who might read this thread (I realise some things are obvious when you know how).

On presentation of the menu.lst, I pressed c for a grub> command prompt, then...

grub> root (hd0,5)  #same as for old os entry in menu.lst

grub> kernel /vmlinuz root=/dev/sda6 ro  #the 6 relates to information found after running bootinfo script

grub> initrd /initrd.img

grub> boot

I didn't manage to edit the entries in the menu nor could I see where control x could be applied (the option in menu.lst was b for boot).

Thanks again for the help,
T

---

### Post by oldfred on 2010-10-17
Glad you got it working. 

Perhaps the edit menu is something new with grub2, I  have not used grub legacy since grub2 came out and now all the old grub info is fading fast.:)

---

