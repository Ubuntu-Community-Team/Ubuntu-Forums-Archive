---
title: "GRUB Error 15 after Karmic upgrade from Jaunty"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by mkuser on 2010-01-07
I can usually find an answer by searching the forum but this time I tried for many hours and nothing helped ](*,) 
so I gave up and registered on the forum. :)

Yesterday when I upgraded from Jaunty to Karmic my sound stopped working. After doing some searching, the problem seemed identical to Ubuntu [Bug#470265]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/470265") (No sound in Karmic, 'uname -r' command shows I'm still running kernel from Jaunty, etc.) So I followed the recommended advice and ran 'sudo update-grub' and rebooted but still no sound and uname -r still shows Jaunty kernel 2.6.28.

I reboot again and this time hit escape when GRUB is loading and it displayed a menu and I choose kernel 2.6.31 and I get "error 15: File not found." When I press any key it takes me back to the GRUB menu. Then I tried kernel 2.6.28 again and now it also gives me the "error 15: File not found." Now I can't get in at all.
 
Here's my setup, I started with a Gateway MX6920 laptop with core 2 duo, pre-installed with Windows XP Home: Media Center Edition. About a year ago I installed Intrepid Ibex inside my windows partition with Wubi installer.

Here's a copy of my menu.lst

```

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
# kopt=root=UUID=5058A7AF58A79270 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5058A7AF58A79270

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

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        5058A7AF58A79270
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=5058A7AF58A79270 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        5058A7AF58A79270
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=5058A7AF58A79270 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.28-13-generic
uuid        5058A7AF58A79270
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5058A7AF58A79270 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode)
uuid        5058A7AF58A79270
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5058A7AF58A79270 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.10, kernel 2.6.27-7-generic
uuid        5058A7AF58A79270
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=5058A7AF58A79270 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.10, kernel 2.6.27-7-generic (recovery mode)
uuid        5058A7AF58A79270
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=5058A7AF58A79270 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.10, memtest86+
uuid        5058A7AF58A79270
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```Thank you in advance.

---

### Post by byStanderone on 2010-01-07
...hope this helps, specially #13 (reintalling grub) :
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

