---
title: "Ubuntu 8.04 won't boot from USB hard disk"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by Borange on 2008-05-08
I downloaded Ubuntu 8.04 LTS and burned it to a cd. I used HashCalc to check the iso file. Also, the self check option after booting to the cd shows the disk is OK. I installed Ubuntu on an external hard drive. The partitioner and installer recognized the external hard drive and Ubuntu appeared to install OK. After installation is done the computer reboots and says Starting Up.... and then it stops. Grub works. I can shoose the regular boot or recovery but the boot process freezes after Starting Up.

The hard disk is a 10.2 GB Maxtor 91020D6. The USB to ATA enclosure is by ADS and has a GL811E chipset (Genesys Logic). According to Device Manager in Windows I have an Intel 82801FB/FBM USB 2.0 controller on an Albatron PX915 motherboard (terrible onboard sound) with an Intel 915P chipset. Also the board has an ITE IT8212 RAID controller but I don't think it is involved in this problem. Gigabyte 6600GT for video. At the computer's POST I see the Maxtor drive listed as a USB device.

How do I get Ubuntu to boot from the external drive?

---

### Post by Pumalite on 2008-05-08
Boot your Live CD and post:
sudo fdisk -l

---

### Post by Borange on 2008-05-09
Disk /dev/sda: 10.2 GB, 10200637440 bytes
255 heads, 63 sectors/track, 1240 cylinders
Unit = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae662037

___Device__Boot__Start___End_____Blocks__Id__System
/dev/sda1____*______1__1181__9486351__83__Linux
/dev/sda2________1182__1240___473917+__5__Extended
/dev/sda5________1182__1240___473886__82__Linux swap/Solaris

---

### Post by Pumalite on 2008-05-09
Is this from your hard drive?. If not; plug it in.

---

### Post by Borange on 2008-05-09
Yup, that's the USB connected hard disk. When I ran sudo fdisk -l that was the only hard disk connected to the computer. When I installed Ubuntu it was the only hard disk connected to the computer because I wanted to avoid puting GRUB on the Windows hard disk.

---

### Post by Pumalite on 2008-05-09
Ok. Post:
cat /boot/grub/menu.lst (from sda1)

---

### Post by Borange on 2008-05-09
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   16M  490M   4% /lib/modules/2.6.24-16-generic/volatile
tmpfs                 506M   16M  490M   4% /lib/modules/2.6.24-16-generic/volatile
varrun                506M  100K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   64K  505M   1% /dev
devshm                506M   12K  505M   1% /dev/shm
tmpfs                 506M   16K  505M   1% /tmp
gvfs-fuse-daemon      506M   23M  483M   5% /home/ubuntu/.gvfs
/dev/sda1             9.0G  2.1G  6.5G  25% /media/disk
ubuntu@ubuntu:~$ cd /media/disk
ubuntu@ubuntu:/media/disk$ cd boot/grub
ubuntu@ubuntu:/media/disk/boot/grub$ cat menu.lst
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
# kopt=root=UUID=2cc18525-e53e-4986-87cf-8ffa03f45a95 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2cc18525-e53e-4986-87cf-8ffa03f45a95 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2cc18525-e53e-4986-87cf-8ffa03f45a95 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:/media/disk/boot/grub$

---

### Post by Pumalite on 2008-05-09
Have you gone to BIOS to make USB first boot?

---

### Post by Borange on 2008-05-09
It isn't set to first boot. I think, at the moment, it is set to boot floppy, cd, usb, internal hard disk. The Maxtor disk is visible in the boot menu of the BIOS. It was booting and going as far as GRUB but after the words Starting Up... it freezes.

Thank you for your assistance with this. I will be back on the forums later.

---

### Post by Borange on 2008-05-09
I tried installing Ubuntu to the external hard disk from Ubuntu- after selecting the live cd option, starting Ubuntu, and clicking the install icon on the desktop. Also, I tried manually setting the partitions during the install process. It continues to freeze after the words Starting up...

---

### Post by Pumalite on 2008-05-09
Edit menu.lst and try root (hd0,3)or (hd0,2) or (hd0,1)

---

### Post by Borange on 2008-05-09
I'm guessing the part I should edit is at the end of menu.lst. Everything else appears to be comments. I changed three  of the root (hd0,0) to root (hd0,1)

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=41576919-5bb8-4294-b1bd-de5531cbb2cf ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=41576919-5bb8-4294-b1bd-de5531cbb2cf ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

I will reply soon with results...

---

### Post by Borange on 2008-05-09
Error 17: Cannot mount selected partition
Press any key to continue...

I pressed a key and was taken to the grub menu. I selected the first option, Ubuntu 8.04, kernel 2.6.24-16 generic. Again I saw Error 17. The Memtest option does not work either. Selecting Memtest also produces Error 17. Earlier, with hd0,0 in menu.lst, Memtest did work.

---

### Post by Borange on 2008-05-11
I tried a few more things.

I tried installing Ubuntu 7.10 I saw the same problem that I saw with 8.04 The computer freezes after the words Starting up... I tried 7.10 with the onboard IT8212 RAID disabled in the BIOS. Also I tried Fedora 7. I saw a similar problem. The computer froze near the beginning of the boot process.

Booting 'Fedora (2.6.21-1.2194.fc7)'
root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
Kernel /vmlinuz-2.6.21-1.3194.fc7 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
 [Linux-gzImage, setup=0x1e00, size=0x1c9dd4]
initrd /initrd-2.6.21-1.3194.fc7.img
 [Linux-initrd @ 0x37c84000, 0x36bbc6 bytes]

That is where it stopped.

I looked up initrd. It is for starting a ram drive. I thought a ram drive was used for booting the live cd, too. I'm guessing Ubuntu and Fedora both use ram drives. I haven't done anything odd to my ram. It is 1 GB of Corsair PC-3200.

I took the hard drive out of the external enclosure and put it in the computer. I put it on the IDE cable controlled by the IT8212 (enabled in the BIOS) with the Windows hd disconnected and the Linux hd set as cable select. I tried to install Ubuntu 8.04 but I couldn't get past partitioning and saw the following error:

Failed to create a swap space
The creation of swap space in partition #5
of SCSI1 (0,1,0) (sda) failed.

I give up. I wish my eMachines motherboard was still working. Say what you want about the brand but the mobo ran Linux with no problems.

---

### Post by Pumalite on 2008-05-11
You might want to read this:
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)

---

