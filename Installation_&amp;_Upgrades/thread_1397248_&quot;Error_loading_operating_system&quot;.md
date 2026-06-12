---
title: "&quot;Error loading operating system&quot;"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by Arachan on 2010-02-03
[FONT=Arial]Hello,

I'm new to both Ubuntu and this forum, so please try to bear with me.

I have a 500GB HDD with these partitions  [/FONT][ATTACH]145802[/ATTACH][FONT=Arial] [/FONT]

I'm currently using the live CD to boot because when I try to boot to this HDD it simply comes up with the error "Error loading operating system". It was working fine until I started reformatting a different drive with XP on it; since then it has had the error.

As far as I know I need to reconfigure GRUB to boot to the correct partition, but I do not know how to do this.

[FONT=Arial]I know that there are already threads about booting/GRUB problems. I have looked at a lot of them but because no one has exactly the same problem as me I do not know what to do.

I would really appreciate any help,
Thanks in advance,
Arachan.
[/FONT]

---

### Post by tommcd on 2010-02-03
> **Arachan said:**
> 
 It was working fine until I started reformatting a different drive with XP on it; since then it has had the error.
Were you formatting /dev/sda1? Is that why GParted says /dev/sda1 is unknown?
> **Arachan said:**
> 
As far as I know I need to reconfigure GRUB to boot to the correct partition, but I do not know how to do this.

Was grub on the MBR of the /dev/sda? If so, then the MBR may have been erased  if you tried formatting /dev/sda1.
For Ubuntu 9.10 (which uses grub2) you can reinstall grub2 from the Ubuntu 9.10 live CD like this:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)
For older versions of Ubuntu (which use grub-legacy) you can reinstall grub from the Ubuntu live CD like this:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)
If you need more help, post back what version of Ubuntu you are running. And whether it was a clean install or an upgrade from a previous version of Ubuntu.
Also post what is going on with /dev/sda1 if you know.

And welcome to the Ubuntu forums!

---

### Post by Arachan on 2010-02-03
The XP I was formatting was on a different HDD, the sda1 partition is just spare (I was going to install XP on it but decided to use another HDD instead). I think when I was running XP then I may have accidentally modified sda1, possibly erasing the MBR.

As far as I know grub was on the MBR of the /dev/sda. I'm using Ubuntu 9.10 and it was a fresh install. I tried using the steps in the first link you posted, and entered the command: 

sudo grub-setup -d /media/ubuntu/boot/grub -m /media/ubuntu/boot/grub/device.map /dev/sda

This however returned:

grub-setup: error: Cannot open `/media/ubuntu/boot/grub/device.map'

The file does exist but maybe the permissions are wrong? 

What can I do now?

Thanks for your help
Arachan.

---

### Post by presence1960 on 2010-02-03
Let's not speculate as to what you have. We need to see what is on your machine. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page and all credit is his.

---

### Post by Arachan on 2010-02-03
Okay, thanks. I downloaded and ran the program and here are the results.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd640d640

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    19,535,039    19,534,977   b W95 FAT32
/dev/sda2    *     19,535,040    39,070,079    19,535,040  83 Linux
/dev/sda3          39,070,080    42,973,874     3,903,795  82 Linux swap / Solaris
/dev/sda4          42,973,875   976,768,064   933,794,190  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        18DF-666A                              vfat                                     
/dev/sda2        023578f6-5766-42e5-af67-ab995737e5aa   ext4       UBUNTU                        
/dev/sda3        bec75a0d-5d80-4fa3-b195-9f3a267ea284   swap                                     
/dev/sda4        08605420-3111-4828-9d89-88c68f87954e   ext3       DATA                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
timeout        5

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
# kopt=root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro

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
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Chainload into GRUB 2
root        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=023578f6-5766-42e5-af67-ab995737e5aa /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda4 during installation
UUID=2AA3-6D4B  /data           vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda3 during installation
UUID=bec75a0d-5d80-4fa3-b195-9f3a267ea284 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  10.0GB: boot/grub/core.img
  10.0GB: boot/grub/grub.cfg
  10.0GB: boot/grub/menu.lst
  10.0GB: boot/initrd.img-2.6.31-14-generic
  10.0GB: boot/initrd.img-2.6.31-16-generic
  10.0GB: boot/initrd.img-2.6.31-17-generic
  10.0GB: boot/vmlinuz-2.6.31-14-generic
  10.0GB: boot/vmlinuz-2.6.31-16-generic
  10.0GB: boot/vmlinuz-2.6.31-17-generic
  10.0GB: initrd.img
  10.0GB: initrd.img.old
  10.0GB: vmlinuz
  10.0GB: vmlinuz.old
```It seems to think that Windows is installed on the first partition, which was supposed to just free free space. Is this because something that XP did?

Thanks,
Arachan.

---

### Post by presence1960 on 2010-02-03
> **Arachan said:**
> Okay, thanks. I downloaded and ran the program and here are the results.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd640d640

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    19,535,039    19,534,977   b W95 FAT32
/dev/sda2    *     19,535,040    39,070,079    19,535,040  83 Linux
/dev/sda3          39,070,080    42,973,874     3,903,795  82 Linux swap / Solaris
/dev/sda4          42,973,875   976,768,064   933,794,190  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        18DF-666A                              vfat                                     
/dev/sda2        023578f6-5766-42e5-af67-ab995737e5aa   ext4       UBUNTU                        
/dev/sda3        bec75a0d-5d80-4fa3-b195-9f3a267ea284   swap                                     
/dev/sda4        08605420-3111-4828-9d89-88c68f87954e   ext3       DATA                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
timeout        5

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
# kopt=root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro

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
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Chainload into GRUB 2
root        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=023578f6-5766-42e5-af67-ab995737e5aa /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda4 during installation
UUID=2AA3-6D4B  /data           vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda3 during installation
UUID=bec75a0d-5d80-4fa3-b195-9f3a267ea284 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  10.0GB: boot/grub/core.img
  10.0GB: boot/grub/grub.cfg
  10.0GB: boot/grub/menu.lst
  10.0GB: boot/initrd.img-2.6.31-14-generic
  10.0GB: boot/initrd.img-2.6.31-16-generic
  10.0GB: boot/initrd.img-2.6.31-17-generic
  10.0GB: boot/vmlinuz-2.6.31-14-generic
  10.0GB: boot/vmlinuz-2.6.31-16-generic
  10.0GB: boot/vmlinuz-2.6.31-17-generic
  10.0GB: initrd.img
  10.0GB: initrd.img.old
  10.0GB: vmlinuz
  10.0GB: vmlinuz.old
```It seems to think that Windows is installed on the first partition, which was supposed to just free free space. Is this because something that XP did?

Thanks,
Arachan.

You need to restore GRUB to MBR of that disk. Boot the ubuntu Live CD (version 9.04) and choose "try ubuntu without any changes." When the desktop loads do this from terminal (Applications > Accessories > Terminal) These directions are for GRUB 0.97:


1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
3. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
4. Type "setup (hd0)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

P.S. Don't type the parenthesis  in commands such as "root (hd0,1)", instead type root (hd0,1)

Edit: Just noticed that you have GRUB 0.97 and GRUB2 files on your ubuntu partition. To install GRUB2 boot the 9.10 Live CD , choose 'try ubuntu without any changes." When the desktop loads open a terminal and run ```
sudo mount /dev/sda2 /mnt
```This will mount your ubuntu partition. Then run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sda
``` This will put GRUB2 on MBR of your hard disk

---

### Post by Arachan on 2010-02-04
The only liveCD I have is 9.10, will that still work?

I tried to run

```
sudo grub
```but I just get 

```
sudo: grub: command not found
```if I try 

```
grub
```I get 

```
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
grub: command not found
```Does this mean something has happened to my grub on sda2? How can I repair it?

Okay, I just saw your edit. I tried the commands, the mount worked but the second command just returned 

```
sudo: grub-install: command not found
```

I take it this also means something is wrong with my grub?

Thanks,
Arachan.

---

### Post by presence1960 on 2010-02-04
Follow my instructions at the bottom of my post after Edit: for installing GRUB2.

---

### Post by Arachan on 2010-02-04
Yes, I tried that, it returned 

```
sudo: grub-install: command not found
```

Is this what you meant?

Thanks,
Arachan.

---

### Post by presence1960 on 2010-02-04
> **Arachan said:**
> Yes, I tried that, it returned 

```
sudo: grub-install: command not found
```

Is this what you meant?

Thanks,
Arachan.

No that is not what I meant. Nowhere in my instructions did I say to run sudo grub-install as you tried to do it. here it is again, do this:

1. Boot the 9.10 Live CD and choose "try ubuntu without any changes" from the menu.

2. When the desktop loads open a terminal and run ```
sudo mount /dev/sda2 /mnt
```

3. From terminal again run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot & you should be good to go.

Follow those commands **_EXACTLY- do not remove or add anything to the commands._**

Edit: are you sure that is a 9.10 Live CD? 9.04 and earlier do not support the GRUB2 commands. Only 9.10 and the Lucid alpha Live CDs support GRUB2. If you are getting a grub-install command not found you are either using the wrong version Live CD or you have a faulty CD.
Since you have both boot files for GRUB Legacy 0.97 and GRUB2 either method I posted will work provided you use the proper version of the Live CD. For GRUB2 it must be a 9.10 Live CD and for legacy GRUB 0.97 it must be a 9.04 or earlier live CD.

---

### Post by Arachan on 2010-02-04
Okay. I ran 

```
sudo mount /dev/sda2 /mnt
```That worked fine. I then ran 

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```Which returned 

```
error: no mapping exists for `hd1'
error: no mapping exists for `hd1'
grub-probe: error: Cannot find a GRUB drive for /dev/sda2.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

What should be in device.map?

I downloaded and burnt to CD the 9.10 image around a month ago. It is definitely 9.10. 

Thanks for your help,
Arachan.

---

### Post by presence1960 on 2010-02-04
> **Arachan said:**
> Okay. I ran 

```
sudo mount /dev/sda2 /mnt
```That worked fine. I then ran 

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```Which returned 

```
error: no mapping exists for `hd1'
error: no mapping exists for `hd1'
grub-probe: error: Cannot find a GRUB drive for /dev/sda2.  Check your device.map.[CODE]

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

What should be in device.map?

I downloaded and burnt to CD the 9.10 image around a month ago. It is definitely 9.10. 

Thanks for your help,
Arachan.

I have 3 hard disks. here is my device map file contents:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

I noticed you said you had another disk with XP on it, yet it didn't show up in your boot info script results- where is it now? because the error is commplaining about hd1. If the disk is still in your machine add the entry for hd1 to the device map. if the disk is no longer in your machine remove the entry for hd1 in device map

---

### Post by Arachan on 2010-02-04
Okay. I now have the 160GB HDD with XP on it also connected. My RESULTS.txt now reads: 

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

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
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd640d640

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    19,535,039    19,534,977   c W95 FAT32 (LBA)
/dev/sda2    *     19,535,040    39,070,079    19,535,040  83 Linux
/dev/sda3          39,070,080    42,973,874     3,903,795  82 Linux swap / Solaris
/dev/sda4          42,973,875   976,768,064   933,794,190  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa2d4a2d4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    20,482,874    20,482,812   7 HPFS/NTFS
/dev/sdb2          20,482,875   165,871,124   145,388,250   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        18DF-666A                              vfat                                     
/dev/sda2        023578f6-5766-42e5-af67-ab995737e5aa   ext4       UBUNTU                        
/dev/sda3        bec75a0d-5d80-4fa3-b195-9f3a267ea284   swap                                     
/dev/sda4        08605420-3111-4828-9d89-88c68f87954e   ext3       DATA                          
/dev/sdb1        F23848D938489F0B                       ntfs       XP                            
/dev/sdb2        75A3533E397335AA                       ntfs       GAMES                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda2        /mnt                     ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
timeout        5

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
# kopt=root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro

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
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Chainload into GRUB 2
root        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=023578f6-5766-42e5-af67-ab995737e5aa /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda4 during installation
UUID=2AA3-6D4B  /data           vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda3 during installation
UUID=bec75a0d-5d80-4fa3-b195-9f3a267ea284 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  10.0GB: boot/grub/grub.cfg
  10.0GB: boot/grub/menu.lst
  10.0GB: boot/initrd.img-2.6.31-14-generic
  10.0GB: boot/initrd.img-2.6.31-16-generic
  10.0GB: boot/initrd.img-2.6.31-17-generic
  10.0GB: boot/vmlinuz-2.6.31-14-generic
  10.0GB: boot/vmlinuz-2.6.31-16-generic
  10.0GB: boot/vmlinuz-2.6.31-17-generic
  10.0GB: initrd.img
  10.0GB: initrd.img.old
  10.0GB: vmlinuz
  10.0GB: vmlinuz.old
```My device.map reads:

```
(hd0) /
(hd1) /XP
```If I try to run:

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```Then I get the error:

```
grub-probe: error: Cannot find a GRUB drive for /dev/sda2.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```I really appreciate your help, 
Arachan.

---

### Post by presence1960 on 2010-02-04
> **Arachan said:**
> Okay. I now have the 160GB HDD with XP on it also connected. My RESULTS.txt now reads: 

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

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
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd640d640

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    19,535,039    19,534,977   c W95 FAT32 (LBA)
/dev/sda2    *     19,535,040    39,070,079    19,535,040  83 Linux
/dev/sda3          39,070,080    42,973,874     3,903,795  82 Linux swap / Solaris
/dev/sda4          42,973,875   976,768,064   933,794,190  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa2d4a2d4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    20,482,874    20,482,812   7 HPFS/NTFS
/dev/sdb2          20,482,875   165,871,124   145,388,250   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        18DF-666A                              vfat                                     
/dev/sda2        023578f6-5766-42e5-af67-ab995737e5aa   ext4       UBUNTU                        
/dev/sda3        bec75a0d-5d80-4fa3-b195-9f3a267ea284   swap                                     
/dev/sda4        08605420-3111-4828-9d89-88c68f87954e   ext3       DATA                          
/dev/sdb1        F23848D938489F0B                       ntfs       XP                            
/dev/sdb2        75A3533E397335AA                       ntfs       GAMES                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda2        /mnt                     ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
timeout        5

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
# kopt=root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro

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
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Chainload into GRUB 2
root        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        023578f6-5766-42e5-af67-ab995737e5aa
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 023578f6-5766-42e5-af67-ab995737e5aa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=023578f6-5766-42e5-af67-ab995737e5aa ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=023578f6-5766-42e5-af67-ab995737e5aa /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda4 during installation
UUID=2AA3-6D4B  /data           vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda3 during installation
UUID=bec75a0d-5d80-4fa3-b195-9f3a267ea284 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  10.0GB: boot/grub/grub.cfg
  10.0GB: boot/grub/menu.lst
  10.0GB: boot/initrd.img-2.6.31-14-generic
  10.0GB: boot/initrd.img-2.6.31-16-generic
  10.0GB: boot/initrd.img-2.6.31-17-generic
  10.0GB: boot/vmlinuz-2.6.31-14-generic
  10.0GB: boot/vmlinuz-2.6.31-16-generic
  10.0GB: boot/vmlinuz-2.6.31-17-generic
  10.0GB: initrd.img
  10.0GB: initrd.img.old
  10.0GB: vmlinuz
  10.0GB: vmlinuz.old
```My device.map reads:

```
(hd0) /
(hd1) /XP
```If I try to run:

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```Then I get the error:

```
grub-probe: error: Cannot find a GRUB drive for /dev/sda2.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```I really appreciate your help, 
Arachan.

You need to edit your device map. Boot from the Live CD again. From Places > Computer mount your ubuntu partition by highlighting it on left pane. When mounted you will see directories on right side. Now open a terminal and run ```
gksu nautilus
```This will open a root file browser. Highlight the Ubuntu partition on left pane and navigate to boot/grub/device.map

Open the device.map file and change the contents to this:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

Click Save at top toolbar and close file & then both file browsers. Now open a terminal and reinstall GRUB2.

---

### Post by Arachan on 2010-02-04
Thanks a lot. I'm now booted to my original 'UBUNTU' partition. 

I noticed that when I booted the grub said version 0.97. Is this a bad thing? 

Also, if I now want to reinstall XP on hd1 how do I go about this?

Thanks so much,
Arachan.

---

### Post by tommcd on 2010-02-05
> **Arachan said:**
> 
I noticed that when I booted the grub said version 0.97. Is this a bad thing? 
If you did a clean install of Ubuntu 9.10, how do you have files for grub legacy and grub 2 in your boot directory? Are you sure you did not do a dist-upgrade from Ubuntu 9.04?
> **Arachan said:**
> 
Also, if I now want to reinstall XP on hd1 how do I go about this?

In order to avoid having to go through this all over again, you could disconnect /dev/sda and install XP on the second hard drive (/dev/sdb). This will avoid any chance of XP overwriting the MBR of /dev/sda. Then reconnect /dev/sda as the first hard drive as it was before. Then boot up Ubuntu and run:
 ```
sudo update-grub
```
from the terminal. This should have grub2 pick up the XP on /dev/sdb and add it to your /boot/grub/grub.cfg.

---

### Post by milky264 on 2010-08-29
hello,

I'm having a similar problem, but am much less proficient at anything linux.  My problem:

I was running lucid.  I tried making my boot splash look better, but when i reboot, I got error 15.  The forums told me to do a new install of grub2 using the grub-install command that you recommended as well.  I experienced no errors but, after that, grub does not load at all and i get the message

'Error Loading OS'

I downloaded your script and am attaching it to this post.  I am currently running from a Live USB on the Netbook Remix, 10.04.  I have several additional harddrives, 2 versions of Ubuntu running and an install of Win XP.  I assume all that will be clear when you read the file.

Thanks for anything.

p.s.  i don't know how to embed the text, so I attached the file instead...

---

