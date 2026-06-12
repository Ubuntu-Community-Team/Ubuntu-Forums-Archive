---
title: "installation on a system without operating system with no usb and bad cd rom"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by usman4575 on 2011-04-10
Hi,
I have a sony vaio FS-315M, it has a CD ROM which is out of order for sometime. It used to have windows XP but i messed up windows MBR while attempting to install ubuntu thru USB by the help of PLOP manager.
Now i am messed up because system can't boot giving me "Missing Operating System" error and i have no CD ROM and USB support.
BIOS supports CD-ROM, HDD, FLOPPY, NETWORK.
What are options for me? Please help as i am stuck badly in this situation.

---

### Post by coffeecat on 2011-04-10
I read your other thread but we need to clarify something. When you installed plop, did that mean that you still had Windows only on the internal drive? And did that mean that you installed Ubuntu to an external USB drive?

If so, you need to be able to repair the Windows mbr. Two ways:

1 - Using a bootable floppy. I'm sure it's possible but I've never done this. I'll have a search and post again if I find something.

2 - Remove the hard drive and use another machine. The drive must be easily removable - with some laptops they are and some not. And you would need a compatible 2[FONT=Times New Roman, serif]½"[/FONT]  USB enclosure. Do you have one? If yes, I can post details of how you can repair the Windows mbr from an Ubuntu live CD or Ubuntu installation on another machine.

---

### Post by usman4575 on 2011-04-10
Actually yes, i wrote before and some body suggested plop and i used it to use USB to install Ubuntu 10.10. Ubuntu 10.10 actually replaced MBR and then what i could get in boot menu was only a GRUB (Ubuntu) menu which included an option to boot from windows XP. I played with ubuntu and almost forgot about windows XP but then i heard about Ubuntu 11.04 beta release and thought to give it a try. I installed Natty but i did not run because of the error during software installation and i tried repairing boot menu because windows xp option was not available anymore. I ended up probably removing ubuntu MBR print which resulted in the message "Missing Operating System". This is the whole story.
I have another laptop though and its CDROM is working and has USB boot option too.
I will try removing the drive but any suggestion/ expert advice is worth a trillion cause i used to use sony vaio laptop most extensively.
Thanks for response

---

### Post by coffeecat on 2011-04-10
Repairing the Windows mbr will mean that you won't be able to boot into Ubuntu. It will boot straight into Windows. In your situation I believe that would be best because it sounds as though your 11.04 installation is broken and to repair that you would need to be able to boot from CD or USB - which is impossible for you. If you need to run Ubuntu from that machine you'd be best to reinstall Ubuntu using Windows and plop as before. But you need to boot into Windows first.

When I asked if you can remove the HD from the laptop I envisaged putting it in a USB enclosure, not another laptop. But if you are prepared to fit it to another laptop, that makes it fairly easy. Two words of warning: your Sony Vaio almost certainly has an older IDE/PATA hard drive. If the other laptop is less than about 3-4 years old it will probably have a newer SATA drive. If so, you will not be able to fit the older drive into the other laptop. Also, are you confident swapping hard drives in laptops? If not, then I suggest you don't do this.

But if you are able to proceed, this is what to do. Fit the HD from the Sony into the other laptop. Boot a live CD or live USB of Ubuntu and make sure you can connect to the internet. You will need to download something. Now look at this post:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

There are three different ways of restoring the equivalent of the Windows mbr described there. I suggest going with the first one, the lilo method. It seems to work reliably.

Once you have done that, shut the machine down. Do not attempt to boot Windows while that HD is still in the "other" laptop. Windows will have a fit if it detects unfamiliar hardware and you may run into activation problems. Put the drive back into the Sony and see if it will boot Windows there.

If you are not happy putting the HD in the other laptop, or if you can't because of IDE - SATA incompatibility, post back and we'll search for another solution.

---

### Post by usman4575 on 2011-04-10
yes my older laptop HDD cannot be connected to the newer laptop, so that's not possible. i will re-install ubuntu 10.10 so i need to get in to windows and install plop as before. any other suggestion?
What if i buy an external DVD drive? will it be possible to boot from that?

---

### Post by C.S.Cameron on 2011-04-10
To easily install Ubuntu move your HDD to an external enclosure, about $10, and install Ubuntu from the other laptop.

---

### Post by amerinde on 2011-04-10
> **C.S.Cameron said:**
> To easily install Ubuntu move your HDD to an external enclosure, about $10, and install Ubuntu from the other laptop.

But, if he does this, where is grub?? on the external or one the internal. when i installed ubuntu, i had no choice where to put it.

---

### Post by coffeecat on 2011-04-10
> **usman4575 said:**
> 
What if i buy an external DVD drive? will it be possible to boot from that?

Unfortunately not because an external DVD will be connected by USB and you cannot boot from USB.

> **amerinde said:**
> But, if he does this, where is grub?? on the external or one the internal. when i installed ubuntu, i had no choice where to put it.

In 10.10, if you choose the manual/advanced option you can designate where to install grub.

---

### Post by usman4575 on 2011-04-10
That means my options are limited to either removing the hard drive and hooking it to some other system and fixing with FIXMBR command or removing and changing or repairing original CD ROM. The hard drive is PATA, it has 40 pin connector. By the way i have a Dell desktop in my office, may be i try connecting my hard drive to that desktop?

---

### Post by coffeecat on 2011-04-11
> **usman4575 said:**
> By the way i have a Dell desktop in my office, may be i try connecting my hard drive to that desktop?

You would need either a suitable USB enclosure or an adapter to connect the laptop-size IDE interface with whatever motherboard interface the Dell has.

By the way, you mention running fixmbr. That's probably not going to work because when running fixmbr, the drive you are working on needs to be the primary one. Hooking it up any way but in the first HD interface means it won't be. Which is why I posted the link to a method using an Ubuntu CD. Using lilo, for example, you can restore the mbr to sda, sdb, sdc, or whichever device your drive appears as once you've connected it. And, of course, you'll need to determine whether it is sda, sdb, or whatever before you run those lilo commands.

---

### Post by usman4575 on 2011-04-11
I tried with Dell desktop but it too has newer SATA cable so hard luck, today i will go search for an enclosure in the market.
I thought i will remove Dell's primary hard drive and instead hook mine and boot as from CD to use FIXMBR. I don't know the method when using as secondary drive. I will go thru method that u sent link before 'LILO'.

---

### Post by usman4575 on 2011-04-11
Ok, i have got the 2.5 inch IDE to USB enclosure. How to restore MBR? can u please suggest.

---

### Post by coffeecat on 2011-04-11
With the HD in the USB enclosure, boot up a live Ubuntu CD or USB in another machine and choose "try Ubuntu". When you get to the desktop, plug in the USB drive. If a Nautilus browser window opens, you can close it. It won't be needed. Now open a terminal and run this command:

```
sudo fdisk -lu
```Have a look at the output and decide which is the HD you've put in the enclosure. If the machine you use has only one hard drive, then its drive will probably be sda and the one in the USB enclosure sdb. But this cannot be guaranteed. Some BIOSs detect drives in a different order.

Make sure you are connected to the internet and have a look at the post I linked to in my post #4 in this thread. You will be running the lilo command. This is where you need to be very, very, very careful to correctly identify the drive in the USB enclosure. You don't want to be installing lilo to the mbr of the internal drive of the machine you are using.

I'll assume the drive in the USB enclosure is sdb, but do check this and if you are unsure, post the output of the fdisk command.

This is what you run:

```
sudo apt-get update
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```Change sdb to whatever it should be. There may be a lilo error message which you can ignore.

If that works, then when you put the drive back in the Sony laptop, Windows should boot.

---

### Post by usman4575 on 2011-04-11
I tried starting ubuntu 10.10 from the newer HP laptop but it refuses to boot from the ubuntu? I tried USB boot and also boot from the CDROM but the same result. I have attached images to show the screen shots of the error it was showing. Infact i tried to run Ubuntu live CD before this problem on this newer laptop and had same problem so abandoned the idea. Now its a big disturbance. Please explain the problem? thanks

---

### Post by coffeecat on 2011-04-11
The first screenshot shows you dropping to a busybox shell. The commonest cause for this is a corrupt CD. Double-check the md5sum for the downloaded ISO and if it passes, try burning another CD, but this time at the slowest possible speed. Also, if you tap the spacebar when the two small icons appear at the base of the screen, you get a CD boot menu with a CD integrity check third (if I remember correctly) choice in the menu.

The second screenshot is intriguing. That was from a USB created with startup disk creator, yes? And you used startup disk creator in Ubuntu 10.04 but using a 10.10 ISO? Am I correct? It's a known bug due to a syslinux incompatibility. You need to use the 10.04 startup disk creator with the 10.04 ISO and 10.10 with 10.10.

---

### Post by usman4575 on 2011-04-11
Ok, thanks for guiding me, i was able to run Ubuntu Live CD and i did all the commands and used lilo to restore Mbr on my old second hard drive exactly the same way as you wrote and i plugged it in my sony laptop but hard luck cause it now says
"No boot signature in partition"
"Operating System not found"
Please do look at this and suggest something else.

---

### Post by coffeecat on 2011-04-11
Re-reading your OP, I guess that when the mbr was written using plop, something may have happened to the boot sector of your Windows partition.

> **usman4575 said:**
> "No boot signature in partition"
"Operating System not found"

Or it's possible that it's something as simple as the boot flag not set on your Windows partition. Rather than speculate, let's investigate. Fortunately, there's an easy way to do this. You're going to have to put the drive back in that enclosure, boot the Ubuntu CD up again on your HP laptop and plug the enclosure in and switch it on. Now go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for legibility. You can use the # icon in the message toolbar for this. 

This output will give us all the information we need to know about your old Sony HD in the enclosure. It will also give us information about the internal HD on the HP which will be irrelevant. I will have to log off now and I won't be logging on again for a few hours. If, in the meantime, you post your RESULTS.txt and someone comments on it, make sure they understand the situation you are in. We are using the boot script in an unusual way and I don't want you to get well-meaning but misleading advice.

---

### Post by usman4575 on 2011-04-11
Below is all the output, i used lilo on c as its my window xp drive 


Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc

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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

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

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   307,628,684   307,219,085   7 HPFS/NTFS
/dev/sda3         307,628,685   574,982,414   267,353,730   f W95 Ext d (LBA)
/dev/sda5         307,628,748   574,982,414   267,353,667   7 HPFS/NTFS
/dev/sda4         574,984,192   579,178,495     4,194,304   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007624704 bytes
32 heads, 63 sectors/track, 3882 cylinders, total 7827392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,826,111     7,826,049   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    88,052,264    88,052,202   7 HPFS/NTFS
/dev/sdc2         117,387,264   153,128,959    35,741,696  83 Linux
/dev/sdc3          88,052,387   117,386,954    29,334,568   f W95 Ext d (LBA)
/dev/sdc5          88,052,389   117,386,954    29,334,566   7 HPFS/NTFS
/dev/sdc4    *    153,128,960   156,301,311     3,172,352  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BC88631A8862D286                       ntfs       SYSTEM                        
/dev/sda2        3810845910841FCC                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        5A7B-23E5                              vfat       HP_TOOLS                      
/dev/sda5        01CBDDF1E75ADE60                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        08F8-3E4C                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        30B80F5AB80F1E4A                       ntfs                                     
/dev/sdc2        fbade52d-2034-426e-b8ad-f08bf97a0f6e   ext4                                     
/dev/sdc3: PTTYPE="dos" 
/dev/sdc4        093fcc4d-3e0f-40aa-8f01-cd7170aceeb9   swap                                     
/dev/sdc5        01CBDEBBC09BAEB0                       ntfs                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/3810845910841FCC  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/01CBDEBBC09BAEB0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc2        /media/fbade52d-2034-426e-b8ad-f08bf97a0f6e ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/30B80F5AB80F1E4A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdc1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
c:\plop\plpbtldr.bin="Install Plop Boot Manager"
=========================== sdc2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root fbade52d-2034-426e-b8ad-f08bf97a0f6e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root fbade52d-2034-426e-b8ad-f08bf97a0f6e
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if hwmatch ${prefix}/gfxblacklist.txt 3; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root fbade52d-2034-426e-b8ad-f08bf97a0f6e
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=fbade52d-2034-426e-b8ad-f08bf97a0f6e ro   splash quiet vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root fbade52d-2034-426e-b8ad-f08bf97a0f6e
    echo    'Loading Linux 2.6.38-7-generic ...'
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=fbade52d-2034-426e-b8ad-f08bf97a0f6e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-7-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root fbade52d-2034-426e-b8ad-f08bf97a0f6e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root fbade52d-2034-426e-b8ad-f08bf97a0f6e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 30B80F5AB80F1E4A
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=fbade52d-2034-426e-b8ad-f08bf97a0f6e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=093fcc4d-3e0f-40aa-8f01-cd7170aceeb9 none            swap    sw              0       0

=================== sdc2: Location of files loaded by Grub: ===================


  64.5GB: boot/grub/core.img
  62.3GB: boot/grub/grub.cfg
  60.6GB: boot/initrd.img-2.6.38-7-generic
  60.3GB: boot/vmlinuz-2.6.38-7-generic
  60.6GB: initrd.img
  60.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  81 6a 77 00 7a 3b 00 00  00 00 00 00 02 00 00 00  |.jw.z;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 4c 3e f8 08 4e  4f 20 4e 41 4d 45 20 20  |..)L>..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 18  77 00 00 66 ba 00 00 00  |..E}.f..w..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by C.S.Cameron on 2011-04-11
If your original intention was to install and dual boot Windows and Ubuntu on the old computer, it is best to disable the new computers internal hard drive insert the external inclosure, boot the Live CD, (after checking MD5SUM of iso), and install to the external drive as if it was internal. 

Use manual partitioning.
The only partition to modify or format is **sda2**.
Select primary
Use default partition size
Select ext4
Mount point "/"
Confirm "Device for boot loader installation" points to the correct drive. **sda, not sda2**.
Then click install.

With 10.10 avoid installing any proprietary drivers before putting the drive back in the old computer.

If you can't disable the new hard drive:
The only partition to modify or format is sdc2
Confirm "Device for boot loader installation" points to the correct drive. **sdc, not sdc2**. be extra careful when partitioning.
Once back in the old computer and booted from Ubuntu do a sudo update-grub to remove mention of the new hard drive.

grub2 will take over from mbr, lilo and plop as the bootloader.

---

### Post by coffeecat on 2011-04-12
I believe the problem is simple and simply fixed. Your Windows partition is sdc1, but the boot flag is set on sdc4, your Linux swap partition. 

> **usman4575 said:**
> 
Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    88,052,264    88,052,202   7 HPFS/NTFS
/dev/sdc2         117,387,264   153,128,959    35,741,696  83 Linux
/dev/sdc3          88,052,387   117,386,954    29,334,568   f W95 Ext d (LBA)
/dev/sdc5          88,052,389   117,386,954    29,334,566   7 HPFS/NTFS
/dev/sdc4    *    153,128,960   156,301,311     3,172,352  82 Linux swap / Solaris

When you have Windows booting code in the mbr (or an alternative such as  that installed with lilo) it simply looks for the partition with the  boot flag and hands over the boot process to the boot sector of that  partition. In your case it's trying to pass the boot process to your swap partition which obviously won't work.

Do as before, drive in enclosure, boot up the live CD/USB (it looks as though you are using a live USB) in your HP laptop and go to the live desktop session. Open System > Administration > Gparted. In the top-right of the Gparted window, where it says /dev/sda, drop down the menu and choose /dev/sdc. Before you do anything, check that this is the correct drive. Your 80GB drive will appear as 74.5GiB (gibibytes). Now highlight the first partition, sdc1, open the "Partition" menu and select "Manage flags". Simply tick the boot flag box. It will take a few seconds and then you're done. Try the HD in the Sony laptop again.

By the way, I asked you to put the boot script output in code tags for legibility. It's very difficult to read posted raw. See how much better the above that I've quoted can be read in code tags.

```
Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    88,052,264    88,052,202   7 HPFS/NTFS
/dev/sdc2         117,387,264   153,128,959    35,741,696  83 Linux
/dev/sdc3          88,052,387   117,386,954    29,334,568   f W95 Ext d (LBA)
/dev/sdc5          88,052,389   117,386,954    29,334,566   7 HPFS/NTFS
/dev/sdc4    *    153,128,960   156,301,311     3,172,352  82 Linux swap / Solaris
```If you need to know more about using the forum's BBCode, this is a useful page:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

You can simply type [noparse]```
[/noparse] and the beginning and  [noparse]
```[/noparse] at the end of the text you want to enlcose, or use the # icon on the message toolbar.

---

### Post by usman4575 on 2011-04-12
Coffeecat, i am really really grateful for all the help that you provided. My windows XP started like it starts everyday without any problem. You really have a very sound knowledge about these things. Linux really rocks, it has very simple but very strong tools; i am convinced.
Sorry for the discourteousness about #codes cause i really had no idea how to use them and was in a hurry to post the output so that you could see that and it was really 3 a.m here and i had to go to office at 6 a.m! so i couldn't concentrate on it.
Anyway, may God help you cause you help others. People like yourself convince me that there are still enough good people in the world.

---

### Post by coffeecat on 2011-04-12
> **usman4575 said:**
> Sorry for the discourteousness about #codes cause i really had no idea how to use them

No problem at all. I didn't see it as discourtesy, merely unfamiliarity with BBCode. It took me some time to get my head around all these BBCode tags when I first started using a forum. :)

I'm glad it's sorted, and Windows is booting on your Sony laptop. It's been quite a journey getting there! That's quite a challenge you have installing to or maintaining a laptop with a broken CD and no ability to boot from USB.

Good luck with that machine and good luck with Ubuntu!

---

