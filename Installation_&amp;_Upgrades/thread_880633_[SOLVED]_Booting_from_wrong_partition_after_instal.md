---
title: "[SOLVED] Booting from wrong partition after installing Hardy."
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by JimGvo on 2008-08-05
I needed to pull an ailing ATA disk from my system so I popped it out and installed a new SATA drive.  At the same time I decided to install Hardy from a CD.  I had been running Edgy until the distros were pulled out from under me. :)  I like to do clean installs and keep the old system around until I make sure I've got everything working the way I like it.

It all went OK until I rebooted.  Grub claims to have written the MBR but instead of booting from my new partition, it booted the old version.  I could tell because the list of boot options was the old one.  I added a couple of lines to the old menu.lst file so I could boot the new system and it's happy, but I was just wondering what might have gone wrong?  

The new partition is on the third disk in the string.  There is one ATA drive and two SATA drives.  

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000855d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2433    19543041   83  Linux
/dev/sda2            2434       19457   136745280   83  Linux

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b85b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2479    19912536   83  Linux
/dev/sdb2            2480        2734     2048287+  82  Linux swap / Solaris
/dev/sdb3   *        2735        3463     5855692+  83  Linux
/dev/sdb4            3464       24792   171325192+   5  Extended
/dev/sdb5            3464        4132     5373711   83  Linux
/dev/sdb6            4133        5348     9767488+  83  Linux
/dev/sdb7            5349        5956     4883728+  83  Linux
/dev/sdb8            5957        6902     7598713+  83  Linux
/dev/sdb9            6903        7717     6546456   83  Linux
/dev/sdb10           7718       13796    48829536   83  Linux
/dev/sdb11          13797       19875    48829536   83  Linux
/dev/sdb12          19876       24792    39495771   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000f1c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        6079    48829536   83  Linux

```

I noticed that the boot flag isn't set for /dev/sdc1 which is the new Hardy root device.  If it was necessary, shouldn't the install have set it?  

It's working fine, but I've had this happen before and always wondered what causes it.

/dev/sdb3 is the partition that holds the menu.lst that is being read by grub during boots.

Thanks,
Jim.

---

### Post by Pumalite on 2008-08-05
Post:
cat /boot/grub/menu.lst

---

### Post by Pumalite on 2008-08-05
sudo mkdir /media/sdc1
sudo mount-t ext3 /dev/sdc1 /media/sdc1
cat /media/sdc1/boot/grub/menu.lst

---

### Post by JimGvo on 2008-08-05
> **Pumalite said:**
> Post:
cat /boot/grub/menu.lst


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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=3b6aaaaf-8521-4cf2-9de5-39eb0aa61b00 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title           Ubuntu 8.04.1, kernel 2.6.24-19-openvz
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-19-openvz root=UUID=3b6aaaaf-8521-4cf2-9de5-39eb0aa61b00 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-openvz
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-openvz (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-19-openvz root=UUID=3b6aaaaf-8521-4cf2-9de5-39eb0aa61b00 ro single
initrd          /boot/initrd.img-2.6.24-19-openvz

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=3b6aaaaf-8521-4cf2-9de5-39eb0aa61b00 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=3b6aaaaf-8521-4cf2-9de5-39eb0aa61b00 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu, kernel 2.6.17-10-generic (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           Ubuntu, memtest86+ (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/memtest86+.bin
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title           Ubuntu, 2.6.18-ovz028stab053.4-smp (on /dev/sdb3)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.18-ovz028stab053.4-smp root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
initrd          /boot/initrd.img-2.6.18-028stab035.1-ovz-smp
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title           Ubuntu, kernel 2.6.18-8.1.15.el5.028stab047.1 (on /dev/sdb3)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.18-8.1.15.el5.028stab047.1 root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
initrd          /boot/initrd.img-2.6.18-8.1.15.el5.028stab047.1
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title           Ubuntu, kernel 2.6.18-028test015 Default (on /dev/sdb3)
root            (hd1,2)
kernel          /boot/vmlinuz root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title           Ubuntu, kernel 2.6.18-028test015 Default (recovery mode) (on /dev/sdb3)
root            (hd1,2)
kernel          /boot/vmlinuz root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro single
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title           Ubuntu, kernel 2.6.18-028stab035.1-ovz-smp (on /dev/sdb3)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.18-028stab035.1-ovz-smp root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
initrd          /boot/initrd.img-2.6.18-028stab035.1-ovz-smp
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title           Ubuntu, kernel 2.6.18-028stab035.1-ovz-smp (recovery mode) (on /dev/sdb3)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.18-028stab035.1-ovz-smp root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro single
initrd          /boot/initrd.img-2.6.18-028stab035.1-ovz-smp
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title           Ubuntu, kernel 2.6.17-11-386 (on /dev/sdb3)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title           Ubuntu, kernel 2.6.17-11-386 (recovery mode) (on /dev/sdb3)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro single
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title           Ubuntu, kernel 2.6.16.29-xenU (on /dev/sdb3)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.16.29-xenU root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title           Ubuntu, kernel 2.6.16.29-xenU (recovery mode) (on /dev/sdb3)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.16.29-xenU root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro single
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title           Ubuntu, memtest86+ (on /dev/sdb3)
root            (hd1,2)
kernel          /boot/memtest86+.bin
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.4.27-2-386 (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.4.27-2-386 root=/dev/hde6 ro
initrd          /boot/initrd.img-2.4.27-2-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.4.27-2-386 (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.4.27-2-386 root=/dev/hde6 ro
initrd          /boot/initrd.img-2.4.27-2-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.6-xen (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6-xen root=/dev/hde6 ro
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.6-xen (recovery mode) (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6-xen root=/dev/hde6 ro single
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.6.16-xen (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.16-xen root=/dev/hde6 ro
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.6.16-xen (recovery mode) (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.16-xen root=/dev/hde6 ro single
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.6.16.29-xen (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.16.29-xen root=/dev/hde6 ro
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.6.16.29-xen (recovery mode) (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.16.29-xen root=/dev/hde6 ro single
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.6.8-3-k7 (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.8-3-k7 root=/dev/hde6 ro
initrd          /boot/initrd.img-2.6.8-3-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.6.8-3-k7 (recovery mode) (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.8-3-k7 root=/dev/hde6 ro single
initrd          /boot/initrd.img-2.6.8-3-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.6.8-3-686 (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.8-3-686 root=/dev/hde6 ro
initrd          /boot/initrd.img-2.6.8-3-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.6.8-3-686 (recovery mode) (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.8-3-686 root=/dev/hde6 ro single
initrd          /boot/initrd.img-2.6.8-3-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.4.27-2-386 (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.4.27-2-386 root=/dev/hde6 ro
initrd          /boot/initrd.img-2.4.27-2-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title           Debian GNU/Linux, kernel 2.4.27-2-386 (recovery mode) (on /dev/sdb6)
root            (hd1,5)
kernel          /boot/vmlinuz-2.4.27-2-386 root=/dev/hde6 ro single
initrd          /boot/initrd.img-2.4.27-2-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title           Debian GNU/Linux, kernel 2.6.8-2-386 (on /dev/sdb7)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.8-2-386 root=/dev/hda7 ro psmouse.proto=bare acpi=off
initrd          /boot/initrd.img-2.6.8-2-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title           Debian GNU/Linux, kernel 2.6.8-2-386 (recovery mode) (on /dev/sdb7)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.8-2-386 root=/dev/hda7 ro single
initrd          /boot/initrd.img-2.6.8-2-386
savedefault
boot

That's NOT the one that grub reads at boot.

Jim.

---

### Post by Pumalite on 2008-08-05
That's the one I want now.

---

### Post by Shazaam on 2008-08-05
Also, check the jumpers on each drive. Make the new one "Master", the old one "Slave". Check and make sure your bios is set to boot from the new drive first.

---

### Post by JimGvo on 2008-08-05
> **Shazaam said:**
> Also, check the jumpers on each drive. Make the new one "Master", the old one "Slave". Check and make sure your bios is set to boot from the new drive first.

I'm not familiar with the master/slave concept for SATA drives.  There doesn't seem to be any jumpers like there was on ATA drives.  I suppose I could swap the cables. There's no indication that  

But what I think you are saying is that I can't boot from /dev/sdc.  

That's OK, I have it working and don't want to have to start fixing menu.lst and fstab entries, which would be required if I rearranged the device order somehow.

Thanks,
Jim.

---

### Post by JimGvo on 2008-08-05
> **Pumalite said:**
> That's the one I want now.
# ********************************************************************
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
#default                3
default         1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, 2.6.18-ovz028stab053.4-smp
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.18-ovz028stab053.4-smp root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
initrd          /boot/initrd.img-2.6.18-028stab035.1-ovz-smp
savedefault
boot

title           Ubuntu 8.04.1, kernel 2.6.24-19-openvz
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-19-openvz root=UUID=3b6aaaaf-8521-4cf2-9de5-39eb0aa61b00 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-openvz
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-openvz (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-19-openvz root=UUID=3b6aaaaf-8521-4cf2-9de5-39eb0aa61b00 ro single
initrd          /boot/initrd.img-2.6.24-19-openvz

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=3b6aaaaf-8521-4cf2-9de5-39eb0aa61b00 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet


title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=3b6aaaaf-8521-4cf2-9de5-39eb0aa61b00 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet


title           Ubuntu, 2.6.18-ovz028stab053.4-smp
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.18-ovz028stab053.4-smp root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
initrd          /boot/initrd.img-2.6.18-028stab035.1-ovz-smp
savedefault
boot

title           Ubuntu, kernel 2.6.18-8.1.15.el5.028stab047.1
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.18-8.1.15.el5.028stab047.1 root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
initrd          /boot/initrd.img-2.6.18-8.1.15.el5.028stab047.1
savedefault
boot

title           Ubuntu, kernel 2.6.18-028test015 Default
root            (hd0,2)
kernel          /boot/vmlinuz root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
savedefault
boot

title           Ubuntu, kernel 2.6.18-028test015 Default (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro single
boot

title           Ubuntu, kernel 2.6.18-028stab035.1-ovz-smp
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.18-028stab035.1-ovz-smp root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
initrd          /boot/initrd.img-2.6.18-028stab035.1-ovz-smp
savedefault
boot

title           Ubuntu, kernel 2.6.18-028stab035.1-ovz-smp (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.18-028stab035.1-ovz-smp root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro single
initrd          /boot/initrd.img-2.6.18-028stab035.1-ovz-smp
boot

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro single
initrd          /boot/initrd.img-2.6.17-11-386
boot

title           Ubuntu, kernel 2.6.16.29-xenU
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.16.29-xenU root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro quiet splash
savedefault
boot

title           Ubuntu, kernel 2.6.16.29-xenU (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.16.29-xenU root=UUID=4f67dae8-cdcb-460e-86cd-a5f0e4009422 ro single
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title           Ubuntu 8.04.1, kernel 2.6.24-19-openvz
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-19-openvz root=UUID=3b6aaaaf-8521-4cf2-9de5-39eb0aa61b00 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-openvz
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-openvz (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-19-openvz root=UUID=3b6aaaaf-8521-4cf2-9de5-39eb0aa61b00 ro single
initrd          /boot/initrd.img-2.6.24-19-openvz

title           Debian GNU/Linux, kernel 2.4.27-2-386 (on /dev/hda6)
root            (hd0,5)
kernel          /boot/vmlinuz-2.4.27-2-386 root=/dev/hde6 ro
initrd          /boot/initrd.img-2.4.27-2-386
savedefault
boot

I added the 8.04.1 entries near the top.  I'm not sure where the ones at the bottom came from.

This is from the /dev/sdb3 partition.

Jim.

---

### Post by Pumalite on 2008-08-05
sudo grub
grub>
root (hd2,0)
setup (hd0)
quit

---

### Post by JimGvo on 2008-08-05
> **Pumalite said:**
> sudo grub
grub>
root (hd2,0)
setup (hd0)
quit
That worked quite well, thank you.  Now the only question is how come the install didn't do it?

Thanks,
Jim.

---

### Post by Pumalite on 2008-08-05
Because I'm better

---

