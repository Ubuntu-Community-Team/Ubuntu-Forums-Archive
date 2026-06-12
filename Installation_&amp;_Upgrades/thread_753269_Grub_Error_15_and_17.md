---
title: "Grub Error 15 and 17"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by ikedaman on 2008-04-12
Up until yesterday, when I tried to partition an external hard drive, I had a triple boot system that was working perfectly.  

I have:
Linux Studio 64
Ubunu 64 7.10
Windows XP

I wanted to partition my new external into thirds so that all of my operating systems would have some of their own space on it.  I tried to partition with gparted in Ubuntu, but it would not write an ntfs partition, so I loaded up Windows and used Power Quest Partion Magic 8 to do it instead.  It prompted me for a reboot to complete the partitioning, so I did.  GRUB would not appear so after booting from the live cd, I solved that with this code in terminal:

```
sudo grub
find /boot/grub/stage 1
root (hd0,5)
setup (hd0)
quit

```

That solved the grub problem and windows can even load off the hard drive.  When I tried to start up Studio 64 in GRUB, however, I get the **Grub Error 15: File Not Found**.  When I try to start up Ubuntu, I get **Grub Error 17: cannot mount selected partition**.  I've tried **Super Grub Disk**, and a multitude of other forum solutions that I have found, but ultimately they did nothing or brought me back a step, causing me to input the above code from the live cd multiple times.

Oddly enough, while taking a break from my frustration with Grub, I was able to successfully partition my external hard drive using the live cd gparted which I guess would have saved me from all of these issues.

I believe my operating systems are somewhere on my internal hard drive intact, but I need GRUB to recognize them.  Since I have been trying to get this back to normal, I have kept my external off to keep that variable out of the equation.

Please help, my desk is becoming swamped in useless codes that I have printed and tried.

---

### Post by Pumalite on 2008-04-12
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by ikedaman on 2008-04-12
```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390   273538754   136721182+   7  HPFS/NTFS
/dev/sda3       481741155   488279609     3269227+  db  CP/M / CTOS / ...
/dev/sda4       273538755   481741154   104101200    f  W95 Ext'd (LBA)
/dev/sda5       273538818   277442549     1951866   82  Linux swap / Solaris
/dev/sda6   *   277442613   367069184    44813286   83  Linux
/dev/sda7       367069248   370989044     1959898+  82  Linux swap / Solaris
/dev/sda8       370989108   379342844     4176868+  83  Linux
/dev/sda9       379342908   481741154    51199123+  83  Linux

```

---

### Post by Pumalite on 2008-04-12
Who is supposed to own the Grub and what partition does it occupy?

---

### Post by ikedaman on 2008-04-12
Windows was the original install, but grub in the state it is in now came with 64 studio

GRUB is in SDA6

is that what you need?

---

### Post by Pumalite on 2008-04-12
Mount your partition:
sudo mkdir /media/sda6
sudo mount -t ext3 dev/sda6 /media/sda6
Post:
cat /media/sda6/boot/grub/menu.lst

---

### Post by ikedaman on 2008-04-12
ubuntu@ubuntu:~$ sudo mkdir /media/sda6
ubuntu@ubuntu:~$ sudo mkdir /media/sda6
mkdir: cannot create directory `/media/sda6': File exists
ubuntu@ubuntu:~$ sudo mount -t ext3 dev/sda6 /media/ada6
mount: mount point /media/ada6 does not exist
ubuntu@ubuntu:~$ cat /media/ada6/boot/grub/menu.lst
cat: /media/ada6/boot/grub/menu.lst: No such file or directory

---

### Post by Pumalite on 2008-04-12
Typo, ada6

---

### Post by ikedaman on 2008-04-12
```
ubuntu@ubuntu:~$ sudo mkdir /media/ada6
ubuntu@ubuntu:~$ sudo mount -t ext3 dev/ada6 /media/ada6
mount: special device dev/ada6 does not exist
ubuntu@ubuntu:~$ cat /media/ada6/boot/grub/menu.lst
cat: /media/ada6/boot/grub/menu.lst: No such file or directory

```

Thanks for the help.

---

### Post by Pumalite on 2008-04-12
change ada6 to sda6

---

### Post by ikedaman on 2008-04-12
```
ubuntu@ubuntu:~$ sudo mkdir /media/sda6
mkdir: cannot create directory `/media/sda6': File exists
ubuntu@ubuntu:~$ sudo mount -t ext3 dev/sda6 /media/sda6
mount: special device dev/sda6 does not exist
ubuntu@ubuntu:~$ cat /media/sda6/boot/grub/menu.lst
cat: /media/sda6/boot/grub/menu.lst: No such file or directory
```

Am I doing something wrong?  Could it be in a different partition?

---

### Post by Pumalite on 2008-04-12
You missed / before dev.

---

### Post by ikedaman on 2008-04-12
ugh...embarrassing.

```
ubuntu@ubuntu:~$ cat /media/sda6/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda8 ro vga=791 splash=silent

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title           64 Studio, kernel 2.6.21-1-multimedia-amd64
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/sda8 ro vga=791 splash=silent 
initrd          /boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault

title           64 Studio, kernel 2.6.21-1-multimedia-amd64 (single-user mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/sda8 ro vga=791 splash=silent single
initrd          /boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda7)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=160a0753-45ef-4a24-b966-89462238b70c ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda7)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=160a0753-45ef-4a24-b966-89462238b70c ro single 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title           Ubuntu 7.10, memtest86+ (on /dev/sda7)
root            (hd0,6)
kernel          /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

Thanks for your patience.

---

### Post by Pumalite on 2008-04-12
first backup your file:
sudo cp /media/sda6/boot/grub/menu.lst /media/sda6/boot/grub/menu.lst.old
I think you have gedit (not sure):
gksudo gedit /media/sda6/boot/grub/menu.lst
Change the root line of studio to (h0,5)
save, exit, reboot.

---

### Post by ikedaman on 2008-04-12
Getting Closer.  Studio 64 loading screen came up and was loading when:

```
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-4) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)

```

Ubuntu hasn't changed.

---

### Post by Pumalite on 2008-04-12
You mean you can get into Ubuntu?

---

### Post by ikedaman on 2008-04-12
no, still has error 17

---

### Post by Pumalite on 2008-04-12
What's Ubuntu's partition?

---

### Post by ikedaman on 2008-04-12
sda9 -according to gparted

---

### Post by Pumalite on 2008-04-12
Your menu.lst says you have 7.10 in sda7. Do you have something there?

---

### Post by ikedaman on 2008-04-12
gparted from the ubuntu live cd says that sda7 is linux-swap 1.87GB
[IMG]http://photos-f.ak.facebook.com/photos-ak-sf2p/v239/101/113/82300105/n82300105_30327941_1297.jpg[/IMG]

---

### Post by Pumalite on 2008-04-12
OK. Edit menu.lst again and this time change Ubuntu 7.10 root line to (to avoid smileys I have to tell you achedezerocomaeight)

---

### Post by ikedaman on 2008-04-12
menu.lst comes up empty. Where did I go wrong?

---

### Post by Pumalite on 2008-04-12
sudo cp /media/sda6/boot/grub/menu.lst.old /media/sda6/menu.lst
gksudo /media/sda6/boot/grub/menu.lst
Post the output.

---

### Post by ikedaman on 2008-04-12
```
ubuntu@ubuntu:~$ sudo cp /media/sda6/boot/grub/menu.lst.old /media/sda6/menu.lst
cp: cannot stat `/media/sda6/boot/grub/menu.lst.old': No such file or directory
ubuntu@ubuntu:~$ gksudo /media/sda6/boot/grub/menu.lst
ubuntu@ubuntu:~$ 

```

I'm using the Live CD again

---

### Post by Pumalite on 2008-04-12
Typo:
sudo cp /media/sda6/boot/grub/menu.lst.old /media/sda6/boot/grub/menu.lst
Copy and paste in Terminal
gksudo /media/sda6/boot/grub/menu.lst
Copy and paste in Terminal
Post the output.

---

### Post by ikedaman on 2008-04-12
still
```
ubuntu@ubuntu:~$ sudo cp /media/sda6/boot/grub/menu.lst.old /media/sda6/boot/grub/menu.lst
cp: cannot stat `/media/sda6/boot/grub/menu.lst.old': No such file or directory
ubuntu@ubuntu:~$ gksudo /media/sda6/boot/grub/menu.lst
ubuntu@ubuntu:~$ 

```

---

### Post by Pumalite on 2008-04-12
Is sda6 still in /media/sda6?

---

### Post by ikedaman on 2008-04-12
no, it was in /media/disk for some reason.  I edited it and am now posting from ubuntu, so thank you for that.  I still can't get into 64 studio, though.

---

### Post by Pumalite on 2008-04-12
Post your new menu.lst

---

### Post by ikedaman on 2008-04-13
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 	5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda8 ro vga=791 splash=silent

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		64 Studio, kernel 2.6.21-1-multimedia-amd64
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/sda8 ro vga=791 splash=silent 
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault

title		64 Studio, kernel 2.6.21-1-multimedia-amd64 (single-user mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/sda8 ro vga=791 splash=silent single
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda7)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=160a0753-45ef-4a24-b966-89462238b70c ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=160a0753-45ef-4a24-b966-89462238b70c ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 7.10, memtest86+ (on /dev/sda7)
root		(hd0,6)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by Pumalite on 2008-04-13
Edit your menu.lst and make sure the 'root' line is the same in all entries of studio and do the same with 7.10. Post the results.

---

### Post by ikedaman on 2008-04-13
menu.lst:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 	5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda8 ro vga=791 splash=silent

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		64 Studio, kernel 2.6.21-1-multimedia-amd64
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/sda8 ro vga=791 splash=silent 
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault

title		64 Studio, kernel 2.6.21-1-multimedia-amd64 (single-user mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.21-1-multimedia-amd64 root=/dev/sda8 ro vga=791 splash=silent single
initrd		/boot/initrd.img-2.6.21-1-multimedia-amd64
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda7)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=160a0753-45ef-4a24-b966-89462238b70c ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda7)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=160a0753-45ef-4a24-b966-89462238b70c ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 7.10, memtest86+ (on /dev/sda7)
root		(hd0,8)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

64 studio still gives me:

```
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-4) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)
```

---

### Post by Pumalite on 2008-04-13
Studio is corrupted then. Save data and home and reinstall

---

### Post by ikedaman on 2008-04-13
thanks for your help.

---

### Post by Pumalite on 2008-04-13
You are welcome. Good luck.

---

