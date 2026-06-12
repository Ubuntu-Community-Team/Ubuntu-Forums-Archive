---
title: "Can't boot after 8.04 gets updates - new kernel issue"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by jrdecastro on 2008-07-05
Motherboard Asus P4Pe
CPU P4 3Ghx
1G Ram
ATI Radeon 9600 graphics card
2x320GB disks running RAID 1 off Promise card, loaded with Win XP
1X 80Gb disk running Ubuntu connected directly to motherboard

Ubuntu 8.04 installed and ran correctly until I installed the 213 updates available. One of them changed the kernel from 2.6.24-16 to 2.6.24-19,  which now causes the system to kick out to BusyBox initamfs) prompt instead of booting. If I select the old kernel 2.6.24-16 then it works fine. What on Earth is gong on and can I continue to use the old kernel?

---

### Post by Pumalite on 2008-07-05
You can continue to use your old kernel. OTOH; maybe all you need to do with your new kernel is reinstall your video driver. Maybe Envy would help:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by jrdecastro on 2008-07-06
I presume envy would need to be run with the new kernel runnig, but I can only run the old kernel. If I try to run the new one all I get is a very unhelpful (initramfs) prompt from which I have no idea how to install envy...

On a separate Envy matter - since at least the old kernel is working, how do I set up my ATI Radeon card for dual monitors (Philips 19 inch 1440x900) side by side, one single workspace? Of course it would be best to run it on the new kernel if that problem can be easily solved...

Thanks!

James

---

### Post by shadarack on 2008-07-06
I've got pretty much the same problem.

If anyone could shed some light on this issue, that would be great! I just updated to Hardy, and due to the issues I'm having, I'm hating it very much so far...

Please help?

---

### Post by jrdecastro on 2008-07-06
Good to see I'm not alone!
Let me know if you find a solution - I'm still stuck...

---

### Post by Pumalite on 2008-07-06
Can you get to Recovery Mode?

---

### Post by shadarack on 2008-07-06
I can.

When I ran in recovery mode, it gave me a screenfull of lines about SCSI drives, which I'm pretty sure I do not have, said something about checking all media, then something else about a volume in dev not existing, then popped out to busybox.

Unfortunately, without the proper logs, I can't give more detail then that - does anyone know where I can find a log of all that nice techtext that scrolls by when the splash screen usually shows? I'd be happy to post it if I could find it...

---

### Post by Pumalite on 2008-07-06
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by tech0007 on 2008-07-06
> **shadarack said:**
> I can.

When I ran in recovery mode, it gave me a screenfull of lines about SCSI drives, which I'm pretty sure I do not have, said something about checking all media, then something else about a volume in dev not existing, then popped out to busybox.

Unfortunately, without the proper logs, I can't give more detail then that - does anyone know where I can find a log of all that nice techtext that scrolls by when the splash screen usually shows? I'd be happy to post it if I could find it...

boot recovery mode, then temporarily change your video driver to vesa in /etc/X11/xorg.conf. you can then reboot to normal and configure your X driver.

---

### Post by shadarack on 2008-07-06
sudo fdisk -lu:

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf83bf83b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    58589054    29294496   83  Linux
/dev/hda2        58589055   117226304    29318625    f  W95 Ext'd (LBA)
/dev/hda5        58589118   115234244    28322563+  86  NTFS volume set
/dev/hda6       115234308   117226304      995998+  82  Linux swap / Solaris

Disk /dev/hdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcf1fc11e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/hdc2        40981815   117210239    38114212+   f  W95 Ext'd (LBA)
/dev/hdc5        40981878    81947564    20482843+   c  W95 FAT32 (LBA)
/dev/hdc6        81947628   117210239    17631306   83  Linux

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf3fa2efa

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *       16128    81915434    40949653+  83  Linux
/dev/hdd2        81915435   156296384    37190475    f  W95 Ext'd (LBA)
/dev/hdd5        81915498   156296384    37190443+   c  W95 FAT32 (LBA)

------------------------------------------------------------------

cat /boot/grub/menu.lst:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu 8.04.1, kernel 2.6.24-19-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro single
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu 8.04.1, kernel 2.6.22-15-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-386

title		Ubuntu 8.04.1, kernel 2.6.22-15-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro single
initrd		/boot/initrd.img-2.6.22-15-386

title		Ubuntu 8.04.1, kernel 2.6.20-17-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-17-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro quiet splash
initrd		/boot/initrd.img-2.6.20-17-386

title		Ubuntu 8.04.1, kernel 2.6.20-17-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-17-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro single
initrd		/boot/initrd.img-2.6.20-17-386

title		Ubuntu 8.04.1, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu 8.04.1, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu 8.04.1, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386

title		Ubuntu 8.04.1, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro single
initrd		/boot/initrd.img-2.6.17-10-386

title		Ubuntu 8.04.1, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386

title		Ubuntu 8.04.1, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro single
initrd		/boot/initrd.img-2.6.15-27-386

title		Ubuntu 8.04.1, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu 8.04.1, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=86bd8347-9102-4366-976a-44398e314c85 ro single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
# title		Microsoft Windows XP Professional
# rootnoverify (hd0,1)
# chainloader +1

---

### Post by shadarack on 2008-07-06
You know what? I may have just found the problem myself. Reading over the result of cat etc, etc, where it says root should be? Yeah, that's the volume it was saying did not exist. I'm going to try to point that at where root is and reboot. I'll let you know how that worked when I get booted back up...

---

### Post by shadarack on 2008-07-06
Strike that, still getting the same error, only now it says volume /dev/hda1 does not exist.

---

### Post by shadarack on 2008-07-06
> **tech0007 said:**
> boot recovery mode, then temporarily change your video driver to vesa in /etc/X11/xorg.conf. you can then reboot to normal and configure your X driver.

Already running in vesa mode. Envy wants you to uninstall your drivers before you upgrade Ubuntu, so not only am I stuck using an old kernel, I'm running it in 800 x 600 vesa.

---

### Post by shadarack on 2008-07-06
Okay, I've been poking at this problem just about all day now - I hope I haven't broken some sort of netiquet rule by posting repeatedly to this thread the way I have been...

Anyways, Apparently for some reason, the combination of Ubuntu 8.04 and img-2.6.24-19-386 is not recognizing and/or cannot mount my hard drive! hd0,0 for Grub and /dev/hda1 for the Kernel. I'm not sure if it's just one or the other, but it can't see it or mount it or somesuch. Not sure exactly what the issue is.

So, does anyone have any idea how to fix this? Should I try to replace the kernel file itself? Is there some config file that needs adjustment? I am not familiar enough with Ubuntu to handle a problem of this magnitude. I really REALLY don't want to have to reinstall from scratch or go through the process of downgrading to 7.10.

Please help!

---

### Post by Pumalite on 2008-07-06
Get in Recovery Mode and do:
sudp apt-get update
sudo apt-get dist-upgrade
Better to run a .19-generic than i386.

---

### Post by jrdecastro on 2008-07-07
I am running the generic kernel and still getting the same problem, no matter what I do about graphics - I have tried the ATI proprietary and open drivers, and just a plain xorg.conf from resetting graphics. I have tried the 16, 18, and 19 kernels on exactly the same setup and the 16 works but 18 and 19 don't. If I remove the quiet splash when booting it seems to be unable to mount the / drive just before kicking out to Busybox so I suspect something in the way this particular kernel tries to mount drives is different and causes problems - maybe only with certain asus motherboards like my P4PE. 
Other people ( [http://ubuntuforums.org/archive/index.php/t-765195.html](http://ubuntuforums.org/archive/index.php/t-765195.html)  ) are also having problems with asus motherboards but unfortunately the remedy posted in that link doesn't work on mine...
My menu.lst file is pretty standard I think - let me know what to try next
Thanks!
 

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
# kopt=root=UUID=1770a691-7469-4daf-8107-d8cf8539881b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1770a691-7469-4daf-8107-d8cf8539881b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1770a691-7469-4daf-8107-d8cf8539881b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=1770a691-7469-4daf-8107-d8cf8539881b ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=1770a691-7469-4daf-8107-d8cf8539881b ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1770a691-7469-4daf-8107-d8cf8539881b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1770a691-7469-4daf-8107-d8cf8539881b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by shadarack on 2008-07-07
> **Pumalite said:**
> Get in Recovery Mode and do:
sudp apt-get update
sudo apt-get dist-upgrade
Better to run a .19-generic than i386.

Eh. Apt-get thinks I'm running the most recent kernel when I follow those instructions. 0 to download, 0 to install.

Am I doing it wrong, perhaps?

---

### Post by Kydwn on 2008-07-08
I have the same problem too (installed 19 kernel but only kernel 18 works fine)
I've tried "everything" but nothing yet...  :(

---

### Post by Wiwer on 2008-07-09
I had this same problem earlier today. When I booted up my ATI graphics card was not detected so ubuntu booted in 800x600. I was previously using the restricted ATI driver so I installed the Envy one instead, rebooted and got Busybox. I booted again in recovery mode for kernel 19, repaired damaged packages and resumed normal boot and now everything works fine.
I hope you get the same result

---

