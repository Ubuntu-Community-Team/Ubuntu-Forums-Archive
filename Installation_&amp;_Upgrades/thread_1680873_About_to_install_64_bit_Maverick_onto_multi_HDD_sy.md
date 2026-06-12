---
title: "About to install 64 bit Maverick onto multi HDD system. Advice please?"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by Glennk on 2011-02-03
I've got two HDDs, One a 320GB that runs XP and Win7 and the other is my new replacement drive 2TB with just a bare Win7 on it, and a 105GB spare partition ready for Ubuntu.

My intent is to move from the old 320GB drive in time to the new 2TB drive with just Win7 and Ubuntu 10.10 64bit. For the moment I just want to correctly install Ubuntu AND maintain my Multiboot menu.

I've attached two screenshots of the partitioning layout. So sda1 hosts my XP OS and sda2 my old Win7 OS. And sdb1 hosts my new Win7 OS and sdb2 is empty ready for Ubuntu 64bit.

Booting from my Live Disc, I am given various choices on where to install Ubuntu to. I will select sdb2.
BUT it asks where I want the GRUB bootloader to be installed to. It proposes sda1. Please can someone advise that this will preserve my current multiboot menu (XP, oldWin7, Win7)? And whether I need to set more options during this install to ensure I can still boot to any OS?

Thanks in advance for your help.

---

### Post by oldos2er on 2011-02-03
Do you have a Win7 boot disk, or recovery disk? 

I would allow grub2 to install to the MBR of sda. It should recognize and create menu entries for your other OSes, but if for some reason it does not, when you reboot into Ubuntu, run *sudo os-prober*

More info on grub2 here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Dual boot: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2011-02-03
Grub may offer partitions but usually complains about installing to partitions. And if you install to the windows partition it breaks windows as windows had part of its boot code in the windows partition boot sector. You want to install to sda. Grub will not let you directly boot each of the windows installs as windows moves essential boot files from a second install to the first one that has the boot flag. The second install is not directly bootable.

I also prefer to set up partitions with small system partitions and large data partitions. If sharing with windows then I use a shared NTFS partition for any data I might want in either system. Ubuntu will show you all the hidden files & folders that windows tries to protect you from and you can accidentally move of delete the wrong file.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Glennk on 2011-02-04
Thanks guys.
 
I'll give that a go. Install Grub to sda1. Use the pre-formatted NTFS 105GB partition with an Ext4 ubuntu / mountpoint around 20GB size. Set a /swap of 4GB (I have 4GB RAM). 
 
Not clear about the /home or 'shared NTFS' bits. I know ubuntu can 'browse' into the NTFS partitions but Writing to them I'm not confident that Win7 will be happy with all it's security descriptors etc...
 
Choices:
1. Do I format the remainder to Ext4 and create /home,
2. Or - I leave the remainder as NTFS that ubuntu can write to and (hopefully Win7 can share R/W data)?
 
Thanks.

---

### Post by oldfred on 2011-02-04
My suggestion is both. If you are going to put most of your data in a shared NTFS partition /home does not have to be large. You will find over time that whatever you do now, it will not be want you want after using the system for awhile.

I started with a shared NTFS partition with my XP and no separate /home. After using Ubuntu for a while I wanted the separate /home, but then started to multi-boot different versions of Ubuntu and wanted to experiment with others so now I have a separate /data for Linux data that windows will not ever need to see. I am in XP so little now, that my NTFS shared partition does not grow, but I still have not moved that data back into my Linux /data partition (yet). Maybe with the next new drive I buy.

---

### Post by Glennk on 2011-02-04
Ok. Will do later.
 
Thanks.

---

### Post by Glennk on 2011-02-04
All done!

Everything preserved. Many thanks for your help.

But in my excitement I've fubar'ed my Netbook boot menu. I had both XP and Win7 partitions. I overwrote the old XP one and left the Win7 one. Booted up. Grub didn't see Win7 at all. Tried reinstalling Grub2, sudo update-grub. All no good. Sudo os-parser does not find Wn7. But I can see the partition on the Disk Utility all fine and dandy.

Your expert help please...

Thanks.

---

### Post by oldfred on 2011-02-04
If XP was you first install, windows then moved the win7 boot files into the XP partition. You need to make sure you have the boot flag on the win7 partition and run win7 repairs.

You can use gparted, right click on partition & manage flags, Disk Utility, or command line:
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda


To see exact configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)
I

---

### Post by Glennk on 2011-02-04
Tried that. Boot flag is set on sda2. Win7 is bootable. And No - Grub does not see it. So here's the boot_info Results.txt for you to interpret:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   104,890,687   104,890,625  83 Linux
/dev/sda2    *    110,752,110   234,436,544   123,684,435   7 HPFS/NTFS
/dev/sda3         104,892,414   110,751,743     5,859,330   5 Extended
/dev/sda5         104,892,416   110,751,743     5,859,328  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   A88E092E8E08F69A                       ntfs                                     
/dev/sda1        54d62f15-ac06-4333-b3cc-82b185939606   ext4       Ubuntu                        
/dev/sda2        01CAAC22FA331E00                       ntfs       Win7                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        fea35e5b-e88e-4b6c-8921-12ebc6ad26c2   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/mmcblk0p1   /media/A88E092E8E08F69A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=54d62f15-ac06-4333-b3cc-82b185939606 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=54d62f15-ac06-4333-b3cc-82b185939606

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

title        Ubuntu 10.10, kernel 2.6.35-25-generic
uuid        54d62f15-ac06-4333-b3cc-82b185939606
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=54d62f15-ac06-4333-b3cc-82b185939606 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic

title        Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid        54d62f15-ac06-4333-b3cc-82b185939606
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=54d62f15-ac06-4333-b3cc-82b185939606 ro  single
initrd        /boot/initrd.img-2.6.35-25-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        54d62f15-ac06-4333-b3cc-82b185939606
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=54d62f15-ac06-4333-b3cc-82b185939606 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        54d62f15-ac06-4333-b3cc-82b185939606
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=54d62f15-ac06-4333-b3cc-82b185939606 ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        54d62f15-ac06-4333-b3cc-82b185939606
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        54d62f15-ac06-4333-b3cc-82b185939606
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 54d62f15-ac06-4333-b3cc-82b185939606
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 54d62f15-ac06-4333-b3cc-82b185939606
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 54d62f15-ac06-4333-b3cc-82b185939606
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=54d62f15-ac06-4333-b3cc-82b185939606 ro  splash vga=771  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 54d62f15-ac06-4333-b3cc-82b185939606
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=54d62f15-ac06-4333-b3cc-82b185939606 ro single  splash vga=771
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 54d62f15-ac06-4333-b3cc-82b185939606
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=54d62f15-ac06-4333-b3cc-82b185939606 ro  splash vga=771  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 54d62f15-ac06-4333-b3cc-82b185939606
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=54d62f15-ac06-4333-b3cc-82b185939606 ro single  splash vga=771
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 54d62f15-ac06-4333-b3cc-82b185939606
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 54d62f15-ac06-4333-b3cc-82b185939606
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=54d62f15-ac06-4333-b3cc-82b185939606 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fea35e5b-e88e-4b6c-8921-12ebc6ad26c2 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  36.7GB: boot/grub/core.img
  43.1GB: boot/grub/grub.cfg
  51.7GB: boot/grub/menu.lst
    .8GB: boot/initrd.img-2.6.35-22-generic
   2.4GB: boot/initrd.img-2.6.35-25-generic
  36.7GB: boot/vmlinuz-2.6.35-22-generic
  36.7GB: boot/vmlinuz-2.6.35-25-generic
   2.4GB: initrd.img
    .8GB: initrd.img.old
  36.7GB: vmlinuz
  36.7GB: vmlinuz.old


Advice please?

Thanks.

---

### Post by oldfred on 2011-02-04
You had the boot files from windows in another partition but the install is still in sda2. You need to run the windows repairs (posted previously) to install these two windows files to sda2.

/bootmgr /Boot/BCD 

If you run the auto repair (or fixMBR), it will also put the windows boot loader in the MBR, but that also let you test that windows boots on its own. Then you will have to reinstall grub2 to the MBR.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

You also have menu.lst from grub legacy. If you have problems we will have to uninstall both grub2 & grub legacy and reinstall grub2 cleanly.

---

### Post by Glennk on 2011-02-05
Thanks.

All fixed and running fine!

Boot menu shows Win7. And it boots fine. Well, as slow as it normally does. I'm thinking maybe Snow Leopard instead now....

---

