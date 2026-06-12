---
title: "GRUB not loading after update"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by Agent.Logic_ on 2010-09-11
Hi guys,

I did an update from the Update Manager, which included the new Linux kernel 2.6.32-25. I am also running a GRUB 1.98-x with custom menu to display custom names for the list of operating systems. I am on a dual boot Windows  Vista and Ubuntu 10.04. After the update I did yesterday and rebooted my laptop, instead of the GRUB menu displaying, it displayed a "Windows is loading files...." message, after which the Vista boot progress bar appeared. A few moments later, a "Please wait a moment..." message appeared and the system rebooted automatically. My laptop is stuck in this infinite loop and I am unable to make the GRUB menu appear. I tried reinstalling GRUB, double-checked the GRUB config files, and all seems well. Can someone shed light on what is happening and how I could fix this?

Thanks in advance.

---

### Post by Rubi1200 on 2010-09-11
Hi,
from the LiveCD, post the results of the bootscript linked to at the bottom of my post.

Thanks.

---

### Post by Agent.Logic_ on 2010-09-11
Hi Rubi1200,

Thanks for your reply. Below is the generated RESULTS.txt file. You can ignore info about the sdb partition, it's the LiveUSB.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

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
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  27 Hidden HPFS/NTFS
/dev/sda2    *     20,482,048   100,482,047    80,000,000   7 HPFS/NTFS
/dev/sda3        100,486,575   150,480,854    49,994,280  83 Linux
/dev/sda4         150,480,855   625,137,344   474,656,490   5 Extended
/dev/sda5         150,480,918   620,141,129   469,660,212  83 Linux
/dev/sda6         620,141,193   625,137,344     4,996,152  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2030 MB, 2030043136 bytes
63 heads, 62 sectors/track, 1015 cylinders, total 3964928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,964,589     3,964,528   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       31f25375-8e6f-4799-9ed7-7d7dd921bf44   ext3                                     
/dev/sda1        EAEE-EB49                              vfat       PQSERVICE                     
/dev/sda2        1A2609E12609BF2F                       ntfs       ACER                          
/dev/sda3        6aa4c402-ef42-48af-abd5-8b966d7f67b1   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        04e6ecbf-b956-4aa6-add9-b53ea08a7271   xfs                                      
/dev/sda6        560345be-81a2-4020-b257-425bca6bc27f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        87D1-32DD                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set default="14"
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
insmod tga
if background_image /usr/share/images/grub/linux-vs-vista.tga ; then
  set color_normal=white/black
  set color_highlight=light-blue/white
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1366x768
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set eaee-eb49
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 1a2609e12609bf2f
	drivemap -s (hd0) ${root}
	chainloader +1
}
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Custom Menu"{
   set root='(hd0,3)'
   search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
   configfile /boot/grub/custom_menu.cfg
}
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=04e6ecbf-b956-4aa6-add9-b53ea08a7271 /home           xfs     defaults        0       2
# swap was on /dev/sda6 during installation
UUID=560345be-81a2-4020-b257-425bca6bc27f none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  51.5GB: boot/grub/core.img
  60.5GB: boot/grub/grub.cfg
  52.5GB: boot/initrd.img-2.6.31-14-generic
  52.8GB: boot/initrd.img-2.6.32-21-generic
  59.4GB: boot/initrd.img-2.6.32-22-generic
  59.3GB: boot/initrd.img-2.6.32-23-generic
  61.3GB: boot/initrd.img-2.6.32-24-generic
  53.4GB: boot/initrd.img-2.6.32-25-generic
  52.1GB: boot/vmlinuz-2.6.31-14-generic
  52.2GB: boot/vmlinuz-2.6.32-21-generic
  58.9GB: boot/vmlinuz-2.6.32-22-generic
  58.6GB: boot/vmlinuz-2.6.32-23-generic
  53.2GB: boot/vmlinuz-2.6.32-24-generic
  57.8GB: boot/vmlinuz-2.6.32-25-generic
  53.4GB: initrd.img
  61.3GB: initrd.img.old
  57.8GB: vmlinuz
  53.2GB: vmlinuz.old
```

---

### Post by Rubi1200 on 2010-09-11
I assume you tried using "Shift" as the computer was booting to get the GRUB menu to come up?

Can you boot into Windows at all or are also stuck there?

What graphics card do you have installed on the laptop?

---

### Post by Agent.Logic_ on 2010-09-11
I had completely forgotten about pressing and holding shift. I tried that after you mentioned it, and the normal grub menu shows up. I am able to boot into Windows Vista and Ubuntu 10.04 without any issues. The problem persists when I try to boot without holding the shift key. I am also able to select my "custom menu" from the GRUB default menu (holding shift key), and then boot into the installed operating systems. That rules out any errors in the custom GRUB .cfg file... it simply refuses to show up and instead it looks like Windows tries to recover itself (?).

My laptop has a ATi Radeon 4570HD graphics card, but I don't have any issues with the graphics driver.

---

### Post by Rubi1200 on 2010-09-11
Can you please post the output from your /etc/default/grub file and the custom file just so we can check it anyway?

Thanks.

---

### Post by Agent.Logic_ on 2010-09-11
Thanks for your patience and time, Rubi1200!

Before I post the /etc/default/grub and the custom menu entries, let me say that all was working well right before the update. With that said, here are the two entries:

**Custom GRUB menu**
```
set default = "Ubuntu, Lucid Lynx"
set timeout = 10

menuentry "Ubuntu, Lucid Lynx" --class ubuntu --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
    linux /vmlinuz root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro quiet splash
    initrd /initrd.img
}

menuentry "Ubuntu, Lucid Lynx (Recovery)" --class ubuntu --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
    linux /vmlinuz root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro single 
    echo 'Loading initial ramdisk ...'
    initrd /initrd.img
}

menuentry "Ubuntu, Lucid Lynx (Linux 2.6.32-24)" --class ubuntu --class gnu-linux --class gnu --class os
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
    linux /vmlinuz.old root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro quiet splash
    initrd /initrd.img.old
}

menuentry "Ubuntu, Lucid Lynx (Linux 2.6.32-24) (Recovery)" --class ubuntu --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 6aa4c402-ef42-48af-abd5-8b966d7f67b1
    echo 'Loading Linux 2.6.32-24-generic ...'
    linux /vmlinuz.old root=UUID=6aa4c402-ef42-48af-abd5-8b966d7f67b1 ro single 
    echo 'Loading initial ramdisk ...'
    initrd /initrd.img.old
}

menuentry "Windows Vista Home Premium" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1a2609e12609bf2f
    drivemap -s (hd0) ${root}
    chainloader +1
}
```

And here's **/etc/default/grub**

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=14
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="splash quiet vga=795"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1366x768
GRUB_GFXPAYLOAD_LINUX=1366x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

---

### Post by Rubi1200 on 2010-09-11
Are you willing to try something that can easily be changed again if it does not work?

In the /etc/default/grub file (use sudo gedit to edit) change this:
> GRUB_HIDDEN_TIMEOUT=0 to this 
> #GRUB_HIDDEN_TIMEOUT=0 and change  
> GRUB_TIMEOUT=0 to 
> GRUB_TIMEOUT=5Then, ```
sudo update-grub
``` and reboot to see what happens.

---

### Post by drs305 on 2010-09-11
It looks like you might have mistaken the default OS and timeout entries. Right now it looks to the 14th menuentry and times out at 0 seconds, which is why you never see the menu without shift.

If you don't have 14 entries, it uses the last one present - Windows.

Do as Rubi1200 suggests, but change the GRUB_DEFAULT to the correct menuentry number (5 if you still want Windows as the default), and your problem will be fixed.

---

### Post by Agent.Logic_ on 2010-09-11
@Rubi1200 and drs305:

Thanks for your respective time. I finally figured out why the **GRUB_DEFAULT=14** was present in the entry. My custom menu was the 14th entry in the default GRUB menu, and I wanted it to automatically show up on system power up. After the update I did yesterday, it moved to the 16th position (with the addition of kernel 2.6.32-25 generic and recovery on top), and the 14th position was taken up by Windows Vista recovery partition (hence my problem).

Once again, thank you both for your time!

---

### Post by Rubi1200 on 2010-09-11
You are more than welcome :)

If you feel this issue is resolved, please mark the thread Solved using the Thread Tools near the top of the page.

---

