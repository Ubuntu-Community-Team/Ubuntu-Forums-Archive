---
title: "Bypassing GRUB"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by rmcellig on 2008-10-29
I successfully installed Ubuntu 8.04 in one of my PC's. I decided to remove the drive and then put it in my other PC. When I start up I get a GRUB loading Error 2 message. This drive is partitioned. One partition has XP Pro and the other, 8.04. What should I do so that I can get back to normal?

---

### Post by caljohnsmith on 2008-10-29
Are you getting the Grub error 2 before seeing the Grub menu (or seeing the text "Press ESC to see menu"), or after you get the Grub menu and select an OS?

How about booting your Live CD, open a terminal, and posting:
```
sudo fdisk -lu
```
Figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Also, follow these steps to ensure that Grub is properly installed to the MBR (Master Boot Record) of your Ubuntu drive:
```
sudo grub
grub> find /boot/grub/stage1

```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands.

---

### Post by rmcellig on 2008-10-29
Thanks for your help.

So this is the easiest way for me to get back up and running without having to delete the Ubuntu partition and starting over again?

---

### Post by rmcellig on 2008-10-29
[QUOTE=caljohnsmith;6056718]Are you getting the Grub error 2 before seeing the Grub menu (or seeing the text "Press ESC to see menu"), or after you get the Grub menu and select an OS?

I am seeing the GRUB error 2 before I see the Grub menu.

---

### Post by rmcellig on 2008-10-29
What am I doing wrong here. I am trying to follow your instructions but I think I may have a syntax error or something similar:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd3dbd3db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195318269    97659103+   7  HPFS/NTFS
/dev/sda2       195318270   781417664   293049697+   5  Extended
/dev/sda5       195318333   778397444   291539556   83  Linux
/dev/sda6       778397508   781417664     1510078+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda5/mnt
mount: can't find /dev/sda5/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount/dev/sda5/mnt
sudo: mount/dev/sda5/mnt: command not found
ubuntu@ubuntu:~$ sudo mount/dev/sda5/mnt
sudo: mount/dev/sda5/mnt: command not found
ubuntu@ubuntu:~$ sudo mount/dev/sda5/ mnt
sudo: mount/dev/sda5/: command not found
ubuntu@ubuntu:~$

---

### Post by rmcellig on 2008-10-29
As requested, here are the results after running the commands suggested above in the previous post. Where do I go from here?

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd3dbd3db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   775361159   387680548+  83  Linux
/dev/sda2       775361160   781417664     3028252+   5  Extended
/dev/sda5       775361223   781417664     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sdXY /mnt
mount: special device /dev/sdXY does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=UUID=c5a87fe5-4170-4684-bb19-6447bc6cc77f ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c5a87fe5-4170-4684-bb19-6447bc6cc77f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c5a87fe5-4170-4684-bb19-6447bc6cc77f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ 
     


 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors aresucceeded.
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/boot/grub/menu.lst"... succeeded
Done.

grub>

---

### Post by rmcellig on 2008-10-29
I just removed the drive from my Dell 4500S machine and put it in my other PC. Works fine!

I want Ubuntu to work in my Dell 4500S though. What should I do? I even tried the Ubuntu alternate CD and still had the same GRUB error described above.

---

