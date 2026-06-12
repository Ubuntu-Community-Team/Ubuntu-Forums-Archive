---
title: "Recovering Grub2"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by Scholar-code on 2011-01-26
Hello all.
My system is triple boot, ubuntu 9.04, ubuntu 10.10 and win 7, recently, I got some booting issues with win 7, and as I got enough time today, I re-install win 7, as it overwrites, MBR, I did recovered the GRUB legacy, but, It doesn't contain, entry for my ubuntu 10.10. Please help me, as I do need to boot into ubuntu 10.10

Thanks in advance.
I appreciate your time.

-Scholar-code.

---

### Post by coffeecat on 2011-01-26
If you want to retain grub legacy for booting, please post the contents of your 9.04 /boot/grub/menu.lst, together with the terminal output of these two commands:

```
sudo fdisk -lu
sudo blkid
```

Please post all of those within code tags for legibility.

However, it might be easier simply to re-install grub2 to the mbr and then run 'sudo grub-update' in Ubuntu 10.10 to get all your OSs automatically added to the 10.10 grub 2 menu. Instructions here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You need a 10.10 live CD. Post back if you need any help with this.

---

### Post by Scholar-code on 2011-01-26
Thank you for your response.

Below is the output of /boot/grub/menu.lst
I did tried with fedora, and I did not like it much, I installed ubuntu 10.10 instead and I like it and kept it, but, I like mostly, ubuntu 9.04 as it is very very stable and runs like charm over my machine, so, I never mangle around with, ubuntu 9.04. 

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		05

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=63b72d80-fd99-4493-9ec2-fb8aeae6de16 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=63b72d80-fd99-4493-9ec2-fb8aeae6de16

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

title		Ubuntu 9.04, kernel 2.6.28-19-generic
uuid		63b72d80-fd99-4493-9ec2-fb8aeae6de16
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=63b72d80-fd99-4493-9ec2-fb8aeae6de16 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid		63b72d80-fd99-4493-9ec2-fb8aeae6de16
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=63b72d80-fd99-4493-9ec2-fb8aeae6de16 ro  single
initrd		/boot/initrd.img-2.6.28-19-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		63b72d80-fd99-4493-9ec2-fb8aeae6de16
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=63b72d80-#fd99-4493-9ec2-fb8aeae6de16 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		63b72d80-fd99-4493-9ec2-fb8aeae6de16
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=63b72d80-#fd99-4493-9ec2-fb8aeae6de16 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		63b72d80-fd99-4493-9ec2-fb8aeae6de16
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
#title		Fedora (2.6.33.6-147.fc13.i686) (on /dev/sda3)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.33.6-147.fc13.i686 ro root=UUID=322b417c-3648-4ec3-9240-87850b3909fb rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM #LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet 
#initrd		/boot/initramfs-2.6.33.6-147.fc13.i686.img
#savedefault

#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
#title		Fedora (2.6.33.5-124.fc13.i686) (on /dev/sda3)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.33.5-124.fc13.i686 ro #root=UUID=322b417c-3648-4ec3-9240-87850b3909fb rd_NO_LUKS rd_NO_LVM #rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 #KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet 
#initrd		/boot/initramfs-2.6.33.5-124.fc13.i686.img
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
#title		Fedora (2.6.33.3-85.fc13.i686) (on /dev/sda3)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.33.3-85.fc13.i686 ro #root=UUID=322b417c-3648-4ec3-9240-87850b3909fb rd_NO_LUKS rd_NO_LVM #rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 #KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet 
#initrd		/boot/initramfs-2.6.33.3-85.fc13.i686.img
#savedefault
#boot

```
Here is the output of the two commands.

```


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   117451214    58725576    7  HPFS/NTFS
/dev/sda2       117451215   201342644    41945715    7  HPFS/NTFS
/dev/sda4       201342974   390716864    94686945+   5  Extended
/dev/sda5       388708803   390716864     1004031   82  Linux swap / Solaris
/dev/sda6       268430211   388708739    60139264+  83  Linux
/dev/sda7       201342976   265779199    32218112   83  Linux
/dev/sda8       265781248   268429311     1324032   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2002 MB, 2002780160 bytes
62 heads, 62 sectors/track, 1017 cylinders, total 3911680 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System


****************************************************************************


/dev/sda1: UUID="B29CB36C9CB32A2D" TYPE="ntfs" 
/dev/sda2: UUID="3C1C80691C801FCE" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="9cae34fd-f386-40b4-85b9-8268f55ca1c5" 
/dev/sda6: UUID="63b72d80-fd99-4493-9ec2-fb8aeae6de16" TYPE="ext4" 
/dev/sda7: UUID="a3c373c1-d156-4cdd-9ba6-930144f19d2c" TYPE="ext4" 
/dev/sda8: TYPE="swap" UUID="2c3d1dea-044c-4c27-a40a-f660eb51d179" 
/dev/sdb: SEC_TYPE="msdos" UUID="1234-5678" TYPE="vfat" 
```

Thank you very much.

-Scholar-Code

---

### Post by coffeecat on 2011-01-26
I'm having to assume that your 10.10 is on sda7 (since 9.04 is on sda6) and that you are running the latest 2.6.35-24 kernel in Maverick. I should have asked you to run the boot script that you may have seen in other threads to be sure of this, but I'm confident my assumptions are correct.

To edit menu.lst in 9.04, open a terminal and:

```
gksudo gedit /boot/grub/menu.lst
```Now insert this stanza into the file where you want it.

```
title        Ubuntu 10.10, kernel 2.6.35-24-generic
uuid        a3c373c1-d156-4cdd-9ba6-930144f19d2c
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=a3c373c1-d156-4cdd-9ba6-930144f19d2c ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic
```You will, of course, have to edit menu.lst again if a newer kernel is released for 10.10, and if you want a menu entry for the 2.6.35-23 kernel, you'll have to adapt the above. To avoid editing your menu.lst each time there's a 10.10 kernel upgrade, you could use this stanza instead:

```
title        Ubuntu 10.10, latest kernel
uuid        a3c373c1-d156-4cdd-9ba6-930144f19d2c
kernel        /vmlinuz root=UUID=a3c373c1-d156-4cdd-9ba6-930144f19d2c ro quiet splash 
initrd        /initrd.img
```That takes advantage of the vmlinuz and initrd.img symlinks you'll find in the root of the 10.10 filesystem; they always link to the latest kernel.

Save the edited file and you should be able to boot into 10.10 when you next restart the machine.

By the way, 9.04 is now unsupported - no more updates or bugfixes. You'll have to abandon it sooner or later when you'll be better off using Maverick's grub 2. Check my earlier post for how to get that re-installed.

---

### Post by HotForLinux on 2011-02-05
No matter how much I read, I can't understand what grub-install does and I can't understand better what update-grub does or can do.

The man page for grub-install is the most ridiculous thing I have ever seen, given the number of problems and misunderstandigs people have about all this.

How can grub-install re install the MBR if the partition table has been errased?

---

### Post by coffeecat on 2011-02-05
> **HotForLinux said:**
> How can grub-install re install the MBR if the partition table has been errased?

It can't. Where in this thread does anyone say anything about the partition table being erased?

---

