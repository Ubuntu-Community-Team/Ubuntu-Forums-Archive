---
title: "Disk drive for / not ready or not present"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by nibal on 2013-03-12
I am a linux veteran, but first time i try Ubuntu (or Debian). Ubuntu 12.04.2 installed fine from the image, but I have started changing a few things around and I need some help.
I uninstalled grub and installed Lilo. On my first boot since, I get:

```

disk drive for / not ready or present
(s) Skip mounting it (m) enter maintenance shell (i) ignore

```

These are approximate, since I do not have /var/log/messages at this point. Strange is that if I enter Maintenance at this point, I find / mounted read-only and fine. I have tried
Maintenance and examining my installation from the liveCD, but nothing so far. All my drives are OK by e2fsck and UUID entries in /etc/fstab are verified and the same as the
working ones with grub. I have also used dpkg --config -a to no result. Lilo runs clean. Any clues appreciated.

TIA,
Nikos

```

ubuntu@ubuntu:/usr/bin$ sudo fdisk /dev/sda

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3f1abf12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      240974      119463+  83  Linux
/dev/sda2          240975   164087909    81923467+   7  HPFS/NTFS/exFAT
/dev/sda3       164087910  1953520064   894716077+   f  W95 Ext'd (LBA)
/dev/sda5       164087973   307323449    71617738+   7  HPFS/NTFS/exFAT
/dev/sda6       307324928   311531519     2103296   82  Linux swap / Solaris
/dev/sda7       311533568   593149951   140808192   83  Linux
/dev/sda8       593151993  1953520064   680184036    7  HPFS/NTFS/exFAT

ubuntu@ubuntu:/usr/bin$ cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=b36e15ed-7929-475e-801e-1357f4a7d3b7 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=f918837b-bb6c-4804-bcbe-e402eb532d26 /boot           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=49816ae1-dfde-4419-b305-1295dd72c0ba none            swap    sw              0       0

ubuntu@ubuntu:/usr/bin$ sudo blkid /dev/sda7
/dev/sda7: UUID="b36e15ed-7929-475e-801e-1357f4a7d3b7" TYPE="ext4" 
ubuntu@ubuntu:/usr/bin$ sudo blkid /dev/sda1
/dev/sda1: UUID="f918837b-bb6c-4804-bcbe-e402eb532d26" SEC_TYPE="ext2" TYPE="ext3"
ubuntu@ubuntu:/usr/bin$ sudo blkid /dev/sda6
/dev/sda6: UUID="49816ae1-dfde-4419-b305-1295dd72c0ba" TYPE="swap"

ubuntu@ubuntu:/usr/bin$ sudo cat /mnt/etc/lilo.conf
# /etc/lilo.conf  -   systemwide LILO configuration (LILO 23)
# details see in manpages: lilo(8) and lilo.conf(5)

# +-------------------------------------------------------------+
# |                        !! Reminder !!                       |
# |                                                             |
# | Don't forget to run 'lilo' after you make changes to this   |
# | conffile or you have installed a new kernel.                |
# +-------------------------------------------------------------+


# #################### LILO global section ######################

# With all newer systems (until year 2004) you can use the RAM
# above 15 MB. This option allows the use of this range of RAM.
#large-memory

# With all newer systems you can boot from any partition on disks 
# with more than 1024 cylinders. This option allows the use of 
# partitions above 1024 cylinders.
lba32

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
# With newer kernel you should use the ID of the boot device, which
# can be found here: /dev/disks/by-id/ata*.
#boot = /dev/sda
boot = /dev/disk/by-id/ata-WDC_WD10EARS-00Y5B1_WD-WCAV55787502

# This option may be needed for some software RAID installs.
#raid-extra-boot = mbr-only

# Enable map compaction.  This tries to merge read requests for 
# adjacent sectors into a single read request. This drastically 
# reduces load time and keeps the map smaller.  Using 'compact' 
# is especially recommended when booting from a floppy disk.  
# It is disabled here by default because it doesn't always work.
compact

# Set the verbose level for bootloader installation. Value range:
# 0 to 5. Default value is 0.
#verbose = 1

# Specifies the location of the map file. Lilo creates the (sector) 
# map file of direct sector addresses which are independent of any
# filesystem.
map = /boot/map

# ---------------------------------------------------------------

# Specifies the menu interface. You have the choice between:
#   text: simple text menu with black background and white text
#   menu: configurable text menu with background and text colors.
#   bmp:  graphical menu with 640x480 bitmap background.
install = menu

# A) Customized boot message for choice 'text'.
# For the simple text menu you can set an extra message in the 
# created file. Its text will be displayed before boot prompt.
#message = /boot/message.txt

# B) Configuration of the scheme for choice 'menu'.
# Use following coding: <text>:<highlight>:<border>:<title>
# The first character of each part sets the text frontcolor, 
# the second character of earch part sets the text backcolor,
# an upper-case character sets bold face text (frontcolor).
# i.g. 'menu-scheme=wm:rw:wm:Wm'. Possible colors: 
# k=black, b=blue, g=green, c=cyan, r=red, m=magenta, y=yellow, w=white.
menu-scheme = Wb:Yr:Wb:Wb
menu-title = " DrWho's PC "

# C) Configuration of the image for choice 'bmp'.
# For the graphical menu you need a bitmap file, which needs a special
# menu configuration in the file header (see: lilo -E). Ideally you 
# use one of the delivered images of the lilo package.
#   with 16 colors:    onlyblue, tuxlogo, inside
#   with 256 colors:   coffee
#   for Debian:        debianlilo, debian, debian-de
#bitmap = /boot/tuxlogo.bmp

# ---------------------------------------------------------------

# Specifies the number of deciseconds (0.1 seconds) how long LILO 
# should wait before booting the first image.  LILO doesn't wait if
# 'delay' is omitted or set to zero. You do not see the defined menu.
#delay = 20

# Prompt to start one certain kernel from the displayed menu.
# It is very recommeded to also set 'timeout'. Without timeout boot 
# will not take place unless you hit return. Timeout is the number
# of deciseconds (0.1 seconds) after there the default image will 
# be started. With 'single-key' alias numbers for each menu line can
# be used.
prompt
#timeout = 100
#single-key

# ---------------------------------------------------------------

# Specifying the VGA text mode that should be selected when booting.
# The following values are recognized (case is ignored):
#   vga=normal    80x25 text mode (default)
#   vga=extended  80x50 text mode (abbreviated to 'ext')
#   vga=ask       stop and ask for user input: choice of text mode
#   vga=<mode>    use the corresponding text mode number. A list of  
#                   available modes can be obtained by booting with  
#                   vga=ask'  and then pressing [Enter].
# Another way is the use of frame buffer mode. Then the kernel 
# will switch from the normal vga text mode (80x25) to the frame
# buffer mode (if frame buffer support is in the kernel):
#   vga=0x314      800x600 @ 16 bit
#   vga=0x317     1024x768 @ 16 bit
#   vga=0x318     1024x768 @ 24 bit
#vga = ask
vga = normal
#vga = 0x317

# ---------------------------------------------------------------

# Kernel command line options that apply to all installed images go
# here.  See 'kernel-parameters.txt' in the Linux kernel 'Documentation'
# directory. I.g. for start into 'init 5' write:  append="5"
#append = ""
 
# If you used a serial console to install Debian, this option should be
# enabled by default.
#serial = 0,9600

root=/dev/sda7
read-only

# Set the image which should be started after delay or timeout.
# If not set, the first defined image will be started.
default = Linux


# ################### LILO per-image section ####################

# Each image is configured with the linux kernel (=image) and
# usually with the initrd file. Configure all GNU/Linux systems
# on other partitions, too.

image=/boot/vmlinuz
    label=Linux
    initrd=/boot/initrd

image=/boot/memtest86+_multiboot.bin
    label="Memory Test"

other=/dev/sda2
    label=Windows
    boot-as=0x80

```

---

### Post by schragge on 2013-03-12
Just guessing, try
```
sudo update-initramfs -u
```

---

### Post by nibal on 2013-03-12
> **schragge said:**
> Just guess, try
```
sudo update-initramfs -u
```

Wow! That was fast. Thanks, but no, thanks. Unfortunately it didn't work. What's more when I switched back to grub,
I didn't run update-initramfs -u and it worked fine. Therefore it is not needed for bootloader switching.

However I am marking this thread as solved. It has to do with kernel compilation or the System-map created. 
Ubuntu must compiled its kernel with grub in mind. I have tested the same exact disk/partition 
layout with opensuse 12.2 and using the same kernel version, although the default BL was grub, 
I had no problem switching to Lilo.

Therefore the solution would be to recompile the kernel from sources. I will do it sometime in the future.
The funny thing is that in looking to debug Lilo, I learned to use grub2, and I kind of liked it better. ;)

Regards,
Nikos

---

