---
title: "Grub error 17"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by nuambenzina on 2008-05-27
Hello All. I just recived the Ubuntu 8.04 CD, and I wish to install it on a computer witch have 2 Hdd-`s. It`s very important that the mbr of first hardisk to be left untouched (Primary Master), (it`s an xp on it), so ubuntu and fc will go on second hdd (Primary Slave).

I installed ubuntu in the second hdd but I get an grub error 17. 


root@ubuntu:/# sudo fdisk -lu
#
 
#
Disk /dev/sda: 80.0 GB, 80026361856 bytes
#
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
#
Units = sectors of 1 * 512 = 512 bytes
#
Disk identifier: 0x5c40f1f9
#
 
#
   Device Boot      Start         End      Blocks   Id  System
#
/dev/sda1   *          63   156296384    78148161    7  HPFS/NTFS
#
 
#
Disk /dev/sdb: 41.1 GB, 41110142976 bytes
#
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
#
Units = sectors of 1 * 512 = 512 bytes
#
Disk identifier: 0xb1b8b1b8
#
 
#
   Device Boot      Start         End      Blocks   Id  System
#
/dev/sdb1   *          63      514079      257008+  83  Linux
#
/dev/sdb2          514080    40162499    19824210   83  Linux
#
/dev/sdb3        40162500    78188354    19012927+  83  Linux
#
/dev/sdb4        78188355    80292869     1052257+  82  Linux swap / Solaris
#
root@ubuntu:/#
#
 



the "/" partition is on /dev/sdb2 and the "/boot" is on /dev/sdb1




#
menu.lst - See: grub(8), info grub, update-grub(8)
#
#            grub-install(8), grub-floppy(8),
#
#            grub-md5-crypt, /usr/share/doc/grub
#
#            and /usr/share/doc/grub-doc/.
#
 
#
## default num
#
# Set the default entry to the entry number NUM. Numbering starts from 0, and
#
# the entry number 0 is the default if the command is not used.
#
#
#
# You can specify 'saved' instead of a number. In this case, the default entry
#
# is the entry saved with the command 'savedefault'.
#
# WARNING: If you are using dmraid do not use 'savedefault' or your
#
# array will desync and will not let you boot your system.
#
default         0
#
 
#
## timeout sec
#
# Set a timeout, in SEC seconds, before automatically booting the default entry
#
# (normally the first entry defined).
#
timeout         10
#
 
#
## hiddenmenu
#
# Hides the menu by default (press ESC to see the menu)
#
#hiddenmenu
#
 
#
# Pretty colours
#
#color cyan/blue white/blue
#
 
#
## password ['--md5'] passwd
#
# If used in the first section of a menu file, disable all interactive editing
#
# control (menu entry editor and command-line)  and entries protected by the
#
# command 'lock'
#
# e.g. password topsecret
#
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#
# password topsecret
#
 
#
#
#
# examples
#
#
#
# title         Windows 95/98/NT/2000
#
# root          (hd0,0)
#
# makeactive
#
# chainloader   +1
#
#
#
# title         Linux
#
# root          (hd0,1)
#
# kernel        /vmlinuz root=/dev/hda2 ro
#
#
#
 
#
#
#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
#
 
#
### BEGIN AUTOMAGIC KERNELS LIST
#
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
#
 
#
 
#
## by the debian update-grub script except for the default options below
#
 
#
## DO NOT UNCOMMENT THEM, Just edit them to your needs
#
 
#
## ## Start Default Options ##
#
## default kernel options
#
## default kernel options for automagic boot options
#
## If you want special options for specific kernels use kopt_x_y_z
#
## where x.y.z is kernel version. Minor versions can be omitted.
#
## e.g. kopt=root=/dev/hda1 ro
#
##      kopt_2_6_8=root=/dev/hdc1 ro
#
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
#
# kopt=root=UUID=f735cc43-d1a3-4d86-a309-202196168a47 ro
#
 
#
## Setup crashdump menu entries
#
## e.g. crashdump=1
#
# crashdump=0
#
 
#
## default grub root device
#
## e.g. groot=(hd0,0)
#
# groot=(hd1,0)
#
 
#
## should update-grub create alternative automagic boot options
#
## e.g. alternative=true
#
##      alternative=false
#
# alternative=true
#
 
#
## should update-grub lock alternative automagic boot options
#
## e.g. lockalternative=true
#
##      lockalternative=false
#
# lockalternative=false
#
 
#
## additional options to use with the default boot option, but not with the
#
## alternatives
#
## e.g. defoptions=vga=791 resume=/dev/hda5
#
# defoptions=quiet splash
#
 
#
## should update-grub lock old automagic boot options
#
## e.g. lockold=false
#
##      lockold=true
#
# lockold=false
#
 
#
## Xen hypervisor options to use with the default Xen boot option
#
# xenhopt=
#
 
#
## Xen Linux kernel options to use with the default Xen boot option
#
# xenkopt=console=tty0
#
## altoption boot targets option
#
## multiple altoptions lines are allowed
#
## e.g. altoptions=(extra menu suffix) extra boot options
#
##      altoptions=(recovery) single
#
# altoptions=(recovery mode) single
#
 
#
## controls how many kernels should be put into the menu.lst
#
## only counts the first occurence of a kernel, not the
#
## alternative kernel options
#
## e.g. howmany=all
#
##      howmany=7
#
# howmany=all
#
 
#
## should update-grub create memtest86 boot option
#
## e.g. memtest86=true
#
##      memtest86=false
#
# memtest86=true
#
 
#
## should update-grub adjust the value of the default booted system
#
## can be true or false
#
# updatedefaultentry=false
#
 
#
## should update-grub add savedefault to the default options
#
## can be true or false
#
# savedefault=false
#
 
#
## ## End Default Options ##
#
 
#
title           Ubuntu 8.04, kernel 2.6.24-16-generic
#
root            (hd1,0)
#
kernel          /vmlinuz-2.6.24-16-generic root=UUID=f735cc43-d1a3-4d86-a309-202196168a47 ro quiet splash
#
initrd          /initrd.img-2.6.24-16-generic
#
quiet
#
 
#
title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
#
root            (hd1,0)
#
kernel          /vmlinuz-2.6.24-16-generic root=UUID=f735cc43-d1a3-4d86-a309-202196168a47 ro single
#
initrd          /initrd.img-2.6.24-16-generic
#
 
#
title           Ubuntu 8.04, memtest86+
#
root            (hd1,0)
#
kernel          /memtest86+.bin
#
quiet
#
 
#
### END DEBIAN AUTOMAGIC KERNELS LIST
#
 
#
# This is a divider, added to separate the menu items below from the Debian
#
# ones.
#
title           Other operating systems:
#
root
#
 
#
 
#
# This entry automatically added by the Debian installer for a non-linux OS
#
# on /dev/sda1
#
title           Microsoft Windows XP Professional
#
root            (hd0,0)
#
savedefault
#
chainloader     +1
#
 
#
 
#
# This entry automatically added by the Debian installer for an existing
#
# linux installation on /dev/sdb3.
#
title           Fedora Core (2.6.9-1.667) (on /dev/sdb3)
#
root            (hd1,2)
#
kernel          /boot/vmlinuz-2.6.9-1.667 ro root=LABEL=/
#
initrd          /boot/initrd-2.6.9-1.667.img
#
savedefault
#
boot
#




/less device.map

 
#
(END) 

(hd0)   /dev/sda
(hd1)   /dev/sdb
device.map (END) 




   What shoud i do? :confused:

---

### Post by dstew on 2008-05-27
Do you get the grub error before you see the grub menu?

---

### Post by nuambenzina on 2008-05-28
No, the computer boot`s the Primary Master and the menu appear. If I select Ubuntu, Ubuntu rescue mode, Windows XP or Fedora, and press enter, the error appears.

---

### Post by dstew on 2008-05-28
At the grub menu, press 'c' to get a grub command line. On the grub command line, type this exactly:```
root (hd1,
```then hit the <TAB> key. Post the output to the forum.

---

### Post by meierfra. on 2008-05-29
At the grub menu at boot up, select "ubuntu" but do not press "enter", press "e" instead.  At the new screen, press "e" again to edit the first line.

Change "root (hd1,0)" to "root (hd0,0)".

Press "enter" and then "b". This should  boot you into Ubuntu.

Once you are in Ubuntu you need to edit "menu.lst":


```
gksudo gedit /boot/grub/menu.lst
```

Change   "#groot (hd1,0)" to "#groot(hd0,0)"

Change  "root (hd1,2)" in  the Fedora entry to "root (hd0,2)"

Change the Windows entry to

title Microsoft Windows XP Professional
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
chainloader +1


Save the file. In the terminal

```
sudo update-grub
```

and hopefully all you problems are solved.

---

### Post by nuambenzina on 2008-06-03
Sadly, I cannot reply very fast cause, I can`t reach at that specific computer every day, I took a picture of the grub menu as you can see lower. If the system will not be full reinstalled, then I`ll try gksudo gedit /boot/grub/menu.lst :)


                     I`ll post reply any way will be, Thank you

---

### Post by nuambenzina on 2008-06-03
Print Screen

---

### Post by dstew on 2008-06-03
It looks like grub can see your disk which was named /dev/sdb by the kernel of the Live CD. Grub names this disk (hd0). If you believe /boot is the first partition, then the kernel images should be in the root directory of (hd0), and the menu list file should be in the /grub directory of (hd0).

To check, get the grub command line and enter ```
kernel (hd0,0)/
```and hit tab. It should give you a list of the files in the root directory of that partition. You should see the vmlinuz kernel images, as well as the grub directory. You can check to see if the menu.lst file is there by entering the grub command```
configfile (hd0,0)/grub/
```and hit tab. If you see menu.lst there, you have found the directory. Complete the configfile command with the file name menu.lst, hit enter and the menu should pop up.

If everything works like this, you can edit the menu item by pressing 'e'. The correct Ubuntu root should be (hd0,0). If this works, you can permanently edit the menu.lst file with a text editor from the Live CD or hard disk Ubuntu system to make the change permanent.

However, since your other disk does not show up in the grub list, you might not have it connected properly. If so, when you get the other disk connected properly, the grub name will change, and you will have to go through all this again.

---

