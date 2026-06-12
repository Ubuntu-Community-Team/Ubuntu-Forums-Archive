---
title: "Lilo Config Problem"
date: 2004-12-24
forum: Installation &amp; Upgrades
---

### Post by Thanatos9602 on 2004-12-24
[size=3]I am putting this up on the Ubuntu, DamnSmall & Linux Questions forums. I redid my harddrive & used Ubuntu to set up the linux partitions. I have Ubuntu on hda5, installed with Lilo. I tried editing lilo.conf, but didn't have much luck. It would only let me boot to Ubuntu or Win98SE. I installed DamnSmall on hda6 & reinstalled Lilo. Edited it for 98 first & default, dsl second & other empty win drives. My problem is?? How do I put an entry in Lilo so I have the choice of Ubuntu. I tried different forms of /dev/hda5 & image=vmlinuz (with all the numbers) . Nothing works. How do I run two linux systems on the same computer?? Thanks for the help & the time.
 
Here is a copy of my lilo.conf out of DSL's etc folder:
 
```
vga=791
# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# --------------- `install-mbr(8)', `/usr/share/doc/lilo/',
# and `/usr/share/doc/mbr/'.
# +---------------------------------------------------------------+
# | !! Reminder !! |
# | |
# | Don't forget to run `lilo' after you make changes to this |
# | conffile, `/boot/bootmess.txt', or install a new kernel. The |
# | computer will most likely fail to boot if a kernel-image |
# | post-install script or you don't remember to run `lilo'. |
# | |
# +---------------------------------------------------------------+
# Support LBA for large hard disks.
#
lba32
# Overrides the default mapping between harddisk names and the BIOS'
# harddisk order. Use with caution.
#disk=/dev/hde
# bios=0x81
#disk=/dev/sda
# bios=0x80
# Specifies the boot device. This is where Lilo installs its boot
# block. It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/hda
# Specifies the device that should be mounted as root. (`/')
#
root=/dev/hda6
# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller. Using `compact' is especially recommended when
# booting from a floppy disk. It is disabled here by default
# because it doesn't always work.
#
# compact
# Installs the specified file as the new boot sector
# You have the choice between: bmp, compat, menu and text
# Look in /boot/ and in lilo.conf(5) manpage for details
#
install=/boot/boot-menu.b
# Specifies the location of the map file
#
map=/boot/map
# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration. If a
# command line is given, other than one specified by an `append'
# statement in `lilo.conf', the password will be required, but a
# standard default boot will not require one.
#
# This will, for instance, prevent anyone with access to the
# console from booting with something like `Linux init=/bin/sh',
# and thus becoming `root' without proper authorization.
#
# Note that if you really need this type of security, you will
# likely also want to use `install-mbr' to reconfigure the MBR
# program, as well as set up your BIOS to disallow booting from
# removable disk or CD-ROM, then put a password on getting into the
# BIOS configuration as well. Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000
# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=20
# You can put a customized boot message up if you like. If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress. `single-key' goes with the `alias' lines in the
# `image' configurations below. eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
prompt
timeout=150
# prompt
# single-key
# delay=100
# timeout=100
# Kernel command line options that apply to all installed images go
# here. See: The `boot-prompt-HOWO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
append="hda=scsi hdb=scsi hdc=scsi hdd=scsi hde=scsi hdf=scsi hdg=scsi hdh=scsi apm=power-off nomce"
# Boot up 98 by default.
#
default=98
other=/dev/hda1
label="98"
image=/boot/vmlinuz
label=dsl
# read-only
# restricted
# alias=1
image=/vmlinuz.old
label=LinuxOLD
read-only
optional
# restricted
# alias=3
# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
# label=HURD
# restricted
# alias=4
other=/dev/hda10
label="Windows(hda10)"
other=/dev/hda11
label="Windows(hda11)"
other=/dev/hda12
label="Windows(hda12)"
other=/dev/hdb1
label="Windows(hdb1)"
 
```
Mod note: Code tags make stuff like this easier to read. - Rancoras
[/size]

---

