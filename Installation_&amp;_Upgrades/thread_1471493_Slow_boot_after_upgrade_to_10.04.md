---
title: "Slow boot after upgrade to 10.04"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Yhanthlei on 2010-05-03
Hey everyone!
I just recently upgraded my kubuntu install from karmic to lucid and now it takes about 10-15 minutes to boot. Directly after the upgrade it was pretty slow already, but it got worse every day from then. The karmic version was a wubi install I moved to a dedicated partition using lvpm. Here are the results from the bootinfoscript (if that helps)
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/home.disk /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30942895 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spur, 19457 Zylinder, zusammen 312581808 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   150,175,619   150,175,557   c W95 FAT32 (LBA)
/dev/sda2         150,175,620   281,638,911   131,463,292   f W95 Ext d (LBA)
/dev/sda5         217,925,632   281,638,911    63,713,280   7 HPFS/NTFS
/dev/sda6         150,175,746   154,368,584     4,192,839  82 Linux swap / Solaris
/dev/sda7         154,368,648   217,921,724    63,553,077  83 Linux
/dev/sda3         281,638,912   312,581,807    30,942,896  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       0807a690-3667-4184-9264-efade530c55c   ext4                                     
/dev/sda1        4112-15E3                              vfat                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        0C6CE3A76CE38A32                       ntfs                                     
/dev/sda5        E602B8F502B8CC35                       ntfs       LENOVO                        
/dev/sda6        89e029b4-adbc-42e0-818a-61b7f94e8a8f   swap       swap                          
/dev/sda7        2c21aa79-0d83-4c2c-97ae-d7a8f4b18e63   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Kubuntu"

======================== sda1/Wubi/boot/grub/menu.lst: ========================



title Ubuntu-on-/dev/sda7
root (hd0,6)
configfile /boot/grub/menu.lst



======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4112-15e3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4112-15e3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4112-15e3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4112-15e3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4112-15e3
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 0c6ce3a76ce38a32
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/home.disk /home           ext4    loop            0       2
/host/ubuntu/disks/usr.disk /usr            ext4    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


    .4GB: boot/grub/grub.cfg
    .1GB: boot/grub/menu.lst
    .3GB: boot/initrd.img-2.6.31-14-generic
   1.7GB: boot/initrd.img-2.6.31-20-generic
    .4GB: boot/vmlinuz-2.6.31-14-generic
    .4GB: boot/vmlinuz-2.6.31-20-generic
   1.7GB: initrd.img
    .3GB: initrd.img.old
    .4GB: vmlinuz
    .4GB: vmlinuz.old

=========================== sda7/boot/grub/menu.lst: ===========================


# This is a divider, added to separate the menu items below from the Debian
# ones.

splashimage=(hd0,6)/boot/grub/splashimages/105103-dark-air.xpm.gz
foreground = 0092b1
background = 000000

title		Other operating systems:
root

title Kubuntu
root (hd0,6)
kernel /boot/vmlinuz-2.6.32-21-generic root=/dev/sda7 splash
initrd /boot/initrd.img-2.6.32-21-generic
boot


title Microsoft Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1
boot
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
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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


=========================== sda7/boot/grub/grub.cfg: ===========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4112-15e3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4112-15e3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4112-15e3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4112-15e3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 4112-15e3
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 0c6ce3a76ce38a32
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
menuentry "Kubuntu" {
        insmod ext2
        set root=(hd0,7)
        search --no-floppy --fs-uuid --set 4112-15e3
       
        linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda7   quiet splash
        initrd /boot/initrd.img-2.6.31-20-generic
}


=============================== sda7/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda7
UUID=     /               ext3        defaults,errors=remount-ro    0   1

=================== sda7: Location of files loaded by Grub: ===================


  97.2GB: boot/grub/grub.cfg
  97.1GB: boot/grub/menu.lst
  97.2GB: boot/grub/stage2
  98.3GB: boot/initrd.img-2.6.31-20-generic
  98.3GB: boot/initrd.img-2.6.32-21-generic
  97.2GB: boot/vmlinuz-2.6.31-20-generic
  97.2GB: boot/vmlinuz-2.6.32-21-generic
  98.3GB: initrd.img
  98.3GB: initrd.img.old
  97.2GB: vmlinuz
  97.2GB: vmlinuz.old

```
Any ideas?
Thanks in advance!

---

### Post by wieman01 on 2010-05-03
To be honest, I went through the same process and the upgrade did not work out for me. Similar issues. I would recommend a fresh install, it will save you a lot of time. Just make a backup of your /home folder and reinstall.

---

### Post by Yhanthlei on 2010-05-03
Actually that was what I thought as well, unfortunately I'm running a netbook without an optical drive, so I could only install from USB (tried once, didn't work for me...) or create a new wubi install and transfer that again... I don't really like either xD
Is there any way to install lucid from an existing, running system (I still have my wubi install)? should not be different from installing from a liveCD technically, as I don't need to repartition anything, or am I missing something?

---

### Post by wieman01 on 2010-05-03
Have you tried to change the boot priorities in the BIOS? Ubuntu has a nice tool called USB Creator. It should help you created a bootable USB-drive with Ubuntu on it. I don't have a CD-drive either and that's how I installed Kubuntu 10.04.

---

### Post by Yhanthlei on 2010-05-03
> **wieman01 said:**
> Have you tried to change the boot priorities in the BIOS? Ubuntu has a nice tool called USB Creator. It should help you created a bootable USB-drive with Ubuntu on it. I don't have a CD-drive either and that's how I installed Kubuntu 10.04.

The problem wasn't the actual booting, but creating the bootable USB-drive (can't remember what exactly went wrong, quite some time ago...)

Well, I'll try that then, thanks!

---

### Post by wieman01 on 2010-05-03
Then install USB Creator. Very easy to use, you will figure it out. :-) If not, you know where to find me.

---

### Post by Yhanthlei on 2010-05-04
So I just used a USB-stick to make a fresh install, and guess what: same problem. Can't boot at all using the grub menuentry automatically created (can't find root filesystem), when booted manually (setting linux /boot/vmlinuz*** root=/dev/sda7)
it takes about ~15 minutes again. The time until kjournald starts varies greatly (between 20 an 70 secs), and it seemingly hangs after
Running /scripts/init-bottom...
done
, but boots correctly after said 10-15 minutes...
So, any other ideas? :(

---

### Post by netmonky on 2010-05-06
Hi Guys, 

I also have this probem :-(. I have wubi installed with ubuntu 10.04 - can anyone help ?

---

### Post by skeptikone on 2010-05-29
hey guys, i have this same problem! are your netbooks nb300/nb305's ? its quite annoying waiting 15 mins for boot! it simply takes that long just to get to any sort of booting. i dont even see the grub intro!

just a flashing "_" cursor.

---

### Post by kansasnoob on 2010-05-29
> **skeptikone said:**
> hey guys, i have this same problem! are your netbooks nb300/nb305's ? its quite annoying waiting 15 mins for boot! it simply takes that long just to get to any sort of booting. i dont even see the grub intro!

just a flashing "_" cursor.

Is your install Kubuntu, or Ubuntu, or UNR?

I'm curious if a bug search would reveal anything :confused:

Do you see your hardware here:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by Scot_Bernard on 2010-07-07
> **skeptikone said:**
> hey guys, i have this same problem! are your netbooks nb300/nb305's ? its quite annoying waiting 15 mins for boot! it simply takes that long just to get to any sort of booting. i dont even see the grub intro!

just a flashing "_" cursor.
I'm using a BenQ Joybook U105 and having exaclty the same problem with a fresh install from USB of the Ubuntu Netbook Remix 10.04 with all update to date installed.

The first thing I made was changing a line in /etc/default/grub from:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to:
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

then had ran: sudo update-grub

and now I see console text while booting, but the delay of about 4 minutes for completing the boot process remains happening.

I noted that this delays is produced afer the line on the screen:
```
init-bootom
Done
```

So i came to this thread and installed the bootchart utility from software center willing to where this delay is produced.

The surprise was that after bootchart were installed and I reboot the netbook the boot time were reduced from 4 minutes to 40 seconds and the problem itself were solved, I don't know why.

I hope you get the same luck.

---

