---
title: "Windows doesn't boot"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by medico1849 on 2007-02-09
I've installed Ubuntu 6.10 on a second HDD (IDE) after a clean XP Pro install (on the SATA drive). I can boot up to Ubuntu perfectly fine, but when I enter GRUB to boot to a different drive, Windows is not shown. :-k

System Specs
ECS nForce 570 SLI motherboard
Pentium D 2.8Ghz
1 IDE drive - Ubuntu
1 Sata drive - XP Pro
Nvidia Geforce 6600 GT

---

### Post by medico1849 on 2007-02-09
This is my menu.lst

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
# kopt=root=UUID=68c55394-7f1e-42a8-a464-186da151495e ro
# kopt_2_6=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by mikewhatever on 2007-02-09
Hi medico,
can you please post the output of > sudo fdisk -lu
It looks like Ubuntu is on the fist HD, according to the GRUB menu.

Thought I'd edit it a bit. 
There is a [similar problem](http://ubuntuforums.org/showthread.php?t=342663) in another thread. It seems that as BIOS sees it, the IDE drive with Ubuntu on it is hd0 (hd0,0), and the SATA drive with windows is hd1 (hd1,0). Under this kind of setup, you'd need to add the following to the end of the menu:
> 
title      Microsoft Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
makeactive
chainloader +1


---

### Post by medico1849 on 2007-02-09
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    26619704    13309821    7  HPFS/NTFS
/dev/sda2        26619705   488375999   230878147+   f  W95 Ext'd (LBA)
/dev/sda5        26619768   257023934   115202083+   7  HPFS/NTFS
/dev/sda6       257023998   488375999   115676001    7  HPFS/NTFS

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   482335559   241167748+  83  Linux
/dev/hda2       482335560   488392064     3028252+   5  Extended
/dev/hda5       482335623   488392064     3028221   82  Linux swap / Solaris

---

### Post by mikewhatever on 2007-02-09
Check the edited post above :)

---

### Post by medico1849 on 2007-02-09
Sorry this is probably pretty simple, but it's not letting me save the file. I've only been using Ubuntu for a day...

---

### Post by medico1849 on 2007-02-09
Nvm, I had to open it from terminal.

---

### Post by medico1849 on 2007-02-09
I get an error when trying to boot to windows. Something about NTLDR is missing.

---

### Post by mikewhatever on 2007-02-09
Try looking for NTLDR with
> grub>  find /ntldr
you can get to command line from GRUB menu by pressing 'c'.
There is a good [GRUB GUIDE](http://users.bigpond.net.au/hermanzone/p15.htm) to have around.

---

### Post by medico1849 on 2007-02-09
That command never does anything, it just stays blinking at the line "This may take a long time."  I've looked, with the windows install cd, for a boot record, but I couldn't find one. I used the bootcfg command with each option, to no avail (/default, etc). Although, I didn't try restoring the boot loader b/c it said it would mess with the partitions. Shouldn't a command like fdisk /mbr put a new boot record at the beginning of the drive (which is where windows is installed).

Any help?

---

### Post by Herman on 2007-02-09
Excuse me for butting in here, but often when IDE and SATA drives are plugged in to the same motherboard it causes a little confusion between the BIOS, the operating systems and Grub as to which hard disk will be called number 1
.
Normally, the BIOS counts SCSI, (and SATA), disk first.

In you case, it looks like, (from your fdisk output and also from your menu.lst file, like Ubuntu and grub have set things up as if your IDE disk is number1 and your SATA disk is number2.

That's not how I would have expected it to be. So which hard disk's MBR would you be booting from? You SATA disk I would normally think. Would they be set up in CMOS (BIOS) that way?
So looks a little upside down and backwards at the moment to me. But don't worry, it might take a little fiddling around, but we should be able to help you get it sorted out.

First, can you show us your /boot/grub/device.map file please? Here is a link that will explain what I am getting at, [**Editing Grub's device.map**]("http://users.bigpond.net.au/hermanzone/p15.htm#device.map")
That might go a long way towards solving your problem.

I would postpone performing any operations at all on your Windows partition, or with any Windows Disk, as neither Grub nor Ubuntu would touch any part of your Windows filesystem. Anything you might do there could possibly just further complicate matters. Grub couldn't detect your boot.ini file because your Windows is on an NTFS filesystem, which grub can't stand the taste of. :) All grub does with Windows is relay the message to boot up to the Windows bootloader, and then NTLDR one takes over. ('Chainloading').  Your NTLDR file will be there all right. It's just that at the moment we are looking on the wrong disk for it I suspect.
That's all for now, I'll be lurking around to see how you go.
Regards, Herman :)

---

### Post by Herman on 2007-02-09
Hello again medico1849,
If you start feeling stressed and worried, or impatient and you have important work you need to get done in a hurry, you can always boot with a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") for now.

Regards, Herman

---

