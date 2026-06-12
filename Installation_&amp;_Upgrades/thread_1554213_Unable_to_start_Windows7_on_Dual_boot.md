---
title: "Unable to start Windows7 on Dual boot"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by bdcollignon on 2010-08-16
Hi,

I have a Dell Inspiron 6400.
Everything was fine with the following OS on dual boot with GRUB:
- Windows XP (Factory Installed)
- Ubuntu 10.04 (Progressively upgraded from Ubuntu 8.04 if I remember well)

This weekend, I made a fresh install of Windows7 to replace my Windows XP (in the same partition: sda2. No change in the other partitions). Install went on OK, but once done, when I started the PC again, I got the Dell start-up screen, and after that just a blinking dash on the top left corner of the screen, and then restarting the Dell start-up screen again and again.

Using a Ubuntu Live-CD, I managed to recover Grub as it was before (redefining root and setup for Grub). Now, I can run Ubuntu again, but if I choose the option "Windows XP Home Edition", which was the one pointing to Windows before, I get the same symptom: nothing, then restart from the Dell start-up screen.

Reading from Ubuntu documentation and different posts, I guess this comes from the different booting system between Windows XP and Windows7 and the fact that Grub has been installed in the MBR... but I'm not sure it's the origin of my problem and I don't know how to fix it. Or does it come from the fact that my Dell computer is "tattooed" (bought it end 2007)?

Can anyone help me? A not-too-complicated way to get Windows7 to boot?

Or should I start from zero again: Dell recovery from factory status (Windows XP, no Ubuntu), upgrade to Windows7, and only then re-install Ubuntu 10.4 with Dual boot? I'd like to avoid this if possible.

Below is the result from "Boot Info Script 0.55" (indeed showing Windows7 on sda2, but as I said, it doesn't boot):

-------
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

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
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 78.5 Go, 78518522880 octets
255 têtes, 63 secteurs/piste, 9546 cylindres, total 153356490 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390    61,882,379    61,785,990   7 HPFS/NTFS
/dev/sda3          61,882,380   145,259,729    83,377,350   5 Extended
/dev/sda5          61,882,443    63,986,894     2,104,452  82 Linux swap / Solaris
/dev/sda6          63,986,958    82,413,449    18,426,492  83 Linux
/dev/sda7          82,413,513   145,259,729    62,846,217  83 Linux
/dev/sda4         145,259,730   153,340,424     8,080,695  db CP/M / CTOS / ...


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D6-071C                              vfat       DellUtility                   
/dev/sda2        D834A03D34A0210C                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        44CA-99CF                              vfat       DellRestore                   
/dev/sda5        c1be4028-191d-41dd-92cf-01168a16d440   swap                                     
/dev/sda6        85e11a18-e1cf-455b-a617-1d41dbed8391   ext3                                     
/dev/sda7        a2ccd4e4-f85b-4e51-b8a8-4ce2f823e208   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda7        /home                    ext3       (rw,relatime)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=85e11a18-e1cf-455b-a617-1d41dbed8391

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
# defoptions=splash

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
# howmany=3

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		85e11a18-e1cf-455b-a617-1d41dbed8391
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		85e11a18-e1cf-455b-a617-1d41dbed8391
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid		85e11a18-e1cf-455b-a617-1d41dbed8391
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		85e11a18-e1cf-455b-a617-1d41dbed8391
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid		85e11a18-e1cf-455b-a617-1d41dbed8391
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		85e11a18-e1cf-455b-a617-1d41dbed8391
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		85e11a18-e1cf-455b-a617-1d41dbed8391
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows NT/2000/XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=a2ccd4e4-f85b-4e51-b8a8-4ce2f823e208 /home           ext3    relatime        0       2
# /dev/sda6
UUID=c1be4028-191d-41dd-92cf-01168a16d440 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda5
UUID=45D2-5573 /media/transfer_sda5 vfat user,rw,exec,noauto,iocharset=utf8,codepage=850 0 0
# Cle USB Avixe
UUID=78BF-9F3E /media/usb_avixe_2GB vfat user,rw,exec,noauto,iocharset=utf8,codepage=850 0 0

=================== sda6: Location of files loaded by Grub: ===================


  36.9GB: boot/grub/core.img
  36.9GB: boot/grub/menu.lst
  36.9GB: boot/grub/stage2
  36.9GB: boot/initrd.img-2.6.32-22-generic
  36.9GB: boot/initrd.img-2.6.32-23-generic
  37.0GB: boot/initrd.img-2.6.32-24-generic
  36.9GB: boot/vmlinuz-2.6.32-22-generic
  37.0GB: boot/vmlinuz-2.6.32-23-generic
  36.9GB: boot/vmlinuz-2.6.32-24-generic
  37.0GB: initrd.img
  36.9GB: initrd.img.old
  36.9GB: vmlinuz
  37.0GB: vmlinuz.old
------------------------

Thanks for your help.

---

### Post by oldfred on 2010-08-16
One advantage of grub2 is its osprober is much better at finding other systems. Grub legacy often had trouble finding and setting up an entry for win7. You may be just able to change your current xp entry from root to rootnoverify as that works better with win7

or this should work.

gksudo gedit /boot/grub/menu.lst

title Windows 7 chainloader (on /dev/sda2)
rootnoverify (hd0,1)
savedefault
chainloader +1

---

### Post by bdcollignon on 2010-08-17
Hi oldfred,

Thanks for the idea. Unfortunately, the "rootnoverify" doesn't change anything. But I noticed that after I select the "Windows7" option from Grub, I have a "Starting up..." flashing on the top left corner of the screen, before it goes back to the Dell startup screen. This happens both with "root" and "rootnoverify" in the "menu.lst" file.

So... any other idea?

You say that Grub2 does a better work.
Should I upgrade to Grub2? How do I do that?
Or a fresh reinstall of Ubuntu 10.4 (I'm intending to do it anyway)?

Looking forward to further advice... Thanks

---

### Post by oldfred on 2010-08-17
Lets see if this shows anything else.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

You can upgrade to grub2, but it is best to totally uninstall both and reinstall only grub2 (grub-pc)

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc
.

---

### Post by bdcollignon on 2010-08-19
Hi,

Unfortunately, Grub2 didn't change anything... and I may have made a mistake that made it worse.

I uninstalled both Grubs and reinstalled Grub2 as you advised. As it was asking me to which partition Grub should be installed, I tried different possibilities (mainly sda and sda6). The result was the same as before: Ubuntu OK, but reboot when trying to log into Windows7. Then I did a try just following your procedure, but not selecting any partition (if I remember well)... and now, instead of the menu with Ubuntu and Windows options, I get a "bash" version of Grub2 with no menu and just the Grub prompt. No possibility to log into any OS.

I tried to solve this via the Ubuntu Live CD again, but didn't manage (trying to re-install Grub or Grub2 on sda, but no change with Grub, and Grub2 was saying it didn't have access to sda when using the live CD).

--> I'm completely blocked... Any idea of instructions I should use from the Grub2 prompt?
Otherwise, I'll just try to reinstall everything from scratch.

Thanks.

---

### Post by varunendra on 2010-08-19
Please post the current output of Boot Info Script as suggested by Fred. I'm sure anyone would need the same for any further suggestions.

Starting from scratch is almost always a sure-shot solution but I'd suggest to try to fix the current one if you are not in a hurry. Because a better understanding of it will ease your future problems.

---

### Post by bdcollignon on 2010-08-19
Well, I had it... but it's on the Ubuntu install that I can't access anymore. Will try to get it again through the Live CD. Not before Friday evening though as I'm not home.

The output before the switch from Grub to Grub2 is at the beginning of the thread.

---

### Post by varunendra on 2010-08-19
To reinstall Grub2, try [this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"). Try any of the three methods (I've tried the chroot method successfully a couple of times), just make sure to verify & mount the partition in which Ubuntu is installed and install Grub on sda (not sda6).

---

### Post by oldfred on 2010-08-19
If grub2 does not see the windows initially, it boots directly into Ubuntu. You have to hold the shift key down from BIOS until menu appears.

To get grub2's osprober to try to find windows again.

sudo update-grub

I have seen where this can cause windows issues, you may want to delete it from your windows partition. 

 /grldr

---

### Post by bdcollignon on 2010-08-22
OK. I'm back. 

First trying the reinstall methods indicated by varunendra. 
- Method 1: No change. Still getting the "bash" version of Grub2 (mounted sda6 and Grub2 installed on sda).
- Method 2: Same thing. And even worse: I cannot run my USB Live Ubuntu anymore. It stops during the process of starting it. Never had that before... Burning a new Live CD. OK. The Live CD works.
- Method 3: "sudo mount --bind /dev  /mnt/dev" doesn't work. I get the answer "mount: mount point /mnt/dev does not exist". Same for /mnt/proc and /mnt/sys

I then found this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Master%20Boot%20Record](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Master%20Boot%20Record)

Thanks to this one, I found back my Grub2 menu.

Now back to the point where I can again start my "old" Ubuntu 10.4, but not Windows7 (the Windows7 entry goes bak to the Dell start menu).

I'm trying further...

---

### Post by bdcollignon on 2010-08-22
Hi,

Good news: deleting '/grldr' from my Windows partition made the trick. I now have a working dual boot on Win7 and Ubuntu 10.04.

Thanks to both of you, Fred and varunendra for the help.

For reference, you'll find below the current results of the Boot-Info-Script.

Next step will be to make a fresh install of Ubuntu 10.04 as my current one is a bit "clogged" and I want to start again with a clean one. No news will be good news on this one ;o).

--------------
```
               Boot Info Script 0.55    dated February 15th, 2010                    

STATUS: 22/08/2010

Ubuntu 10.04 (Install updated from previous versions) 
 and 
Win7 (New install) working... after removing "/grldr" from Windows partition

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 72209494 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 78.5 Go, 78518522880 octets
255 têtes, 63 secteurs/piste, 9546 cylindres, total 153356490 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390    61,882,379    61,785,990   7 HPFS/NTFS
/dev/sda3          61,882,380   145,259,729    83,377,350   5 Extended
/dev/sda5          61,882,443    63,986,894     2,104,452  82 Linux swap / Solaris
/dev/sda6          63,986,958    82,413,449    18,426,492  83 Linux
/dev/sda7          82,413,513   145,259,729    62,846,217  83 Linux
/dev/sda4         145,259,730   153,340,424     8,080,695  db CP/M / CTOS / ...


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D6-071C                              vfat       DellUtility                   
/dev/sda2        D834A03D34A0210C                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        44CA-99CF                              vfat       DellRestore                   
/dev/sda5        c1be4028-191d-41dd-92cf-01168a16d440   swap                                     
/dev/sda6        85e11a18-e1cf-455b-a617-1d41dbed8391   ext3                                     
/dev/sda7        a2ccd4e4-f85b-4e51-b8a8-4ce2f823e208   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda7        /home                    ext3       (rw,relatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 85e11a18-e1cf-455b-a617-1d41dbed8391
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 85e11a18-e1cf-455b-a617-1d41dbed8391
set locale_dir=($root)/boot/grub/locale
set lang=fr
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, avec Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 85e11a18-e1cf-455b-a617-1d41dbed8391
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-24-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 85e11a18-e1cf-455b-a617-1d41dbed8391
	echo	'Chargement de Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro single 
	echo	'Chargement du disque mémoire initial...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 85e11a18-e1cf-455b-a617-1d41dbed8391
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-23-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 85e11a18-e1cf-455b-a617-1d41dbed8391
	echo	'Chargement de Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro single 
	echo	'Chargement du disque mémoire initial...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 85e11a18-e1cf-455b-a617-1d41dbed8391
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 85e11a18-e1cf-455b-a617-1d41dbed8391
	echo	'Chargement de Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 ro single 
	echo	'Chargement du disque mémoire initial...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 85e11a18-e1cf-455b-a617-1d41dbed8391
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 85e11a18-e1cf-455b-a617-1d41dbed8391
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d6-071c
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d834a03d34a0210c
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda4)" {
	insmod fat
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 44ca-99cf
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=85e11a18-e1cf-455b-a617-1d41dbed8391 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=a2ccd4e4-f85b-4e51-b8a8-4ce2f823e208 /home           ext3    relatime        0       2
# /dev/sda6
UUID=c1be4028-191d-41dd-92cf-01168a16d440 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda5
UUID=45D2-5573 /media/transfer_sda5 vfat user,rw,exec,noauto,iocharset=utf8,codepage=850 0 0
# Cle USB Avixe
UUID=78BF-9F3E /media/usb_avixe_2GB vfat user,rw,exec,noauto,iocharset=utf8,codepage=850 0 0

=================== sda6: Location of files loaded by Grub: ===================


  36.9GB: boot/grub/core.img
  36.9GB: boot/grub/grub.cfg
  36.9GB: boot/initrd.img-2.6.32-22-generic
  36.9GB: boot/initrd.img-2.6.32-23-generic
  37.0GB: boot/initrd.img-2.6.32-24-generic
  36.9GB: boot/vmlinuz-2.6.32-22-generic
  37.0GB: boot/vmlinuz-2.6.32-23-generic
  36.9GB: boot/vmlinuz-2.6.32-24-generic
  37.0GB: initrd.img
  36.9GB: initrd.img.old
  36.9GB: vmlinuz
  37.0GB: vmlinuz.old
```

---

