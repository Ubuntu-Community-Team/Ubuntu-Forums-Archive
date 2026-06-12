---
title: "Install Ubuntu in a 160GB HD USB BOX"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by Lord_ZealoN on 2005-03-30
Hi, i'm trying to install Ubuntu hoary preview on my laptop (compaq
nx9030) with a HD 160GB with chasis USB

The install is good, but, when i reboot, i get this error

pivot_root: No such file or directory
/sbin/init : 429: Cannot open Dev/Console: No such File
Kernel Panic: Attempted to Kill Init

I have 2 HD

HD 40GB - Windows XP Home (in laptop)
HD 160GB with USB Chasis (i like this for ubuntu)

Grub is in MBR and the 160GB HD has this partitions

Swap with 500MB
"/" with 100GB (ext3)
59.5 GB in FAT32

Somebody have any idea?

With warty i can't too

Thank you very much and Sorry for my bad english, this is a resume of my
spanish mail.

----------
Hola a todos.

Recién me acaba de llamar un amigo que intenta instalar la ubuntu warty
que le regalé para que la probase.

Intenta instalarlo en un HD 160GB conectado a su portatil con un chasis
USB.

Ha creado 3 particiones primarias. Una de intercambio, una de 100GB y
otra de 59.5 GB

La instalación dice que ha ido sin problemas hasta que ha reiniciado y
ha seleccionado en grub a Ubuntu para arrancar...con este mensaje.

pivot_root: No such file or directory
/sbin/init : 429: Cannot open Dev/Console: No such File
Kernel Panic: Attempted to Kill Init

Grub instalado en el MBR
/ montada en la partición de 100GB
La partición de 59.5 formateada en FAT32

Yo he intentado hacer la misma jugada (solo que yo he probado con la
ultima preview de hoary) puesto nos compramos los HD y los chasis
juntos, y la verdad, es que me da el mismo error y ahora mismo no se me
ocurre que puede ser.

Un saludo, y graciias.

---

### Post by Lord_ZealoN on 2005-03-31
up

---

### Post by Marble2 on 2005-03-31
I have a little bit different setup, but the same problem. I am running lilo though. I also can't boot to windows, I get a "NTLDR is missing" error when I try that, so I'm guessing the problem might be in my lilo.conf? here it is, if it helps. 
```
# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.

# +---------------------------------------------------------------+
# |                        !! Reminder !!                         |
# |                                                               |
# | Don't forget to run `lilo' after you make changes to this     |
# | conffile, `/boot/bootmess.txt' (if you have created it), or   |
# | install a new kernel.  The computer will most likely fail to  |
# | boot if a kernel-image post-install script or you don't       |
# | remember to run `lilo'.                                       |
# |                                                               |
# +---------------------------------------------------------------+

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/hda

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/hda4

# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller.  Using `compact' is especially recommended when
# booting from a floppy disk.  It is disabled here by default
# because it doesn't always work.
#
# compact

# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu

# Specifies the location of the map file
#
map=/boot/map

# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration.  If a
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
# BIOS configuration as well.  Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000

# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=300

# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
#       prompt
#       delay=100
#       timeout=100

# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode> )
#
# vga=ask
# vga=9
#
vga=normal

# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
 
# If you used a serial console to install Ubuntu, this option should be
# enabled by default.
# serial=

#
# Boot up Linux by default.
#
default=Windows

image=/vmlinuz
        label=Linux
        read-only
#       restricted
#       alias=1
        initrd=/initrd.img
        root=/dev/hda4

image=/vmlinuz.old
        label=LinuxOLD
 read-only
 optional
# restricted
# alias=2

 initrd=/initrd.img.old


# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
# label=HURD
# restricted
# alias=3
other=/dev/hdd1
 label=Windows
 optional
 alias=4

```

---

### Post by Lord_ZealoN on 2005-04-01
Well.....i will try to install lilo instead of grub, but i think thath this is not the problem

Greetings

---

### Post by propagandhi on 2005-05-18
First of all, I am disappointed no-one else has cleared this up yet. There's nothing you can do in your grub or lilo configuration that will change this problem. The cause of the problem stems from the fact that the kernel is not loading the necessary modules to support mounting and using USB as the root partition. I have seen this on various distributions, the error message sometimes varies, but the fact is, the kernel hasn't loaded the USB drivers/modules before attempting to mount what it needs to see as the root partition in order to boot.

I found the only way to achieve booting a linux distro of a USB drive is to actually re-create the initrd (ramdisk) image with USB modules set to preload. To be honest, I have thus far only been able to do this 100% successfully with Fedora Core 3, but I know it could be done with any linux distro, because the theory is much the same.

In the case of fedora core 3 i was able to execute mkinitrd --with-usb --preload (all the USB modules here, such as ehci, etc etc).

The complete guide for this method is found at [http://www.simonf.com/usb](http://www.simonf.com/usb) 

What would be really handy is if someone wrote a utility to perform such an operation, or better yet if it were included as an optional ramdisk for those installing under such circumstances.  I am writing now whilst using fedora on my USB drive, and must admit, I am really disappointed I cant do this with Ubuntu as yet.

---

