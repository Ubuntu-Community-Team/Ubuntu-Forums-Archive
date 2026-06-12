---
title: "bootcd : create live cd with nfs root and local (on cd) /boot partition"
date: 2015-09-11
forum: Installation &amp; Upgrades
---

### Post by jgngnj on 2015-09-11
Hi @ all,

I'm following a little project for reusing old PCs. For doing this i have followed the (bad written) tutorial here: [https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot]("https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot") (**warning**: half of this page is totally wrong or double old) but after my changes all seems run very well. On the pc grub boot from /boot partition then aquire DHCP ip then mount right root from NFS and startup ends correctly.

But, my goal is to boot via cd then aquire DHCP ip then mount right root from NFS so, I have installed bootcd (check this: [https://launchpad.net/ubuntu/+source/bootcd]("https://launchpad.net/ubuntu/+source/bootcd")) and edited the bootcdwrite.conf as follow:

```

#
# bootcdwrite.conf
#
# look for man bootcdwrite.conf(5) for more informations
#

# this path was added as prefix to KERNEL, INITRD, DISABLE_CRON, NOT_TO_CD
# and NOT_TO_RAM, if this are relativ paths (without starting "/")
SRCDISK=/

# Define the kernel which is used
KERNEL=/boot/vmlinuz-3.19.0-26-generic

# additional options for the kernel
# If you boot bootcd via HP ILO you might get the message:
# "Monitor is in graphics mode or an unsupported text mode" 
# even if only text is displayed. To prevent this:
# APPEND="vga=normal nomodeset" is configured.
#APPEND="vga=normal nomodeset"
APPEND="root=/dev/nfs nfsroot=10.0.2.16:/srv/exports/u rw ip=dhcp"

# path to initrd
INITRD="/boot/initrd.img-NFS"

# define multiple kernels with KERNEL<number> and label KLABEL<number>
# default label is "linux<number>
# KLABEL1=686-3
# KERNEL1=/boot/vmlinuz-2.6.18-3-686-bigmem
# INITRD1=/boot/initrd.img-2.6.18-3-686-bigmem
# APPEND1=

# Text to Display at Boottime (see syslinux doku)
# display info files on boot prompt (F1 = DISPLAY, F2 = DISPLAY2 ...)
# (kernelinfo is replaced with a file which includes the kernelinfo)
DISPLAY="/usr/share/bootcd/default.txt"
DISPLAY2="kernelinfo"

# typ is CD or DVD
TYP=CD

# specify one or more CD devices to boot from, first is default
# "auto" try to find the bootcd on all SCSI and IDE CDROMS
CDDEV="auto /dev/hda /dev/hdb /dev/hdc /dev/hdd /dev/sr0 /dev/sr1"


# do some checks or not
DO_CHECK=yes

# exclude some files or directories from writing to cd 
NOT_TO_CD=""

# If you are using ssh it is helpful to have a unique ssh hostkey for
# each CD.
SSHHOSTKEY=yes

# If you are using udev filesystem and install the image only on other 
# machines you need to set this to "yes" because the network interfaces are 
# hardwired in /etc/udev/rules.d/z25_persistent-net.rules (etch) or in 
# /etc/udev/rules.d/70-persistent-net.rules (lenny) and we must remove 
# them. You can do this also on bootcd2disk.
UDEV_FIXNET="yes"

# logfile
ERRLOG=/var/log/bootcdwrite.log

# where the image resists after build
VAR=/mnt/mkbootcd/bootcd

# FLOPPY_RUNTIME_DEV=<floppy device>|""
# When you boot from cd you read changes from this device.
FLOPPY_RUNTIME_DEV=/dev/fd0

# BOOTFLOPPY=yes|no
# If you want to boot from FLOPPY specify BOOTFLOPPY=yes. This reduces
# space on floppy used by bootcdflopcp. For this to work FLOPPY_CREATE_DEV
# has to be specified.
# Default:
#   BOOTFLOPPY=no
BOOTFLOPPY=no

# If you want to boot several machines from the same cdrom, you must have
# the individual configuartion (exp: /etc/network/interfaces) on floppy.
# If one can not be mounted it is a good idea to stop booting and to wait
# for manual interaction instead of comming up with a wrong configuration.
BOOT_ONLY_WITH_FLOPPY=no

# delete some chached files in /var
CLEAN_VAR=yes

# addiditionel entries to fstab
# TO_FSTAB="/dev/hdc1 /home ext3 defaults 1 1
# /dev/usb0 /mnt/usb ext3 defaults 1 1 "
TO_FSTAB=""

COMPRESS=no
# Files or Directory-Trees that should never be compressed on CD can be listed
# here.
NOTCOMPRESSED=""

# Files listed in DISABLE_CRON will be on the cdrom with a .no_run_on_bootcd
# suffix so run-parts won't execute them. The original file will be a link to
# /bin/true.
#
DISABLE_CRON="etc/cron.daily/find etc/cron.daily/standard etc/cron.daily/security"

# With this variable you can add or delete some options 
# given to mkisofs by bootcdwrite. 
#   Please create debian-bugreports if you have to use special 
#   options, not mentioned here. Then I can list this options here.
#
MKISOFS_CHNG=""

# extra_changes()
# It is possible to define a function called extra_changes to have some
# files modified on the ISO image. Here is an example:
#
#   extra_changes() {
#     echo "noname" >$VAR/changes/etc/hostname
#
#     mkdir -p $VAR/changes/etc/network
#     ( echo "auto lo"
#       echo "iface lo inet loopback"
#       echo ""
#       echo "auto eth0"
#       echo "iface eth0 inet static"
#       echo "       address 0.0.0.0"
#       echo "       netmask 255.255.255.0"
#     ) >$VAR/changes/etc/network/interfaces
#
#     echo "127.0.0.1 localhost noname" >$VAR/changes/etc/hosts
#
#     cat $SRCDISK/etc/passwd |
#     grep -v -e "^bs:" -e "^bianca:" -e "^tim:" >$VAR/changes/etc/passwd
#
#     cat $SRCDISK/etc/shadow |
#     grep -v -e "^bs:" -e "^bianca:" -e "^tim:" >$VAR/changes/etc/shadow
#
#     cat $SRCDISK/etc/group | 
#     grep -v -e "^bs:" -e "^bianca:" -e "^tim:" >$VAR/changes/etc/group
#   }
#
#

# BOOTCDMODPROBE=standard|bootcd|auto
# If booted from initrd bootcd has to load the necessary modules. 
# If only modules provided by initramfs-tools are needed you can 
# specify "standard" here. If bootcd should try extra hard to load 
# neccessary modules you can specify "bootcd" here. 
# Bootcd will use discover for this purpose. So discover has to be installed.
# If you specify auto, bootcd will check if discover is installed. 
# If it is installed # BOOTCDMODPROBE=bootcd will be set, if not 
# BOOTCDMODPROBE=standard will be set.
# Be aware that people have reported, that sometimes BOOTCDMODPROBE=bootcd 
# may not work but sometimes it is needed.
BOOTCDMODPROBE=standard

```


Iso cd is correctly created (i have created a test lab using virtualbox) and nfs server is exported and ready, but when I boot from cd after boot, kernel searching for NFS server with message:

```

bootcdproberoot: searching on devices nfs

```

Boot exit with error and start busybox (no good :( ) :

[IMG]http://i62.tinypic.com/20zuzxl.png[/IMG]

No IP is assigned (but if you check, NIC is already created and i'm able to up networking and mount nfs, check screenshot):


 [IMG]http://i62.tinypic.com/348pojn.png[/IMG]

Can you help me? If you know another alternative method without using bootcd (but without using TFTP and PXE boot please!) all helps are welcome!

Extra info: initrd-NFS is created with following initramfs.conf and AFTER the bootcd installation (and, again, with /boot in local HD all works fine):
```

#
# initramfs.conf
# Configuration file for mkinitramfs(8). See initramfs.conf(5).
#
# Note that configuration options from this file can be overridden
# by config files in the /etc/initramfs-tools/conf.d directory.

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add most filesystem and all harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

#MODULES=most
MODULES=netboot

#
# BUSYBOX: [ y | n ]
#
# Use busybox if available.
#

BUSYBOX=y

#
# COMPCACHE_SIZE: [ "x K" | "x M" | "x G" | "x %" ]
#
# Amount of RAM to use for RAM-based compressed swap space.
#
# An empty value - compcache isn't used, or added to the initramfs at all.
# An integer and K (e.g. 65536 K) - use a number of kilobytes.
# An integer and M (e.g. 256 M) - use a number of megabytes.
# An integer and G (e.g. 1 G) - use a number of gigabytes.
# An integer and % (e.g. 50 %) - use a percentage of the amount of RAM.
#
# You can optionally install the compcache package to configure this setting
# via debconf and have userspace scripts to load and unload compcache.
# 

COMPCACHE_SIZE=""

#
# COMPRESS: [ gzip | bzip2 | lzma | lzop | xz ]
#

COMPRESS=gzip

#
# NFS Section of the config.
#

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

#BOOT=local
##########NFS#########
BOOT=nfs
DEVICE=eth0
NFSROOT=10.0.2.16:/srv/exports/u
#######################

#
# DEVICE: ...
#
# Specify a specific network interface, like eth0
# Overridden by optional ip= bootarg
#

#DEVICE=

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

#NFSROOT=auto

```

---

