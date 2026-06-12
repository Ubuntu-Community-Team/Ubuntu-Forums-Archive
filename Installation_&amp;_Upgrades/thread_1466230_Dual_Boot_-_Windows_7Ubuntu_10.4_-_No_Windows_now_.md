---
title: "Dual Boot - Windows 7/Ubuntu 10.4 - No Windows now after upgrade"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Linux7 on 2010-04-30
I just did an upgrade from 9.10 to 10.04 and now I can't boot into Windows 7 on this dual boot desktop.  I usually do a clean install but with a laptop and desktop a copy of Windows 7 and Ubuntu on each machine it's getting very tiring with 4 os's so opted for the upgrade this time.

During the installation there was a window that game up about upgrading grub and what devices to install it on.  The help box was not very complete and seemed to say to click all the check boxes which included the main drive and it's partitions including windows.  During the install somewhere it said something like grub could not be installed on one of the devices which I think was sda6 which is probably the Windows 7 partition.

So how would I get the option of booting into Windows 7 on startup as now I only get a blank black screen when I click on the Windows 7 option upon bootup?  I hope I don't have to reinstall one or both os's again from scratch as this is becoming to much work to do on two systems every 6 months, especially with the amount of programs I have installed.

Is this a simple fix or can you give me a suggestion on what to do?

Thanks....

---

### Post by from_au on 2010-04-30
Im having same problem i had windows7 but after i nstalled Ubuntu 10.04 i cant get in to windows 7 anymore but im lucky i had backup from my windows 7 and Mbr so i recovered windows 7 and now i cant install ubuntu because of the boot loader probably i will wait for Fedora 13.

---

### Post by ssican on 2010-04-30
**Installing the available updates and rebooting will fix this issue.**

See this information on PHORONIX website:
"An Ubuntu Incident Report is available on the Ubuntu Wiki: 
We had a late discovery of GRUB bootloader bug affecting dual-boot users of Ubuntu. When installing in a dual-boot environment, the other operating system will not appear at first in the GRUB menu. **Installing the available updates and rebooting will fix this issue**. However, it was determined the day of the release that this is not an optimal solution for new users or those not connected to the Internet."
[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng)

Menu entries for GRUB can be re-generated using **update-grub**.

**Updating GRUB After Installation of a New Linux Distribution or Kernel**: 
**Updating GRUB**
Updating GRUB to recognize new Linux distributions or kernel images can be done in two ways, **automatically** and manually.

"**The automatic procedure involves executing a simple command **which will scan your boot partition for new kernel images and make relevant entries for them in the GRUB configuration file. **The command is "update-grub" or "sudo update-grub" depending on your current user permissions**"
[http://www.brighthub.com/computing/linux/articles/36648.aspx](http://www.brighthub.com/computing/linux/articles/36648.aspx)

---

### Post by dvlchd3 on 2010-04-30
@ssican - I believe that was fixed before the ISOs were released.  Unless the users got the ISO from an unofficial source, 10.04 was pushed back a couple of hours yesterday to solve this issue:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765)

Nonetheless, please do try to run ```
sudo update-grub
```  If this does not resolve the issue run:
```
sudo osprober
``` and post the output here.

---

### Post by uzuzjmd on 2010-05-02
Followed the instruction 
sudo update-grub

> julian@julian-desktop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found:  /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-21-generic-pae
Found kernel: /boot/vmlinuz-2.6.31-20-generic-pae
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


no windows found

The output of sudo os-prober is as follows

> julian@julian-desktop:~$ sudo os-prober
/dev/sda1:Windows 7 (loader):Windows:chain

what now?

---

### Post by Spac3man on 2010-05-02
dual booting lucid and windows 7

Same problem as uzuzjmd, tried "sudo update-grub" and am still unable to boot windows 7; i get a black screen with flashing underscore... windows does not load.

andrew@andrew-laptop:~$ sudo update-grub
[sudo] password for andrew: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

andrew@andrew-laptop:~$ sudo os-prober
/dev/sda1:Windows 7 (loader):Windows:chain

what to do?

---

### Post by Dafau on 2010-05-02
Same problem here but With Windows Vista Ultimate.
[FONT=Arial][SIZE=2][FONT=Arial]Acer laptop with 2 HDD, Vista preinstalled, I  added 1.5 years ago, Ubuntu 9.04, then update to 9.10. Ubuntu created its Grub for dual boot which  worked fine. Yesterday I updated Ubuntu to the new version 10.04 and I have chosen to recreate a new Grub and although  the Grub sees my Vista I am unable to boot it,  the screen remains black with a blinking Underscore character at top lhs. This happens with  another 2 bootable Windows partitions, one being the Recovery  partition.[/FONT][/SIZE][/FONT]
 [FONT=Arial][SIZE=2][FONT=Arial]I am able to boot and use Ubuntu and  see all the files from my Vista  partition.[/FONT][/SIZE][/FONT]
 [FONT=Arial][SIZE=2][FONT=Arial]What I understand is that the new  Ubuntu may have messed up Vista&#8217;s MBR, my guess is that it has created a Windows  7 mbr instead of Vista  mbr, a fdisk -l shows id 7 which means Windows 7.[/FONT][/SIZE][/FONT]
 [FONT=Arial][SIZE=2][FONT=Arial]I used a bootable Vista Recovery  Disc, and although it recognises Vista os, it  is unable to fix it.[/FONT][/SIZE][/FONT]
Tried to reinstall Ubuntu 9.10 that worked fine, no luck either.
It would be good to know how to fix this as 10.04 seems so nice. I do not want to wipe the entire HDD and spend weeks to get something back.
I should have adopted "if it ain't broken don't fix it" strategy or just search in this forum :-(

---

### Post by AzT3K on 2010-05-03
Dont loose hope!!

I fixed my dual boot,

They key was to manually edit the /boot/grub/grub.cfg file to point to the windows install.

read this post:

[http://ubuntuforums.org/showthread.php?t=1469763](http://ubuntuforums.org/showthread.php?t=1469763)

---

### Post by kansasnoob on 2010-05-03
Before everyone tries to jump on the same "fix" please slow down! (Depending on your skill level).

Each and every boot problem should be looked at separately! So please everyone open their own new thread and post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by uzuzjmd on 2010-05-03
Here the output of the Boot Info Summary. I would be thrilled, if someone could figure this out.

> ============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 505929354 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 505929842 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 505929074 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   505,636,863   505,430,016   7 HPFS/NTFS
/dev/sda3         505,645,875   976,768,064   471,122,190   5 Extended
/dev/sda5         505,645,938   958,678,874   453,032,937  83 Linux
/dev/sda6         958,678,938   976,768,064    18,089,127  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   781,401,599   781,401,537   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0C6C641D6C640434                       ntfs       System-reserviert             
/dev/sda2        F028733F287303BE                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        2af4c549-06be-4778-8346-6f74559d25f6   ext4                                     
/dev/sda6        0c322d66-4ff8-4404-b2ca-1a83b70139b4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        69C7-A139                              vfat       Elements                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout        3

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
# kopt=root=UUID=2af4c549-06be-4778-8346-6f74559d25f6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2af4c549-06be-4778-8346-6f74559d25f6

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic-pae
uuid        2af4c549-06be-4778-8346-6f74559d25f6
kernel        /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=2af4c549-06be-4778-8346-6f74559d25f6 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic-pae

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic-pae (recovery mode)
uuid        2af4c549-06be-4778-8346-6f74559d25f6
kernel        /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=2af4c549-06be-4778-8346-6f74559d25f6 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic-pae

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic-pae
uuid        2af4c549-06be-4778-8346-6f74559d25f6
kernel        /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=2af4c549-06be-4778-8346-6f74559d25f6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic-pae

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic-pae (recovery mode)
uuid        2af4c549-06be-4778-8346-6f74559d25f6
kernel        /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=2af4c549-06be-4778-8346-6f74559d25f6 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic-pae

title        Chainload into GRUB 2
root        2af4c549-06be-4778-8346-6f74559d25f6
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        2af4c549-06be-4778-8346-6f74559d25f6
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2af4c549-06be-4778-8346-6f74559d25f6
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2af4c549-06be-4778-8346-6f74559d25f6
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2af4c549-06be-4778-8346-6f74559d25f6
    linux    /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=2af4c549-06be-4778-8346-6f74559d25f6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2af4c549-06be-4778-8346-6f74559d25f6
    echo    'Loading Linux 2.6.32-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=2af4c549-06be-4778-8346-6f74559d25f6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2af4c549-06be-4778-8346-6f74559d25f6
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=2af4c549-06be-4778-8346-6f74559d25f6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2af4c549-06be-4778-8346-6f74559d25f6
    echo    'Loading Linux 2.6.31-20-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=2af4c549-06be-4778-8346-6f74559d25f6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2af4c549-06be-4778-8346-6f74559d25f6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2af4c549-06be-4778-8346-6f74559d25f6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0c6c641d6c640434
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=2af4c549-06be-4778-8346-6f74559d25f6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0c322d66-4ff8-4404-b2ca-1a83b70139b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 259.0GB: boot/grub/core.img
 259.1GB: boot/grub/grub.cfg
 259.1GB: boot/grub/menu.lst
 259.7GB: boot/initrd.img-2.6.31-20-generic-pae
 259.8GB: boot/initrd.img-2.6.32-21-generic-pae
 259.4GB: boot/vmlinuz-2.6.31-20-generic-pae
 259.9GB: boot/vmlinuz-2.6.32-21-generic-pae
 259.8GB: initrd.img
 259.9GB: vmlinuz


---

### Post by uzuzjmd on 2010-05-03
Problem solved.

The reason was that grub overwrote the boot loader. 
Solution

sudo apt-get testdisk
overwrite boot sector with backup

---

### Post by oldfred on 2010-05-03
Just to document the fix that uzuzjmd used with some explaination.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by replikanxxl on 2010-05-08
> **Spac3man said:**
> dual booting lucid and windows 7

Same problem as uzuzjmd, tried "sudo update-grub" and am still unable to boot windows 7; i get a black screen with flashing underscore... windows does not load.

andrew@andrew-laptop:~$ sudo update-grub
[sudo] password for andrew: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

andrew@andrew-laptop:~$ sudo os-prober
/dev/sda1:Windows 7 (loader):Windows:chain

what to do?

my problem is exactly the same.so all i needed is to quote yours.

---

### Post by oldfred on 2010-05-08
See post #12 if that does not solve your problem start a new thread and post results.txt from the boot info script also linked in above post.

---

### Post by OmnyDevi on 2010-05-09
yeah, i just clicked everything so grub installed like, 20 times on sda, sdb, and sdc, sdd, and sde, along with their partitions.

what i have come to understand, and i should have known better anyway, is that it overwrote the windows boot area. so when i went to load windows 7, it was just a blinking cursor prompt on a  black screen.

so i tossed in my windows 7 dvd, went into repair options, selected the command prompt and ran these commands:

bootrec.exe /fixmbr
bootrec.exe /fixboot
bootrec.exe /scanos
bootrec.exe /rebuildbcd

then upon rebooting, only windows 7 will load; there is no grub now at all. however, when i press my esc key during startup for boot priorities, and choose to boot from any drive OTHER than sda, i get grub flawlessly, and can boot into Ubuntu, but not windows. 

all in all it will work well for me, since my wife and whoever else uses this machine will most likely have no idea it is even installed. i am sure now i can just install grub from a live cd, but, i would prefer most people to just load into the windows part on my box and have no idea that Ubuntu is even possible. 

hope that might help someone. be well mates.

---

### Post by OmnyDevi on 2010-05-09
i upgraded no more than 24 hours ago. i lost windows 7 as a result. the iso might be fixed, but the repositories for upgrade from 9.10 might not be, as it upgraded over 1600 packages. 

i got the blank screen with the cursor too, fixed now, but just a heads up.

---

### Post by spin498 on 2010-05-09
I went the Testdisk route worked for me. Quick and easy.

---

### Post by oldfred on 2010-05-09
If you have multiple drives you can change the order in BIOS to boot the drive with grub and leave the windows in the other drive's MBR in case you ever want to directly boot it. Grub will let you boot windows and you can set it as default if others in the family really want windows. I managed to convert spouse to firefox and thunderbird so she now sees no real difference between operating systems.

---

### Post by bembengarifin on 2010-05-10
many thx for the posts, the testdisk worked just fine for me :popcorn:

---

### Post by Analisis on 2010-05-13
Hello,
I have the same problem, after upgrading to Ubuntu 10.4 I can no more access to Windows 7 Starter. I am new to Ubuntu so I need more help to follow the steps to recover from this problem. I have tried sudo update-grub and got:
adolfo@adolfo-laptop:~$ sudo update-grub
[sudo] password for adolfo: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
adolfo@adolfo-laptop:~$ ^C
adolfo@adolfo-laptop:~$ 

but still windows don't load.

I have seen others options searching with google but I am not sure what is the best way. Some people say that is enough using Testdisk but I have not found instructions in how to use Testdisk

Thank you for your help.

---

### Post by wilee-nilee on 2010-05-13
> **Analisis said:**
> Hello,
I have the same problem, after upgrading to Ubuntu 10.4 I can no more access to Windows 7 Starter. I am new to Ubuntu so I need more help to follow the steps to recover from this problem. I have tried sudo update-grub and got:
adolfo@adolfo-laptop:~$ sudo update-grub
[sudo] password for adolfo: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
adolfo@adolfo-laptop:~$ ^C
adolfo@adolfo-laptop:~$ 

but still windows don't load.

I have seen others options searching with google but I am not sure what is the best way. Some people say that is enough using Testdisk but I have not found instructions in how to use Testdisk

Thank you for your help.

Start a thread and post the bootscript in code tags. To do this paste the scrip[t into the reply or thread start and highlight the text and click on the # in the panel,
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Make sure you use the code tags this puts the script in a scrolling window and makes it much easier to read.
Don't try any fixes until you get a response in your own thread if you make changes then repost the script again. Yes testdisk works in some situations, but is not always the answer.

---

### Post by spin498 on 2010-05-14
As I said before, went the testdisk route quick and easy. However, after updates installed I've had to do it again. Any ideas on what upgrades are causing this?

---

### Post by wilee-nilee on 2010-05-14
> **spin498 said:**
> As I said before, went the testdisk route quick and easy. However, after updates installed I've had to do it again. Any ideas on what upgrades are causing this?

If you really want to get to the root of this and get it fixed or your setup fixed you have to start your own thread. Start it with the boot script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
It is important that we know exactly whats going on. And it is important that you start your own thread. ;)

---

### Post by jweaver28 on 2010-05-17
I don't see a separate thread for these dual boot with Windows7 problems, and googling produces more results than really helpful. So my 2 cents here. I have managed to install dual boots with several versions of Ubuntu and Windows XP and Vista with relatively few problems. I've used both Wubi and the standard installation option. 

Windows7 is another matter, IMHO. Wubi doesn't work because of the increased Windows7 startup permissions (the technical term escapes me at the moment). I installed Windows7 as an upgrade, and both months ago with Karmic and this weekend with Lucid, I've managed to so mess up my hard drive that I can't get Windows to start, even with grub2 alternations and with Windows 7 repair discs. Yes, I backed up first, but the backup files through Windows7 show as 0 bytes and won't load. They do show through Ubuntu but also won't load. And because this is a clean upgrade from XP, Windows7 off the CD won't fully load (the unchanging pastoral background has gotten mighty annoying). I realize that one of my mistakes might have been not partitioning the new hard disc through Windows7--or maybe I did and Lucid doesn't recognize it. I thought the recognizing the other OS bug was corrected by now.  Anyway, for what it's worth, here are the bootscript results. Results.txt was with just the hard drive that was working nicely until the latest attempt to dual boot with Windows7. Results1.txt includes the hard drive that was messed up with the previous attempt to bual boot with Karmic (and which subsequently and unsuccessfully became my backup drive).

---

### Post by kansasnoob on 2010-05-17
> **jweaver28 said:**
> I don't see a separate thread for these dual boot with Windows7 problems, and googling produces more results than really helpful. So my 2 cents here. I have managed to install dual boots with several versions of Ubuntu and Windows XP and Vista with relatively few problems. I've used both Wubi and the standard installation option. 

Windows7 is another matter, IMHO. Wubi doesn't work because of the increased Windows7 startup permissions (the technical term escapes me at the moment). I installed Windows7 as an upgrade, and both months ago with Karmic and this weekend with Lucid, I've managed to so mess up my hard drive that I can't get Windows to start, even with grub2 alternations and with Windows 7 repair discs. Yes, I backed up first, but the backup files through Windows7 show as 0 bytes and won't load. They do show through Ubuntu but also won't load. And because this is a clean upgrade from XP, Windows7 off the CD won't fully load (the unchanging pastoral background has gotten mighty annoying). I realize that one of my mistakes might have been not partitioning the new hard disc through Windows7--or maybe I did and Lucid doesn't recognize it. I thought the recognizing the other OS bug was corrected by now.  Anyway, for what it's worth, here are the bootscript results. Results.txt was with just the hard drive that was working nicely until the latest attempt to dual boot with Windows7. Results1.txt includes the hard drive that was messed up with the previous attempt to bual boot with Karmic (and which subsequently and unsuccessfully became my backup drive).

I see no RESULTS.txt or RESULTS1.txt :confused:

---

### Post by jweaver28 on 2010-05-18
I thought they were attached. Seem I closed the extra tab before clicking the upload button. So here goes again. I've included the results2.txt, which is this morning's result, for what it's worth.

---

### Post by oldfred on 2010-05-18
You do not show a windows directory with /Windows/System32/winload.exe as part 2 of the boot process. You show sdb1 as the win7 boot partition with /bootmgr /Boot/BCD.

Did you overwrite a windows partition in sdb or was sda1 your original windows install?

---

### Post by jweaver28 on 2010-05-18
Frankly, I'm not sure. From my frustrating efforts today, it seems /sdb1 was the Lucid boot. And I hope noone was offended by my apparently choosing the "thumbs down" ani for the prior post when I meant to choose the "oops" one--I hadn't enabled all the page's scripts.

I'll explain the completely messed up boots a bit more, and anyone can peruse results3.txt to try to figure out what the latest results were (hint: I'm heading to the computer store). After this post, I decided to try the scary (command line) mode of the supposed RestoreDVD I had made after installing Window7. The other options hadn't worked over the weekend. The method is explained in a microsoft article (927392). The RestoreDVD couldn't find any windows partition on either hard drive, nor the system image that I could see on the 500 GB drive after loading Lucid onto the 1 TB drive. The Bootrec.exe explained in the article didn't fix my problem, but changed the fatal error message from 000000x something to 0x8070057 and eventually 0x0000098. 

Following those Microsoft instructions managed to wipe the Lucid boot record. The Lucid repair option off the CD did not work either, nor did I have an option to just run Lucid off the CD. If I had known what partition Grub had been on, maybe the result would've been a tad more elegant, but 6 options to reinstall using various formatting options, almost all unbootable?

Given the installation-only option, I admit getting the red screen of death (exit code 1) in trying to boot what had been /sdb1, /sdb2 and /sdb7 in the old 10-logical drive version. I couldn't figure out how to get to the syslog, much less what to do there. /sdc1 turned out to be my USB stick. /sda1, /sda2, /sda5 and /sda6 turned out to be the nonworking dual-boots of the old 500 GB drive. I removed it before reinstalling lucid to type this explanation, lest I mess that supposed backup more (even if the RestoreDVD doesn't recognize it). 

I ended up having to resize the largest partition to recreate 2 new logical drives to use as a new Ubuntu boot. Now I can use grub to get into Ubuntu, including the boot removed by today's microsoft instructions, though the bootloader is far from elegant (two 12.2 mb swap files and pretty much identical 20 and 30 gb ext4 logical partitions translating into a couple versions of the old linux kernel as well as the updated one and safe option). Plus, Window7 isn't loading.

I don't doubt part of the problem is Microsoft not being willing to "play nice" with Ubuntu. Their RestoreDVD for Windows7 doesn't work, and messed up the Lucid boot. The restoration options worked much better in XP and Vista. IMHO, on the Ubuntu side, it would be nice to be able to just boot off the Lucid CD to check whether my files still exist instead of further messing up the hard drive by partitioning and reinstalling. And the Ubuntu How-Tos really should be rewritten to distinguish between dual boots of the various Windows OSs. 

Needless to say, I'm frustrated and a tad angry. I don't know that venting via this email (retyped after an allowed script deleted my prior explanation) has done much good. But maybe it's documenting the various recovery problems for posterity. Now I have to run out and buy a new hard drive and format it and reinstall windows in an appropriately partitioned space and then try installing Lucid and then actually transferring my files. Arghhh! And almost another whole day has gone by without being able to get to my work.

---

### Post by oldfred on 2010-05-18
I am not sure what you want, but I would with multiple hard drives keep windows on one drive with its boot loader in that drive's MBR. then install Ubuntu in a second hard drive with grub in that drive's MBR. Select in BIOS to boot the Ubuntu/grub drive and it should also give you the choice to boot windows. If you ever have trouble with Ubuntu, you then can in BIOS switch  back and still boot the windows drive.

Some with large drives always put a operating system on the drive just in case. I have 4 operating systems on my 3 drives, XP and several versions of Ubuntu with different boot loaders in each drive. And each drive could boot without any of the others.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

### Post by jweaver28 on 2010-05-18
Thanks, OldFred, for the info. I was trying to get by with just one hard drive, partitioned into dual boots, with the old drive removable (both not drawing power and more secure). But with these large drives, and the numerous partitions ubuntu wants to create, I see the wisdom of having a smaller drive as the ubuntu one. Frankly, what I was trying to do with the posting, besides venting, was explain to developers how confusing the whole partitioning parocess is, or the ways Ubuntu and Windows can refuse to play nicely together.

---

### Post by KimeraBubble on 2010-05-25
Hi, it all works again if you do a fixboot with a Windows cd and reboot.

---

### Post by jweaver28 on 2010-05-26
Glad to hear that the Win7 cd worked for KimeraBubble. However, it didn't work for me. It's been of week of Windows hell (Microsoft flavor). My repair cd also didn't work. Apparently, Ubuntu wrote over too much of the the Windows7 installation.  Not only couldn't the repair and original CDs not find it, nor could supergrub. And while I backed up my files externally, apparently the directory got corrupted so I could only restore the backup from 2 months ago (first backup after the first Win7/Ubuntu dual boot disaster) although the other backups showed on that drive. I had made another backup onto my other PC a week earlier, via the old drag and drop method, so I've probably recovered most everything, but I now have a lot of duplicate files to find and delete. Sigh....

So now I'm on a clean install of Windows7, but Wubi still won't work with Window7. I'm darn scared to use any Ubuntu 10.4 install CD. FYI, I did acquire a small used SATA drive and installed Ubuntu on it, as OldFred and eventually Microsoft tech support suggested. But it seems crazy to have to go into BIOS or a SuperGrub CD and change to that hard drive every time I want to change OSes. FYI, my BIOS will only boot from floppy (physically not installed), CD or whatever in BIOS has been designated the first hard drive......

---

### Post by oldfred on 2010-05-26
If your motherboard supports SATA drives it almost for sure has another setting on which drive is the first drive or primary master. With IDE we set jumpers, but with SATA it is in software. The drive selection is separate from the boot order of HD, CD, floppy, USB, etc. If you try the single boot key (mine is f12) and choose hard drive does it open another choice for which hard drive?

---

### Post by gerola on 2010-07-29
:-({|= Boa Tarde! Estou realmente preocupado, como você, com o Ubuntu 10.4. As modificações introduzidas criaram uma série de problemas.
1 - Dual Boot não funciona no windows 7. Após instalado, simplesmente acaba com qualquer boot, seja dAgora uso um pendriver gravado com o Unetbootin, quando quero entrar no Ubuntu (versão 8.4).
2 - Emprestei meu CD para um amigo instalar o Ubuntu 10.4 no seu computador. Maior zebra: não funcionou a parte gráfica (rodadndo com o CD). Meu amigo foi obrigado a usar a versão 9.10, que funcionou na sua placa de vídeo Radeon.
O QUE VAMOS FAZER? VOLTAR EM MASSA PARA O 9.10 ATÉ CORRIGIREM?
A Microsoft conseguiu afastar o Linux do dual boot?
Se alquém tiver uma luz, agradeço!

---

### Post by gerola on 2010-07-29
First of all, thank you for the oportunity to explain my problem.
Realy we have multi problems with Ubuntu 10.4.

1 - No boot after the instalation with dual boot with Windows7. It was a "drama" to restore windows after the deletion of the MBR and Grub.
2 - My friend problem was with video card Radeon. Only solved coming back to 9.10 version.

Realy Microsoft put way the dual boot?
Please, I have no Linux in my computer!
Gerola

---

### Post by starlinq on 2011-03-07
> **oldfred said:**
> Just to document the fix that uzuzjmd used with some explaination.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I have a dual-boot OS notebook. Recently I have had a problem with Windows 7 boot (black blank screen) after Ubuntu 10.04 kernel update (before I had no any problems). I was lucky to fix the problem using the cited link. However, in my case I had no 'BackupBS' menu option, instead of that I had a 'RebuildBS' menu item, and I selected that. Finally my Windows 7 boot problem is fixed.

---

