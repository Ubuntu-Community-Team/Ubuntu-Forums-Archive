---
title: "[SOLVED] Installing Ubuntu can\t boot"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by Mobjerkn on 2008-10-07
Hi, Ok I decided to finally delete my Windows Vista and install ubuntu on my desktop computer. I`ve done this on my laptop and everything works fine. I'm not an expert on Linux but can usually find my way around problems. Now I'm completely stuck and need help .. 
I can't boot after installing Ubuntu, there is no dual boot but I can't reach GRUB. I've deleted everything from hard disks and installed Ubuntu and now I'm logged on through live session. I have two hard disks in a raid can this have something to do with the problem I'm experiencing?
Regards
Moo

---

### Post by Mobjerkn on 2008-10-07
When doing sudo fdisk /lu from live CD I get the following:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a18d8d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   612992204   306496071   83  Linux
/dev/sda2       612992205   625137344     6072570    5  Extended
/dev/sda5       612992268   625137344     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf358d6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   612992204   306496071   83  Linux
/dev/sdb2       612992205   625137344     6072570    5  Extended
/dev/sdb5       612992268   625137344     6072538+  82  Linux swap / Solaris

---

### Post by Mobjerkn on 2008-10-07
grub> find /boot/grub/stage1
 (hd1,0)

grub> find /grub/stage1

Error 15: File not found

grub>

---

### Post by Bucky Ball on 2008-10-07
Well, both your hard disks are saying they have ubuntu installed by the looks. sda and sdb both have swap files and a linux partition. :)

I would say you might need to unplug one of the raid drives and install ubuntu on the drive you want then make sure that is happening, then set your raid up again. Looks like the second drive in the array has backed up the first or some such as they look almost identical. I am no RAID expert so just a suggestion ...

---

### Post by Mobjerkn on 2008-10-07
Hmmf I'd might been to fast saying this is a RAID config .. sorry. I've tried a lot of different things so deleting the content of one of the hdd's could help :) I'm trying to install Grub manually :
grub> root (hd1,0)      

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 

Going to try a boot and leave this live session to se what happens :)
Moo

---

### Post by Bucky Ball on 2008-10-07
Grub is installed on your second drive:

grub> find /boot/grub/stage1
 (hd1,0)

... from your second post, so adding another may confuse the issue. Let us know how you go booting, though.

You could try downloading supergrubdisk, boot from that and see if that helps, if you have another computer to make the disk with:

[www.supergrubdisk.org]("http://www.supergrubdisk.org")

That will find what you have on there and help you work things out.

---

### Post by Mobjerkn on 2008-10-07
Reinstalled the system and ended up as following:
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a18d8d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   612992204   306496071   83  Linux
/dev/sda2       612992205   625137344     6072570    5  Extended
/dev/sda5       612992268   625137344     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf358d6e

   Device Boot      Start         End      Blocks   Id  System

---

### Post by Mobjerkn on 2008-10-07
grub> find /boot/grub/stage1

Error 15: File not found

grub> find /grub/stage1

Error 15: File not found

grub>

---

### Post by Mobjerkn on 2008-10-07
And ofc the boot doesn't work. Grub never starts after rebooting the machine.
Anyone have an idea on what to try next?
Moo

---

### Post by Bucky Ball on 2008-10-07
> **Bucky Ball said:**
> 

You could try downloading supergrubdisk, boot from that and see if that helps, if you have another computer to make the disk with:

[www.supergrubdisk.org]("http://www.supergrubdisk.org")

That will find what you have on there and help you work things out.

Error 15:

[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

You are definitely on the right track and pretty close. If you can't boot in it is pretty hard to edit the menu.lst so this is one way.

> And ofc the boot doesn't work. Grub never starts after rebooting the machine.
Anyone have an idea on what to try next?
Moo

Can you boot to the desktop? Is it just missing the grub? You can hit Ctl/Alt/F1 to drop to a shell and edit the menu.lst from there.

---

### Post by caljohnsmith on 2008-10-07
So are you sure you have your BIOS set to boot the sda drive first? Also, from your Live CD, please post the following:
```
sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo mount /dev/sda1 /mnt
ls -lR /mnt/boot
```
And we can work from there.

---

### Post by Mobjerkn on 2008-10-07
When restarting my machine I get:
Grub loading, please wait
Error 22
and then nothing happens.

Any advise would be helpful.
Moo

---

### Post by Mobjerkn on 2008-10-07
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub

GRUB 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff00                                   
0000002
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ ls -lR /mnt/boot
/mnt/boot:
total 20356
-rw-r--r-- 1 root root  422607 2008-04-10 16:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root  504774 2008-09-24 03:15 abi-2.6.27-4-generic
-rw-r--r-- 1 root root   79964 2008-04-10 16:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root   95910 2008-09-24 03:15 config-2.6.27-4-generic
drwxr-xr-x 2 root root    4096 2008-10-07 20:33 grub
-rw-r--r-- 1 root root 7349268 2008-04-22 18:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root 8333924 2008-10-07 20:33 initrd.img-2.6.27-4-generic
-rw-r--r-- 1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r-- 1 root root  899892 2008-04-10 16:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root 1041452 2008-09-24 03:15 System.map-2.6.27-4-generic
-rw-r--r-- 1 root root    1073 2008-09-24 03:17 vmcoreinfo-2.6.27-4-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 16:51 vmlinuz-2.6.24-16-generic

/mnt/boot/grub:
total 208
-rw-r--r-- 1 root root    197 2008-10-07 20:33 default
-rw-r--r-- 1 root root     30 2008-10-07 20:33 device.map
-rw-r--r-- 1 root root   8108 2008-10-07 20:33 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-10-07 20:33 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-07 20:33 installed-version
-rw-r--r-- 1 root root   8712 2008-10-07 20:33 jfs_stage1_5
-rw-r--r-- 1 root root   4399 2008-10-07 20:33 menu.lst
-rw-r--r-- 1 root root   7352 2008-10-07 20:33 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-10-07 20:33 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-10-07 20:33 stage1
-rw-r--r-- 1 root root 121500 2008-10-07 20:33 stage2
-rw-r--r-- 1 root root   9556 2008-10-07 20:33 xfs_stage1_5
ubuntu@ubuntu:~$

---

### Post by Mobjerkn on 2008-10-07
After mounting /dev/sda1 /mnt
I can do:
grub> find /boot/grub/stage1
 (hd0,0)

Should I try to restore grub from live CD?
Regards
Moo

---

### Post by caljohnsmith on 2008-10-07
Yes, go ahead and do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Post the results, and let us know what happens on start up after rebooting. I don't think it will make any difference since your Grub MBR is all ready pointing at sda1 for its files, but it's worth a try before pursuing something else yet.

---

### Post by Mobjerkn on 2008-10-07
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

---

### Post by Mobjerkn on 2008-10-07
The boot failed with Error 22 :(

---

### Post by caljohnsmith on 2008-10-07
Before we go any further, are you sure you are booting the sda drive and not the sdb drive on start up? Can you disconnect the sdb drive and then report what happens on start up?

---

### Post by Mobjerkn on 2008-10-07
I'm going to need a few min here. On thin ice not my area of expertise. Just so you know I really appreciate the help.. Going to take a quick look in the BIOS and then try to disconnect the sdb.

---

### Post by Mobjerkn on 2008-10-07
Now I get:
Kernel Panic / Not syncing / VFS unable to mount root fs on unknown/block(0,0) 
I get this after changing the boot order on my hdd's in BIOS.

---

### Post by caljohnsmith on 2008-10-07
So do you get that kernel panic error after selecting Ubuntu from the Grub menu, or does it happen before you see a Grub menu? It sounds like Ubuntu is trying to load, but there are obviously some issues. If you aren't seeing a Grub menu yet, does pressing ESC repeatedly on start up get you to the Grub menu?

---

### Post by Mobjerkn on 2008-10-07
This is before I can choose anything in GRUB. Almost like GRUB can't load.

---

### Post by caljohnsmith on 2008-10-07
Before we take any major steps, please post your menu.lst as follows:
```
sudo mount /dev/sda1 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by Mobjerkn on 2008-10-08
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
# kopt=root=UUID=76eb051a-8517-4601-a885-f30f8ec6a94c ro

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

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=76eb051a-8517-4601-a885-f30f8ec6a94c ro quiet splash 
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=76eb051a-8517-4601-a885-f30f8ec6a94c ro  single

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd0,0)
kernel		/boot/last-good-boot/vmlinuz root=UUID=76eb051a-8517-4601-a885-f30f8ec6a94c ro quiet splash  last-good-boot
quiet

title		Ubuntu intrepid (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Mobjerkn on 2008-10-08
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a18d8d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   612992204   306496071   83  Linux
/dev/sda2       612992205   625137344     6072570    5  Extended
/dev/sda5       612992268   625137344     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf358d6e

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$

---

### Post by Mobjerkn on 2008-10-08
Solved:
I've unplugged the sdb and installed ubuntu one more time. Then I pluged in the sdb to the machine and everything now works :D Thanks for all the help.
Regards
Moo

---

