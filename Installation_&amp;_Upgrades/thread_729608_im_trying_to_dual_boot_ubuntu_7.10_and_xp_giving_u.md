---
title: "im trying to dual boot ubuntu 7.10 and xp giving ubuntu my sata drive and xp my pata"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by gorillainachinashop on 2008-03-20
ive been using ubuntu for more than 3 months now, i love it, but i just built a new comp, and want to dual boot xp and ubuntu, as i did with my old comp.  i bought i sata drive and a mother board "asrock 4coredual-sata2" that supports sata2, i really want to put ubuntu on this drive(hatachi), and xp on my older pata drive(western digital), I installed xp first, then ubuntu with the live cd. but i dont get a grub menu when i boot, it just says windows didnt start properly, and gives me the option to boot windows in safe or normal mode.  do i need to manually install grub? how do i do that? i was also wondering if ubuntu supports pent. dual core processors? please help, i miss my ubuntu

---

### Post by confused57 on 2008-03-20
> **gorillainachinashop said:**
> ive been using ubuntu for more than 3 months now, i love it, but i just built a new comp, and want to dual boot xp and ubuntu, as i did with my old comp.  i bought i sata drive and a mother board "asrock 4coredual-sata2" that supports sata2, i really want to put ubuntu on this drive(hatachi), and xp on my older pata drive(western digital), I installed xp first, then ubuntu with the live cd. but i dont get a grub menu when i boot, it just says windows didnt start properly, and gives me the option to boot windows in safe or normal mode.  do i need to manually install grub? how do i do that? i was also wondering if ubuntu supports pent. dual core processors? please help, i miss my ubuntu
Have you tried booting first to your other hard drive?

You could try booting the live cd, open a terminal and post the output of:
```
sudo fdisk -l
```
-l is a small "L"

You can use the live cd to mount your root partition:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/xxx /media/ubuntu
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/boot/grub/device.map
```
substitute your root partition for /dev/xxx

You could try reinstalling grub with the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
but it might be best to post the output of "fdisk -l" and your menu.lst & device.map first.

---

### Post by waylandbill on 2008-03-20
If you want grub to be booted, you need to 'grub-install' to the drive that the bios boots from. If this is the PATA drive, then you need to install grub to that. Booting from the PATA drive may be simpler because Windows expects to boot from C: unless you modify the boot.ini, which you would have to do if you boot from grub on the SATA drive.

---

### Post by Bucky Ball on 2008-03-20
Try this ...

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

Burn a copy to CD or dongle, reboot using that and see if you can't fix it up. There is excellent documentation on the website also to help you through. It should identify both operating system boot requirements and then ask you to reboot after a few questions. Good luck ...

---

### Post by gorillainachinashop on 2008-03-20
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c0466

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05d1e78c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19456   156280288+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

ive been trying to burn and supergrub iso, but i havent been able to boot from them im also quit a noob, ive tried to boot from the sata drive, but i get nothing but a blinking line, how do you install grub? when i do find out where the boot file is?

---

### Post by Bucky Ball on 2008-03-20
But how silly of me; I should have said to check this:

[http://ubuntuforums.org/showthread.php?t=710803](http://ubuntuforums.org/showthread.php?t=710803)

(Thanks Herman for the post and Adrian15)

---

### Post by gorillainachinashop on 2008-03-20
im having trouble figuring out wich distro of super grub to down load, and what files to burn to iso. i down loaded a program to burn iso in windows, but my comp wont load from the disks i burn, maybe i messing up the order the files should be in?, im at a loss here, thank you so much for helping guys, i wouldnt mind putting grup from the live disk where it needs to be or mod. window files, these installs are new and clean, nothing im to worried about loosing

---

### Post by gorillainachinashop on 2008-03-20
also how do you officially thank some one in the forums?

---

### Post by gorillainachinashop on 2008-03-20
i got super grub working, but when i tried booting into ubuntu i got this response "file system type unknown, partition type 0x7, kernal/ boot/vm/inuz-2.6.22-14-generic root=uuid= e694do8a-4aca-bcfc-60c86 ecof7a4 no quiet splash

error 17: cannot mount selected partition

i read some forums and changed my hd devices to auto in bios, i reinstalled ubuntu from a diff disk, now grub loads, but i cant load xp with out the supergrub disk, and i cannot load ubuntu

---

### Post by confused57 on 2008-03-20
> **gorillainachinashop said:**
> i got super grub working, but when i tried booting into ubuntu i got this response "file system type unknown, partition type 0x7, kernal/ boot/vm/inuz-2.6.22-14-generic root=uuid= e694do8a-4aca-bcfc-60c86 ecof7a4 no quiet splash

error 17: cannot mount selected partition

i read some forums and changed my hd devices to auto in bios, i reinstalled ubuntu from a diff disk, now grub loads, but i cant load xp with out the supergrub disk, and i cannot load ubuntu
If you can boot into Ubuntu, post the output of:
```
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```
this may show how your devices are recognized by grub...

Added:  Sorry, just noticed you can't boot Ubuntu...boot the live cd, then mount your root partition from a terminal:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/boot/grub/device.map
```

You could also try using SGD to restore your Windows IPL(Initial Program Loader) to boot Windows without using SGD, boot SGD:
1.) Super Grub Disk (No Help)
2.) English SGD
3.) Windows
4.) Fix Boot of Windows

I'm not sure what's going on...was the PATA drive set to boot first in bios when you installed Windows & Ubuntu?  If so, you could try using SGD to install Windows IPL to the mbr, then see if Windows boots OK using it's own bootloader.  Then set your SATA drive as the first boot device in bios, reinstall Ubuntu...make sure to install grub to the SATA drive's mbr by clicking the "Advanced" button & changing the location to install grub to /dev/sda(instead of the default hd0).   When there is a mix of IDE & SATA drives, grub seems to install to the mbr of the IDE drive even if the SATA drive is first in the boot sequence.

---

### Post by gorillainachinashop on 2008-03-20
menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		10

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
# kopt=root=UUID=3ba27032-2a87-4564-b677-ae10cb18c46a ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=U

im going to try reinstalling and changing where grub is i do believe it has been installed on the ide drive

---

### Post by confused57 on 2008-03-20
> im going to try reinstalling and changing where grub is i do believe it has been installed on the ide drive
That's what I thought may have happened, your menu.lst pretty much confirms that. If Ubuntu still doesn't boot and you get a grub boot menu when you boot first to your SATA drive...make sure your first Ubuntu is highlighted, press "e" to edit, then select the line with root, press "e" again, change root from (hd2,0) to (hd0,0), press "enter" then "b" to boot.
This is temporary, but you can make it permanent if it works:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by gorillainachinashop on 2008-03-21
ok, that worked i can boot into ubuntu now, had to change some hardware settings, and reinstall windows and ubuntu, and setting grub on the right hdd, but now i can't boot windows, i get a grub error and it says device dose not exist.  im going to post my results for "sudo fdisk -l" because it has changed.  if you can help please please dodaniel@daniel-desktop:~$ sudo fdisk -l
[sudo] password for daniel:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c0466

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05d1e78c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4865    39078081    7  HPFS/NTFS

---

### Post by confused57 on 2008-03-21
Please post your Ubuntu & Windows boot entries in your /boot/grub/menu.lst and also your /boot/grub/device.map.  One of these Windows entries may work:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

```
title              Windows XP
root               (hd2,0)
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1
```

To edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```


Does Windows boot if you boot first to the drive it's on?  Are your PATA drives set the "Auto" in bios?

---

