---
title: "Nothing showing up..."
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by c0rsana on 2010-06-16
Recently, I have tried to tweak my grub2 to run my windows partition, which was somehow changed during the 10.04 update to restart instead of run windows. In my tweaking and search for results, I downloaded a program on the Ubuntu software center that was called something like "Startup tool" or "startup config", that said it could configure grub for me. In my obvious noobishness, I set the resolutions to my native resolution, 1900x1200, and changed the default boot to a custom_40 windows partition (That may or may not have worked...).

Now, whenever I start my computer, all I get is a blinking underscore in the top left corner. If I press enter it starts blinking. I also tried booting from a gparted disk, but the same thing happened. Any suggestions? I have some important files on the windows partition that I'd very much like to not wipe. (Wiping is my second choice should a solution not be found. Hopefully it won't come to that.) So is there some hotkey or certain disk I should be booting from? :\

Extreme thanks in advance!

---

### Post by darkod on 2010-06-16
Run the boot info script from my signature and if the windows partition shows grub2 is installed on it, like shown here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

do the procedure from that link to remove grub2 from your windows partition.

As far as the startup tool, I don't know what you did but almost everything would be reversible, if not by the tool then from terminal and command line.

---

### Post by c0rsana on 2010-06-16
How would I run it? If I press anything on my keyboard it does nothing and emits a beep or two. Would I run it on a disk or something? Because I can't do anything besides choose the boot device and edit the BIOS on my computer at this point.

---

### Post by darkod on 2010-06-16
Boot with the ubuntu cd in live mode, Try Ubuntu option. That will run ubuntu from the cd.

---

### Post by c0rsana on 2010-06-16
Alright, tried that. Look like my windows partition does, in fact, have grub on it. But now, the disk version of ubuntu won't install testdisk correctly. >.<

---

### Post by darkod on 2010-06-16
> **c0rsana said:**
> Alright, tried that. Look like my windows partition does, in fact, have grub on it. But now, the disk version of ubuntu won't install testdisk correctly. >.<

If used from live mode, you need to go in System-Administration-Software Sources and enable the (universe) repository.

After that the command to install in terminal should work.

---

### Post by c0rsana on 2010-06-16
Alright, it's still giving me an error:
```
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk

```

Then when I try to run it, the predictable:
```
ubuntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found

```

---

### Post by darkod on 2010-06-16
Download it for kernel 2.6.x from here:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

It's compressed file. Right-click on it and extract it, then in the linux folder you will see file testdisk-static. This is the only file you need. Move it where ever you want to run it from, the command to run it will depend on in which folder it's located.

If you put it in the home folder in live mode for example, in terminal you execute it with:

sudo ./testdisk-static

---

### Post by c0rsana on 2010-06-16
Got the terminal version working and followed the instructions in the link, but update-grub won't work in the disk version. Should I reboot now?

---

### Post by darkod on 2010-06-16
> **c0rsana said:**
> Got the terminal version working and followed the instructions in the link, but update-grub won't work in the disk version. Should I reboot now?

You don't need update-grub, and yes, it doesn't work because you're in live mode.

Restart and check if the windows option is working now.

---

### Post by c0rsana on 2010-06-16
Nothing's showing up still... My screen literally just has a grand total of
```
_








```

And every other second, it dissappears. Then it blinks for a second. Repeats that process into infinity. I can't even see grub. I have a Dell Inspiron 1720, and all I see when it starts up is the dell logo, with a loading bar and "f2 for setup, f12 for boot menu". Then the blinking underscore appears if I don't press anything...

---

### Post by darkod on 2010-06-16
Maybe I should have asked you earlier, but are you sure you had grub2 on the MBR and a full ubuntu install, or just wubi installed inside windows?
It's not the same.

---

### Post by c0rsana on 2010-06-16
I used to have vista, then nuked my computer (Program called boot and nuke). I then installed ubuntu at the end of last summer, and installed windows 7 ultimate shortly afterwards. It's worked up until I installed the 10.04 update. grub2 the whole time. I installed ubuntu using a disk, freshly installing onto a completely empty computer. :)

That help?

And I'm wondering if it would be possible to completely overwrite the old ubuntu files/OS and have a clean install using the live disk. Or would I have to use gparted or something else first?

---

### Post by darkod on 2010-06-16
OK, that's proper dual boot.

Download the boot info script in my signature, run it and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

It will show us more details.

Yes, it is possible to just install over the old ubuntu, but you need to use Manual Partitioning and tell it what partition to use for what (root, swap, etc). But lets see the results first.

---

### Post by c0rsana on 2010-06-16
Here you go. Contents of RESULTS.txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 271935 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 271935 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   154,464,974   154,464,912  83 Linux
/dev/sda2    *    154,466,304   154,671,103       204,800   7 HPFS/NTFS
/dev/sda3         154,671,104   300,511,231   145,840,128   7 HPFS/NTFS
/dev/sda4         300,511,890   312,576,704    12,064,815   5 Extended
/dev/sda5         300,511,953   312,576,704    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        94460fad-d3d2-4753-b198-c553be93fc6f   ext4                                     
/dev/sda2        4C4E3FBF4E3FA11E                       ntfs       System Reserved               
/dev/sda3        308646368645FD3A                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0eb360c6-c793-48c4-8221-e189a1928b3b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4E79-06E9                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/308646368645FD3A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/94460fad-d3d2-4753-b198-c553be93fc6f ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout        30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=94460fad-d3d2-4753-b198-c553be93fc6f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=94460fad-d3d2-4753-b198-c553be93fc6f

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

title        Ubuntu 9.10, kernel 2.6.31-15
uuid        94460fad-d3d2-4753-b198-c553be93fc6f
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=94460fad-d3d2-4753-b198-c553be93fc6f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-15 (recovery mode)
uuid        94460fad-d3d2-4753-b198-c553be93fc6f
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=94460fad-d3d2-4753-b198-c553be93fc6f ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

# title        Ubuntu 9.10, kernel 2.6.31-14-generic
# uuid        94460fad-d3d2-4753-b198-c553be93fc6f
# kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=94460fad- # d3d2-4753-b198-c553be93fc6f ro quiet splash 
# initrd        /boot/initrd.img-2.6.31-14-generic

# title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
# uuid        94460fad-d3d2-4753-b198-c553be93fc6f
# kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=94460fad- # d3d2-4753-b198-c553be93fc6f ro  single
# initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        94460fad-d3d2-4753-b198-c553be93fc6f
kernel        /boot/grub/core.img

# title        Ubuntu 9.10, memtest86+
# uuid        94460fad-d3d2-4753-b198-c553be93fc6f
# kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows 7 Ultimate Edition
root        (hd0,1)
makeactive
chainloader    +1

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set default="7"
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 94460fad-d3d2-4753-b198-c553be93fc6f
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 94460fad-d3d2-4753-b198-c553be93fc6f
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 94460fad-d3d2-4753-b198-c553be93fc6f
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=94460fad-d3d2-4753-b198-c553be93fc6f ro  splash vga=799  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 94460fad-d3d2-4753-b198-c553be93fc6f
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=94460fad-d3d2-4753-b198-c553be93fc6f ro single  splash vga=799
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 94460fad-d3d2-4753-b198-c553be93fc6f
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=94460fad-d3d2-4753-b198-c553be93fc6f ro  splash vga=799  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 94460fad-d3d2-4753-b198-c553be93fc6f
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=94460fad-d3d2-4753-b198-c553be93fc6f ro single  splash vga=799
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 94460fad-d3d2-4753-b198-c553be93fc6f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 94460fad-d3d2-4753-b198-c553be93fc6f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c4e3fbf4e3fa11e
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7 Paul(loader) (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4c4e3fbf4e3fa11e
chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=94460fad-d3d2-4753-b198-c553be93fc6f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0eb360c6-c793-48c4-8221-e189a1928b3b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
   2.4GB: boot/grub/menu.lst
   8.1GB: boot/initrd.img-2.6.31-17-generic
    .5GB: boot/initrd.img-2.6.32-22-generic
   2.8GB: boot/vmlinuz-2.6.31-17-generic
    .8GB: boot/vmlinuz-2.6.32-22-generic
    .5GB: initrd.img
   8.1GB: initrd.img.old
    .8GB: vmlinuz
   2.8GB: vmlinuz.old
```

---

### Post by c0rsana on 2010-06-16
Also, I found the name of the program I used before grub didn't show up... It's called "StartUp-Manager", I got it from the Ubuntu Software Center thinking it would help. >.<

---

### Post by darkod on 2010-06-16
Do you have 9.04 cd at hand? I see you might still have grub1 installed, it seems you started a process to upgrade grub1 to grub2, but never finished it. That's why there is entry Chainload to Grub2 in the menu.lst.

If you started the process you should really finish it. Right now I'm not even sure if we need to reinstall grub1 or grub2, there are files from both in /dev/sda1.

---

### Post by c0rsana on 2010-06-16
Hmm. I could make another 9.04 disk, I have the .iso

However, through the disk, I think it may be easier to just backup files I want to keep, wipe the system, and reinstall both the operating systems with a correct dual boot...

---

### Post by darkod on 2010-06-16
> **c0rsana said:**
> Hmm. I could make another 9.04 disk, I have the .iso

However, through the disk, I think it may be easier to just backup files I want to keep, wipe the system, and reinstall both the operating systems with a correct dual boot...

This is a correct dual boot, I'm just wondering which grub version to reinstall. Lets try with the 10.04 or 9.10 cd. From live mode:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

See if that makes ubuntu boot. Windows will still be unable to boot because of having grub2 installed on the partition, we'll sort it out once ubuntu boots.

---

### Post by c0rsana on 2010-06-16
Nope, still nothing. same old blinky underscore. The commands you gave me worked, though, with no errors. Grub was "Successfully installed with no errors", according to the Terminal...

---

### Post by darkod on 2010-06-16
At this point it might be better to copy all the data you need in live mode, and then just reinstall on the existing partitions.
You will have to use Manual Partitioning, and tell it to use /dev/sda1 as / (by clicking on it and then the Change button), and /dev/sda5 as swap.

That still won't fix win7. You need to remove grub2 from /dev/sda2 where the win7 loader is. You can do that with this procedure from ubuntu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by c0rsana on 2010-06-16
As I said before, I have no problems with wiping and reinstalling both. I have the win7 disk, as well as the newest Ubuntu disk. All I need to do is copy the files I want to keep (ie, documents, music, videos) onto an external. At this point, I think I'm even better off doing that anyway, considering a clean wipe for the summer would actually be convenient. :)

---

