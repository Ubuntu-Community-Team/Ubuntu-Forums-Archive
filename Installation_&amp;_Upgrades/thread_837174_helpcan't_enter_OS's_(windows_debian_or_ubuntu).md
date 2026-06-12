---
title: "help:can't enter OS's (windows debian or ubuntu)"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by Frantic-Atheist on 2008-06-22
hello 
lately I decided to reinstall Ubuntu 7.10 because  I was having problems with the sound and display in the newer version.

when I put the live CD this was displayed on my monitor 
[32.338492]pci:cannot allocate resource region 3 of device 0000:00:00.0
loading, please wait

[227.767655] Buffer I/O error on device fd,0 logical block 0 
[265.734519] Buffer I/O error on device fd,0 logical block 0 

and then continues regularly, then i made a partition of about 20 G.  I finished installing. when I tried to enter the Ubuntu partition it wrote

error 22: no such partition


when I tried to enter windows

error 12: invalid device requested 


and when I tried Debian

error 17: cannot mout selected partition


so I thought it my be some thing with Ubuntu so I installed Debian on the same partition and this time when I tried to enter the Debian I just installed it wrote this:

booting 'Debian GNU/Linux; kernel 2.6.18-6-686'
root (hd0,2)

error 22: no such partition

when tried to ender other Debian  

booting 'Debian GNU/Linux; kernel 2.6.18-6-686 (on /dev/sda2)'
root (hd0,1)
filesystem type unknown, partition type 0xf
kernel  /boot/vmlinuz-2.6.18-6-686 root=/dev/sdb2 ro
error 17: cannot mout selected partition

and in windows
 
booting 'Microsoft Windows XP Professional'
root (hd1,0)
filesystem type unknown, partition type 0xf
savedefult
makeactive
error 12: invalid device requested 

so my question is does he message when I entered the live CD have anything to do with this and how to fix it 
my messenger is [email]frantic.atheist@gmail.com[/email] and my icq is 472771760
thanks in advance
waiting for your response.

---

### Post by Pumalite on 2008-06-22
You are trying to boot Windows from a logical partition. Windows requires a primary partition.
Post:
sudo fdisk -lu

---

### Post by pickarooney on 2008-06-22
For the Debian bit, my guess is that your actual boot partition should be (0,0) and not (2,0). Ubuntu has screwed that up every single time I installed it. Try changing it to (0,0) either in the (I think) /boot/grub.lists file or live in the console with the E key.

---

### Post by Frantic-Atheist on 2008-06-22
> **Pumalite said:**
> You are trying to boot Windows from a logical partition. Windows requires a primary partition.
Post:
sudo fdisk -lu

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd6f861e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        41769000   260670689   109450845    f  W95 Ext'd (LBA)
/dev/sda2       260670690   312576704    25953007+  83  Linux
/dev/sda3   *          63    41768999    20884468+  83  Linux
/dev/sda5        41769063   258341264   108286101    7  HPFS/NTFS
/dev/sda6       258341328   260670689     1164681   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10401040

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    62910539    31455238+   7  HPFS/NTFS
/dev/sdb2        62910540   156232124    46660792+   f  W95 Ext'd (LBA)
/dev/sdb5        62910603   156232124    46660761    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


> **pickarooney said:**
> For the Debian bit, my guess is that your actual boot partition should be (0,0) and not (2,0). Ubuntu has screwed that up every single time I installed it. Try changing it to (0,0) either in the (I think) /boot/grub.lists file or live in the console with the E key.

I tried live with e but it did nothing

---

### Post by Pumalite on 2008-06-22
Post:
cat /boot/grub/menu.lst

---

### Post by Frantic-Atheist on 2008-06-22
> **Pumalite said:**
> Post:
cat /boot/grub/menu.lst


ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-06-22
Look in the 'boot' and 'grub' folders and tell me what you see in there. Is you are at the Live CD; you have to mount your partition first (sda3 I think)

---

### Post by Frantic-Atheist on 2008-06-22
> **Pumalite said:**
> Look in the 'boot' and 'grub' folders and tell me what you see in there. Is you are at the Live CD; you have to mount your partition first (sda3 I think)

(I am using a live CD but it was automatically mounted) 

ubuntu@ubuntu:/media/disk-2/boot/grub$ ls
default        fat_stage1_5  menu.lst~          stage1
device.map     jfs_stage1_5  minix_stage1_5     stage2
e2fs_stage1_5  menu.lst      reiserfs_stage1_5  xfs_stage1_5
ubuntu@ubuntu:/media/disk-2/boot/grub$

---

### Post by Pumalite on 2008-06-22
Do you have a menu.lst in there?; if so, copy and paste here.

---

### Post by Frantic-Atheist on 2008-06-22
> **Pumalite said:**
> Do you have a menu.lst in there?; if so, copy and paste here.


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
timeout		5

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --censored 
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
# kopt=root=/dev/sdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		Debian GNU/Linux, kernel 2.6.18-6-686
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.18-6-686 root=/dev/sdb2 ro 
initrd		/boot/initrd.img-2.6.18-6-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-6-686 (single-user mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.18-6-686 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.18-6-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-686
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sdb2 ro 
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-4-686
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.18-4-686 root=/dev/sdb2 ro 
initrd		/boot/initrd.img-2.6.18-4-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-4-686 (single-user mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.18-4-686 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.18-4-686
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Pumalite on 2008-06-22
Make Debian 'root (hd0,2)' and lets see if it boots.

---

### Post by Frantic-Atheist on 2008-06-22
> **Pumalite said:**
> Make Debian 'root (hd0,2)' and lets see if it boots.
to change all "root (hd1,1)" to "root (hd0,2)"?
how do I edit it and save?

---

### Post by Pumalite on 2008-06-22
Backup first:
sudo cp /media/disk-2/boot/grub/menu.lst /media/disk-2/boot/grub/menu.lst.old
Edit:
gksudo gedit /media/disk-2/boot/grub/menu.lst
Make changes
File>Save
Exit
Reboot.
Try Debian.

---

### Post by Frantic-Atheist on 2008-06-22
> **Pumalite said:**
> Backup first:
sudo cp /media/disk-2/boot/grub/menu.lst /media/disk-2/boot/grub/menu.lst.old
Edit:
gksudo gedit /media/disk-2/boot/grub/menu.lst
Make changes
File>Save
Exit
Reboot.
Try Debian.

still cant enter Ubuntu Debian or windows

---

### Post by Pumalite on 2008-06-22
Do you have a mix of SATA and IDE?

---

### Post by Frantic-Atheist on 2008-06-22
> **Pumalite said:**
> Do you have a mix of SATA and IDE?

both are connected by SATA but one has IDE connection 
p.s. do you think it could have any thing to do with the buffer error I get when i put the live cd? 

([227.767655] Buffer I/O error on device fd,0 logical block 0
[265.734519] Buffer I/O error on device fd,0 logical block 0 )

---

### Post by Pumalite on 2008-06-22
That's you problem. Follow this link:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by Frantic-Atheist on 2008-06-24
recently I've mad a brack throw I was able to boot to Ubuntu by changing the boot from (hd0,2) to (hd1,2) how do I make it always boot Ubuntu from (hd1,2)?

---

### Post by Pumalite on 2008-06-24
Follow my instructions in post # 13, but make root (hd1,2)

---

