---
title: "ubuntu won't boot after installing opensuse"
date: 2012-03-08
forum: Installation &amp; Upgrades
---

### Post by joelc336 on 2012-03-08
Hello everyone I have a big problem. I have looked all over the internet for this to no avail. I'm running ubuntu 11.04 and out of spite I chose to install opensuse 12.1 alongside of it. Now I can't boot into ubuntu. For some reason either grub or the MBR just won't detect it. Can anyone please help me? I'll post whatever information needed in order to get a solution to this. 

Thank you

---

### Post by cortman on 2012-03-08
So have you tried running

```
sudo grub-install /dev/sda
```

??

---

### Post by joelc336 on 2012-03-08
> **cortman said:**
> So have you tried running

```
sudo grub-install /dev/sda
```??

The only option I have since I can only boot in opensuse is "sudo zypper /sbin/update-bootloader" and I haven't even figured out how to that because i'm missing an argument. I've been googling since yesterday. As you can see i'm very new to opensuse. I've looked at the gui bootloader control panels, and all the options I have within opensuse. Is there anything I can do with a Livecd perhaps?

---

### Post by cortman on 2012-03-08
> **joelc336 said:**
> The only option I have since I can only boot in opensuse is "sudo zypper /sbin/update-bootloader" and I haven't even figured out how to that because i'm missing an argument. I've been googling since yesterday. As you can see i'm very new to opensuse. I've looked at the gui bootloader control panels, and all the options I have within opensuse. Is there anything I can do with a Livecd perhaps?

The command I gave would be run in a terminal, and should work with openSUSE as well.

---

### Post by oldfred on 2012-03-08
You can manually add a boot stanza for Ubuntu to 40_custom Not sure where 40_custom is in OpenSuse.

Ubuntu keeps a link to the most current kernel in root, so this entry does not have to be updated on kernel changes. Change all 13 to your partition number:

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

```
menuentry "Ubuntu on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

```

---

### Post by joelc336 on 2012-03-08
ok I did that and here's the output I got

: WARNING! You are trying to invoke the unsupported grub-install script
with a parameter. To really do this, call grub-install.unsupported.
You should rather call "yast2 bootloader" or create configuration files
appropriate for the intended target.

---

### Post by joelc336 on 2012-03-08
the post above was the output of the command sudo /usr/sbin/grub-install /dev/sda

---

### Post by darkod on 2012-03-08
Does opensuse use grub2 as bootloader at all? This is what you needed to investigate before installing it, and if you don't like the bootloader coming with that distribution, simply tell it not to install a bootloader during the install. There should be Advanced option or similar to do that.
After that, running update-grub in ubuntu should have detected the new OS.

Anyway, now you can try reinstalling grub2 from ubuntu to the MBR, like it was earlier.

Boot with the ubuntu cd in live mode, and simply mount your ubuntu root partition and install grub2 to the MBR. Lets assume your ubuntu root is /dev/sda5 (use the correct partition in the first command below):

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

After that you should see your ubuntu grub2, without suse entry. Boot ubuntu and do the update-grub command.

---

### Post by joelc336 on 2012-03-08
I will try that but I want to show you this first before I do anything so I don't make any further mistakes. Sorry about all the questions. Here's my partition layout from fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       26647   214033995   83  Linux
/dev/sda2           38396       38914     4159489    5  Extended
/dev/sda3   *       26647       38396    94375936   83  Linux
/dev/sda5           38396       38914     4159488   82  Linux swap / Solaris

sda 1 is where Ubuntu is and sda3 is where opensuse is.

---

### Post by joelc336 on 2012-03-08
I keep getting this output:

install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.

---

### Post by darkod on 2012-03-08
If sda1 is ubuntu, you need to execute in live mode in terminal:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That will reinstall grub2 to the MBR of /dev/sda which will be connected to your sda1 installation.

---

### Post by joelc336 on 2012-03-08
well I got that to work finally, it installed with no errors. However once I unmounted and rebooted the strangest thing occurs. Now all I get is some error that basically flashes for like a split second saying "file error......" I think that's what it says. It appears and disappears so fast. Then I just get a black screen, No cursor or anything. Bottom line, I can't boot into either of my partitions.

---

### Post by joelc336 on 2012-03-08
haha well you guys can ignore that. Here's where i'm at step by step. I booted the ubuntu live cd. I installed grub. I mounted the root partition, ran the commands grub-install, etc. Now here's where i'm stuck. When I run the command: "sudo grub-install --root-directory=/mnt /dev/sda" Here's the output I get:

 "Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda

I check the path is describes above and it checks out ok, it just shows the same disks it says it finds. I re-run the script and get the same result.

---

### Post by darkod on 2012-03-08
That message is normal, and it says installation finished.

What exactly is the problem? Does grub2 boot menu show up now or not? Does it boot all OSs?

---

### Post by joelc336 on 2012-03-08
I get the grub prompt. I don't know if that's good or bad. Here's the exact output I get:     [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>

---

### Post by darkod on 2012-03-08
Something is wrong.

In this case it's best to run the boot info script from the link in my signature. Post the results as explained there. It will show more details.

You can do all that from live mode.

---

### Post by joelc336 on 2012-03-08
ubuntu@ubuntu:~/Downloads$ cat RESULTS.txt 
                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda1 and looks at sector 402932031 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on the same 
                       partition for /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda3 and looks at sector 436907096 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #3 
                       for /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 12.1 
                       "Asparagus" - Kernel ().
    Boot files:        /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   428,068,052   428,067,990  83 Linux
/dev/sda2         616,822,782   625,141,759     8,318,978   5 Extended
/dev/sda5         616,822,784   625,141,759     8,318,976  82 Linux swap / Solaris
/dev/sda3    *    428,068,864   616,820,735   188,751,872  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        39579244-aa5a-42f0-aa9a-8b13e5e3c0ea   ext4       
/dev/sda3        c248c5de-e746-4cf0-87cb-808e209bb785   ext4       
/dev/sda5        337fa741-4ff1-4871-8266-2780f26c7a18   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
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
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=39579244-aa5a-42f0-aa9a-8b13e5e3c0ea ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
    echo    'Loading Linux 2.6.38-13-generic ...'
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=39579244-aa5a-42f0-aa9a-8b13e5e3c0ea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=39579244-aa5a-42f0-aa9a-8b13e5e3c0ea ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=39579244-aa5a-42f0-aa9a-8b13e5e3c0ea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=39579244-aa5a-42f0-aa9a-8b13e5e3c0ea ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=39579244-aa5a-42f0-aa9a-8b13e5e3c0ea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=39579244-aa5a-42f0-aa9a-8b13e5e3c0ea ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=39579244-aa5a-42f0-aa9a-8b13e5e3c0ea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=39579244-aa5a-42f0-aa9a-8b13e5e3c0ea ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=39579244-aa5a-42f0-aa9a-8b13e5e3c0ea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 39579244-aa5a-42f0-aa9a-8b13e5e3c0ea
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=39579244-aa5a-42f0-aa9a-8b13e5e3c0ea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=337fa741-4ff1-4871-8266-2780f26c7a18 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 192.177978039 = 206.349532672  boot/grub/core.img                             1
 110.230300426 = 118.358883840  boot/grub/grub.cfg                             1
 192.133079052 = 206.301322752  boot/grub/stage2                               1
   8.254489422 = 8.863190528    boot/initrd.img-2.6.38-10-generic              2
 112.437530041 = 120.728878592  boot/initrd.img-2.6.38-11-generic              2
  17.523551464 = 18.815770112   boot/initrd.img-2.6.38-12-generic              2
 137.254462719 = 147.375857152  boot/initrd.img-2.6.38-13-generic              2
   1.445342541 = 1.551924736    boot/initrd.img-2.6.38-8-generic               2
   1.453467846 = 1.560649216    boot/vmlinuz-2.6.38-10-generic                 1
 146.672217846 = 157.488094720  boot/vmlinuz-2.6.38-11-generic                 1
  17.367530346 = 18.648243712   boot/vmlinuz-2.6.38-12-generic                 1
 137.023795605 = 147.128180224  boot/vmlinuz-2.6.38-13-generic                 1
 192.132846355 = 206.301072896  boot/vmlinuz-2.6.38-8-generic                  1
 137.254462719 = 147.375857152  initrd.img                                     2
  17.523551464 = 18.815770112   initrd.img.old                                 2
 137.023795605 = 147.128180224  vmlinuz                                        1
  17.367530346 = 18.648243712   vmlinuz.old                                    1

=========================== sda3/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Modified by YaST2. Last modification on Thu Mar  8 07:40:13 EST 2012
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# For the new kernel it try to figure out old parameters. In case we are not able to recognize it (e.g. change of flavor or strange install order ) it it use as fallback installation parameters from /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,2)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 12.1 - 3.1.9-1.4
    root (hd0,2)
    kernel /boot/vmlinuz-3.1.9-1.4-desktop root=/dev/disk/by-id/ata-TOSHIBA_MK3252GSX_X8BDT72ZT-part3 resume=/dev/disk/by-id/ata-TOSHIBA_MK3252GSX_X8BDT72ZT-part5 splash=silent quiet showopts vga=0x314
    initrd /boot/initrd-3.1.9-1.4-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 12.1 - 3.1.9-1.4
    root (hd0,2)
    kernel /boot/vmlinuz-3.1.9-1.4-desktop root=/dev/disk/by-id/ata-TOSHIBA_MK3252GSX_X8BDT72ZT-part3 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x314
    initrd /boot/initrd-3.1.9-1.4-desktop

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (fd0)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/disk/by-id/ata-TOSHIBA_MK3252GSX_X8BDT72ZT-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-TOSHIBA_MK3252GSX_X8BDT72ZT-part3 /                    ext4       acl,user_xattr        1 1
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 208.361049652 = 223.725973504  boot/grub/core.img                             1
 208.321216583 = 223.683203072  boot/grub/menu.lst                             1
 208.333633423 = 223.696535552  boot/grub/stage2                               1
 205.205078125 = 220.337274880  boot/initrd                                    2
 205.205078125 = 220.337274880  boot/initrd-3.1.9-1.4-desktop                  2
 208.504196167 = 223.879675904  boot/vmlinuz                                   1
 208.504196167 = 223.879675904  boot/vmlinuz-3.1.9-1.4-desktop                 1


```

I didn't see the # in the code thing. Believe it or not this is the first time I've ever actually posted on any forums lol. Hopefully this is the format that you were expecting. I really appreciate your help on this. You've saved me a LOT of grief.

---

### Post by darkod on 2012-03-08
You have grub legacy (grub1) on the MBR. The reinstall of grub2 didn't seem to work.

Are you doing it from live mode with a ubuntu 11.04 cd? You need to use the same version cd.

Other than that, it looks fine except that you also have grub legacy on the ubuntu partition but that shouldn't get into way.

Try once more, boot into Try Ubuntu with the 11.04 cd, open terminal and execute:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

After that try to reboot and see what happens.

If that doesn't work you might need to enter your ubuntu install and reinstall grub2 completely. Lets see.

---

### Post by joelc336 on 2012-03-08
Oh I didn't know it had to be the same version. I'm using a livecd of ubuntu 10.04. I don't have one of 11.04. I can make one it's no big deal. Whatever it takes to fix this. I'll try this once more and I'll get back to you.

---

### Post by darkod on 2012-03-08
In theory 10.04 should do the job because it also comes with grub2. All versions since 9.10 are with grub2 so as long as you use on of them it should work.

Give those commands another shot first, and run the script again. Look at the top of the results file if it says Grub Legacy or Grub 1.98 (or similar number) is installed on /dev/sda.

Yes, grub 1.98 is grub2. It should be grub2 that you see installed on /dev/sda, and not grub legacy or grub 0.97, etc.

---

### Post by joelc336 on 2012-03-08
Well I tried it again and no matter what i'm still stuck at the grub prompt. I went ahead a little bit and I tried something that I think had solved that problem before. I had that happen to me before when I installed fedora alongside ubuntu on my other laptop, and somehow I was able to access the same grub prompt when I was inside an actual partition, and I did this: 

1) typed "grub" in terminal
2) at the grub prompt: find /boot/grub/stage1 
which in turn outputs this: (hd0,0)
                                          (hd0,2)
3) then I typed "root (hd0,0)" 
4) then "setup (hd0,0) 

It executed with no errors but I ended up with the same result as before. I will make a live cd of 11.04 and I guess we'll go from there. I'll get back to you.

---

### Post by oldfred on 2012-03-08
Added code tags to post of boot info script just to make a bit easier to review.

You do have to use same version with grub 1.99. The old install steps should work but they have update with a slightly different version for grub 1.99.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#[COLOR=Red]If grub 1.99 with Natty or later uses boot not root.[/COLOR]
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by joelc336 on 2012-03-08
I'm not sure if i'm doing something wrong or not but I think I'm doing exactly what you guys are telling me. I went ahead and ran a livecd ubuntu 11.04. Now when I open a terminal I immediately run sudo apt-get install grub. I've tried to install grub2 and it gives me an error saying there's no candidate. 

After I install grub I update it all right there on the livecd. I'm not sure what you guys mean about installing it on sda5. I thought I was installing grub in my particular linux partition which happens to be sda1, when I run the "sudo grub-install" command. 

Here's how it looks exactly: 

sudo mount /dev/sda1 /mnt

sudo grub-install --root-directory=/mnt/ /dev/sda
OUTPUT: Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda

----------------------------------------------------------------------------------

Should I do this afterwards? 

1) sudo grub

grub> find /boot/stage1-2
(hd0,0)
(hd0,2)

grub> root (hd0,0)

grub> setup (hd0,0)
OUTPUT: Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.
 
grub> quit

I've done exactly step by step what i've described above and all i get when I boot up is this:  grub>

---

### Post by darkod on 2012-03-09
NO.

You just need to run the two commands I gave you, booting with the 11.04 cd.

First of all, don't run sudo apt-get install grub, because you are in live mode and it doesn't install like that. In fact, that might be the reason why you are ending up with grub1 and not grub2.

The package for grub1 is grub, and for grub2 is grub-pc. But you DO NOT need to do any of this, you are in live mode not inside your hdd installation.

Also, the group of commands you specified later is the procedure to reinstall (restore) grub1, not grub2. You never do any find /boot/stage, etc, nothing.

Look again at post #11 and when you open terminal in live mode do only that. NOTHING MORE!

After that restart and see if ubuntu boots up.

---

### Post by joelc336 on 2012-03-09
ALRIGHT!! I'm back in business. I feel so stupid but I can't say I haven't learned anything. Thank so much for sticking with me through this. I really needed this. I'm studying networking using the GNS3 Emulator which was in my ubuntu partition and I couldn't afford to lose all that so I really appreciate your help and anyone else that pitched in on this thank you!!!!!

---

### Post by darkod on 2012-03-09
No problem.

Now, suse doesn't exist in the grub2 menu because it was installed later. In case you haven't done it already, boot ubuntu, open terminal and do:

sudo update-grub

See if that adds suse to the grub2 menu and if it can boot OK.

---

### Post by joelc336 on 2012-03-09
It all works fine. I tried it all before I replied the last time. I made sure it all worked. I've been a huge ubuntu or should I say "debian" based linux fan for a while, and I've never really gotten so much into redhat rpm based linux, so that's what my main motive was for installing opensuse. On my other computer I have fedora 12, and I'm trying to get familiar with them.

---

