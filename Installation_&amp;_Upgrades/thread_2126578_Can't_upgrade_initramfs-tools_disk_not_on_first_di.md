---
title: "Can't upgrade initramfs-tools: disk not on first disk?"
date: 2013-03-17
forum: Installation &amp; Upgrades
---

### Post by gfunkdave on 2013-03-17
I'm running Ubuntu 12.04 and noticed that I have been getting the following error on all upgrades:

```
Setting up initramfs-tools (0.99ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic
Warning: /dev/disk/by-id/ata-ST3320813AS_9SZ3W20C is not on the first disk
Fatal: No images have been defined.
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now, the disk it's looking for is and always has been /dev/sdb, so I really don't know why it would suddenly start complaining about that. At least, I assume it means it wants that disk to be sda.

I have tried all the usual remedies: apt-get purge, apt-get clean, apt-get autoremove, etc.

Does anyone know what's going on?

Thanks

---

### Post by gfunkdave on 2013-03-17
As an update (problem not solved)...I figured out the problem is occurring when lilo runs as part of the initramfs-tools update. After some Googling, I found that manually assigning the two disks new BIOS addresses can resolve this. So, I added the below to /etc/lilo.conf:

```

disk = /dev/disk/by-id/ata-ST3320813AS_9SZ3W20C
bios = 0x80

disk = /dev/disk/by-id/ata-WDC_WD15EARS-32MVWB0_WD-WCAZA2393985
bios = 0x81

```

Now, when I try to run dpkg --configure -a or apt-get upgrade, I just get this:

```

Setting up initramfs-tools (0.99ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic
Fatal: No images have been defined.
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools

```

Can anyone help? I might just need to reinstall Linux, I'm worried.

---

### Post by dino99 on 2013-03-18
why are you not following the ubuntu grub choices which use uuid ?

---

### Post by nibal on 2013-03-18
> **gfunkdave said:**
> As an update (problem not solved)...I figured out the problem is occurring when lilo runs as part of the initramfs-tools update. After some Googling, I found that manually assigning the two disks new BIOS addresses can resolve this. So, I added the below to /etc/lilo.conf:

```

disk = /dev/disk/by-id/ata-ST3320813AS_9SZ3W20C
bios = 0x80

disk = /dev/disk/by-id/ata-WDC_WD15EARS-32MVWB0_WD-WCAZA2393985
bios = 0x81

```

Now, when I try to run dpkg --configure -a or apt-get upgrade, I just get this:

```

Setting up initramfs-tools (0.99ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic
Fatal: No images have been defined.
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools

```

Can anyone help? I might just need to reinstall Linux, I'm worried.

No, you don't need to reinstall Linux for bootloader problems!

What is the output of your:
```

lilo

```

Please display your lilo.conf file.
The error is right. You can not have 2 subsequent disk definitions, without an intervening
image definition, and i am surprised that lilo runs without errors. For the syntax in
lilo.conf use:

```

man lilo.conf

```

HTH,
Nikos

---

### Post by gfunkdave on 2013-03-18
OK. I have removed the BIOS re-definitions from my second post from lilo.conf. It is now back to plain vanilla.

As to your question about why I don't use UUID...I have never touched any of this before now. This is just what the system has generated. 

Thanks!

```

david@ike:~$ sudo lilo
Warning: /dev/disk/by-id/ata-ST3320813AS_9SZ3W20C is not on the first disk
Fatal: No images have been defined.

```

The output is still a little different: prior to adding the BIOS definitions I did not get the second error of no images are defined. 

```

david@ike:~$ sudo cat /etc/lilo.conf
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
#boot = /dev/sdb
boot = /dev/disk/by-id/ata-ST3320813AS_9SZ3W20C

# This option may be needed for some software RAID installs.
#raid-extra-boot = mbr-only

# Enable map compaction.  This tries to merge read requests for
# adjacent sectors into a single read request. This drastically
# reduces load time and keeps the map smaller.  Using 'compact'
# is especially recommended when booting from a floppy disk.
# It is disabled here by default because it doesn't always work.
#compact

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
#menu-title = " DESDEMONA Boot-Manager "

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
timeout = 100
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

# Set the image which should be started after delay or timeout.
# If not set, the first defined image will be started.
#default = Linux


# ################### LILO per-image section ####################

# Each image is configured with the linux kernel (=image) and
# usually with the initrd file. Configure all GNU/Linux systems
# on other partitions, too.

david@ike:~$

```

---

