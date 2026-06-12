---
title: "Can't change default OS in Grub"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by jbelt on 2010-02-07
Hi,

I recently installed Karmic, and want to change the default Grub entry to Windows XP. Having done some research and tried things out, I am a bit confused. I have edited etc/default/grub so that it has GRUB_DEFAULT=6 (to correspond to my XP installation) and GRUB_TIMEOUT="3", but after running sudo grub-mkconfig the grub.cfg file still says set default="0".

Can someone please tell me where I'm going wrong?

Cheers

James

---

### Post by mushwars on 2010-02-07
you need to run sudo update-grub to keep the change perminate.


If you want the menu to appear when the timeout is zero just hold down the "shift" key when the computer is booting.

---

### Post by jbelt on 2010-02-07
Thanks Mushwars, I ran sudo update-grub but grub.cfg still hasn't changed. Here is the output I got in the terminal when I ran update-grub:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.31-19-generic
Found kernel: /vmlinuz-2.6.31-17-generic
Found kernel: /vmlinuz-2.6.31-16-generic
Found kernel: /vmlinuz-2.6.31-15-generic
Found kernel: /vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Does this help at all?

---

### Post by darkod on 2010-02-07
> **jbelt said:**
> Thanks Mushwars, I ran sudo update-grub but grub.cfg still hasn't changed. Here is the output I got in the terminal when I ran update-grub:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.31-19-generic
Found kernel: /vmlinuz-2.6.31-17-generic
Found kernel: /vmlinuz-2.6.31-16-generic
Found kernel: /vmlinuz-2.6.31-15-generic
Found kernel: /vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Does this help at all?

Was this an upgrade from 9.04? Why do you have /boot/grub/menu.lst which is used in grub1? Karmic comes with grub2 which uses /boot/grub/grub.cfg.
This might be the issue, if it's using menu.lst because it usually needs to be modified by hand. Your XP doesn't seen to be detected at all, it's not in the list here.
To make sure what your boot situation is, you can download the script in my signature, move it on desktop for example, and run it with:

sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with info about your boot process. Copy the content here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above).

---

### Post by jbelt on 2010-02-07
Cheers Darko- here's what came out from the script:
```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002efe0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    42,427,664    42,427,602   7 HPFS/NTFS
/dev/sda2          42,427,665    48,725,144     6,297,480  83 Linux
/dev/sda3          48,725,145   312,303,599   263,578,455   f W95 Ext d (LBA)
/dev/sda5          48,725,208   226,468,304   177,743,097   7 HPFS/NTFS
/dev/sda6         226,468,368   233,810,009     7,341,642   7 HPFS/NTFS
/dev/sda7         233,810,073   265,265,279    31,455,207   7 HPFS/NTFS
/dev/sda8         265,265,343   300,913,514    35,648,172  83 Linux
/dev/sda9         300,913,578   309,299,444     8,385,867   7 HPFS/NTFS
/dev/sda10        309,299,508   312,303,599     3,004,092  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       eb4b780e-39f4-4332-8f54-7d71f3e836d4   swap                                     
/dev/sda1        9E142F91142F6B89                       ntfs                                     
/dev/sda2        ee34f96c-4491-44a6-8124-b52736fc9c32   ext3                                     
/dev/sda5        B01C8A601C8A2208                       ntfs       Data                          
/dev/sda6        56CC364DCC36279F                       ntfs       Pagefile                      
/dev/sda7        C00CA5540CA545EE                       ntfs       Image                         
/dev/sda8        8f4fed08-333c-435b-ba84-15d7262604c3   ext4                                     
/dev/sda9        64350F5D27D84443                       ntfs       Games                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /boot                    ext3       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

============================= sda2/grub/menu.lst: =============================

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
default        6

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
# kopt=root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ee34f96c-4491-44a6-8124-b52736fc9c32

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

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /vmlinuz-2.6.31-19-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro quiet splash 
initrd        /initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /vmlinuz-2.6.31-19-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro  single
initrd        /initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /vmlinuz-2.6.31-17-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro quiet splash 
initrd        /initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /vmlinuz-2.6.31-17-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro  single
initrd        /initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /vmlinuz-2.6.31-16-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro quiet splash 
initrd        /initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /vmlinuz-2.6.31-16-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro  single
initrd        /initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /vmlinuz-2.6.31-15-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro quiet splash 
initrd        /initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /vmlinuz-2.6.31-15-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro  single
initrd        /initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /vmlinuz-2.6.31-14-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro quiet splash 
initrd        /initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /vmlinuz-2.6.31-14-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro  single
initrd        /initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        ee34f96c-4491-44a6-8124-b52736fc9c32
kernel        /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

============================= sda2/grub/grub.cfg: =============================

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set 8f4fed08-333c-435b-ba84-15d7262604c3
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
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee34f96c-4491-44a6-8124-b52736fc9c32
    linux    /vmlinuz-2.6.31-15-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro   quiet splash
    initrd    /initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee34f96c-4491-44a6-8124-b52736fc9c32
    linux    /vmlinuz-2.6.31-15-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro single 
    initrd    /initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee34f96c-4491-44a6-8124-b52736fc9c32
    linux    /vmlinuz-2.6.31-14-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro   quiet splash
    initrd    /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee34f96c-4491-44a6-8124-b52736fc9c32
    linux    /vmlinuz-2.6.31-14-generic root=UUID=8f4fed08-333c-435b-ba84-15d7262604c3 ro single 
    initrd    /initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 9e142f91142f6b89
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda2: Location of files loaded by Grub: ===================


  21.7GB: grub/core.img
  21.7GB: grub/grub.cfg
  21.7GB: grub/menu.lst
  21.7GB: initrd.img-2.6.31-14-generic
  21.7GB: initrd.img-2.6.31-15-generic
  21.7GB: initrd.img-2.6.31-16-generic
  21.7GB: initrd.img-2.6.31-17-generic
  21.7GB: initrd.img-2.6.31-19-generic
  21.7GB: vmlinuz-2.6.31-14-generic
  21.7GB: vmlinuz-2.6.31-15-generic
  21.7GB: vmlinuz-2.6.31-16-generic
  21.7GB: vmlinuz-2.6.31-17-generic
  21.7GB: vmlinuz-2.6.31-19-generic

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=8f4fed08-333c-435b-ba84-15d7262604c3 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=ee34f96c-4491-44a6-8124-b52736fc9c32 /boot           ext3    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=eb4b780e-39f4-4332-8f54-7d71f3e836d4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```It's a clean install of Karmic.

---

### Post by darkod on 2010-02-07
OK, you have:
/ on /dev/sda8
/boot on /dev/sda2   (separate partition)
swap on /dev/sda10

Looks fine. Go into /boot/grub and move menu.lst to your home folder for example (don't delete it yet, so you can put it back if the boot fails, you can use the live desktop and put it back from home to /boot/grub).

After you move menu.lst, you should still have grub.cfg there which should be the main file for grub2. Then in terminal run:

sudo update-grub

See which OSs it finds, which ones it will list (it should also report XP). Reboot and see how it goes.
We will deal with the default OS later, first see if it will work without menu.lst.

---

### Post by jbelt on 2010-02-07
I moved menu.lst, then ran sudo update-grub. Here is the response:

```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N)
```

Would this suggest that I'm using Grub 1? It says version 1.97 on the boot screen.

---

### Post by darkod on 2010-02-07
You are definitely using grub2, 1.97 is grub2. And the script shows it too.
I have no explanation why it wants menu.lst to be there. Put it back for the time being. Maybe someone else that knows more will jump in.

I double checked you menu.lst and you don't even have an entry for XP there. You should open it for editing with:
sudo gedit /boot/grub/menu.lst

and at the end add something like:

title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

If I counted correctly, that would be entry number 13 in menu.lst. You need to count all of them including the recovery mode titles. Which means if you want XP to be default you need to use:

default 12

in menu.lst toward to top of the file (you will find the line there).

Then do the update-grub again, reboot and see how it goes.

---

### Post by kansasnoob on 2010-02-07
Having mixed grub2 and legacy grub files makes a mess of things. I'll also bet if you run:

```
grub-install -v
```

It shows 0.97, but regardless I'd:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub grub-common
```

```
sudo apt-get install --reinstall grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

Then see how things go.

---

### Post by jbelt on 2010-02-07
Thanks, Kansasnoob, that seems to have done the trick. I followed what you said and changed the default in /etc/default/grub to 12, and that entry is now coming up as the default in the menu. Thanks also to Darko- it's been a good learning experience. Good to do business with you both.

James

---

