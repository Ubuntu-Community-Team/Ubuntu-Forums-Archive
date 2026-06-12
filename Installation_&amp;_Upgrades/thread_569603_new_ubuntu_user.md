---
title: "new ubuntu user"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by sandysandy on 2007-10-07
Hi everyone! i am a new convert to Ubuntu and have installed 7.04. however i am unable to boot from hard disk. there are other threads on this subject but are way above an absolute novice like me. Kindly help.

Thanx:)

---

### Post by Pumalite on 2007-10-07
Hi: welcome to ubuntuforums. Start by posting specs and what you used to install

---

### Post by sandysandy on 2007-10-07
the specs of my machine are Intel Pentium D processor. 1GB RAM, 2 HDD ( 160GB & 40GB).
the 160gb HDD had windows XP.
i downloaded ubuntu from web and burnt the iso image on CD. 
i booted with the Ubuntu CD and then used the install option.
first i installed on the second HDD of 40 GB. 
however was unable to boot linux inspite of changing boot priority to 40 gb hdd. only win xp booted.
next i used last partition on 160 gb hdd for installing ubuntu ( install done using auto option, 53% of hdd used for install, rest used by linux cd to create swap etc)
after this the omputer is not booting from either hdd.
i am presntly booted from ubuntu bootable cd.

---

### Post by Pumalite on 2007-10-07
You need to follow these guides:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
(burn at 4x, definitely do md5sum on iso)
Post:
sudo fdisk -lu

---

### Post by sandysandy on 2007-10-07
i think the burning is ok as i am able to boot from the burnt ubuntu CD. i am getting the desktop and can browse files etc. the problem is that i am not able to boot from hard disk. is any change required to menu.lst. the present menu.lst is as follows( quite long)

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
# kopt=root=UUID=254e52d1-f0f8-4f7c-ad23-e2c412bb280b ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=254e52d1-f0f8-4f7c-ad23-e2c412bb280b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=254e52d1-f0f8-4f7c-ad23-e2c412bb280b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
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
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Pumalite on 2007-10-07
To be able to make sense of your menu.lst I need what I ask you first:
sudo fdisk -lu

---

### Post by sandysandy on 2007-10-07
thanx.
can u tell me how to get     sudo fdisk -lu 
i tried running this command ( sudo fdisk -lu) in grub editor. nothing happened.

Thanx again

---

### Post by Pumalite on 2007-10-07
At the Terminal:
sudo fdisk -lu
(l is small L)

---

### Post by sandysandy on 2007-10-07
[COLOR="Red"]its as follows:-[/COLOR]

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    37929464    18964701   83  Linux
/dev/sda2        73224270    78156224     2465977+   5  Extended
/dev/sda3   *    37929465    73224269    17647402+  83  Linux
/dev/sda5        74862963    78156224     1646631   82  Linux swap / Solaris
/dev/sda6        73224396    74862899      819252   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    51199154    25599546    7  HPFS/NTFS
/dev/sdb2        51199155   266373764   107587305    f  W95 Ext'd (LBA)
/dev/sdb3   *   266373765   312576704    23101470   83  Linux
/dev/sdb5        51199218   133114589    40957686    7  HPFS/NTFS
/dev/sdb6       133114653   215030024    40957686    7  HPFS/NTFS
/dev/sdb7       215030088   264285314    24627613+   7  HPFS/NTFS
/dev/sdb8       264285378   266373764     1044193+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

----------

thanx:)

---

### Post by Pumalite on 2007-10-07
You have Linuxes at sda3 and sdb3 with two bootflags. Let's find out.
Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst
Change (hd0,0) for (hd0,2)
Save, exit, reboot

---

### Post by sandysandy on 2007-10-07
[COLOR="Red"]**the following displayed in the terminal:-**[/COLOR]

ubuntu@ubuntu:~$ sudo cp/boot/grub/menu.lst /boot/grub/menu.lst.bac
sudo: cp/boot/grub/menu.lst: command not found
ubuntu@ubuntu:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bac
cp: cannot stat `/boot/grub/menu.lst': No such file or directory
ubuntu@ubuntu:~$ sudo gedit /boot/grub/menu.lst
ubuntu@ubuntu:~$ gksu gedit /boot/grub/menu.lst
ubuntu@ubuntu:~$ gksu gedit /boot/grub/menu.lst
ubuntu@ubuntu:~$ suco cp /boot/grub/menu.lst /boot/grub/menu.lst.back
bash: suco: command not found
ubuntu@ubuntu:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
cp: cannot stat `/boot/grub/menu.lst': No such file or directory
ubuntu@ubuntu:~$ gksudo gedit /boot/grub/menu.lst

** (gedit:15815): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

** (gedit:15815): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

** (gedit:15815): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
ubuntu@ubuntu:~$ 

thanxs

---

### Post by Pumalite on 2007-10-07
Typo:

gksudo gedit /boot/grub/menu.lst

---

### Post by sandysandy on 2007-10-07
[COLOR="Red"]
while trying to save file the following displayed:-[/COLOR]

ubuntu@ubuntu:~$ gksudo gedit /boot/grub/menu.lst

** (gedit:16953): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
ubuntu@ubuntu:~$ 

thanx

---

### Post by Pumalite on 2007-10-07
I hope you have your backup
sudo cp /boot/grub/menu.lst.back /boot/grub/menu.lst
Check that is there again. Backup again. Be careful this time.

---

### Post by sandysandy on 2007-10-07
i think the menu.lst is empty from beginning itself. it is refusing to save or back up. 

thanx

---

### Post by Pumalite on 2007-10-07
With your file browser go to /boot/grub and see if menu.lst is there and double click on it.
Report back.

---

### Post by sandysandy on 2007-10-08
the file menu.lst is there on both partition. however it does not permit changes. maybe this is because i have booted from live cd & not hdd.

thanx

---

### Post by Pumalite on 2007-10-08
[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

---

### Post by sandysandy on 2007-10-12
thanx for ur patience.

i reinstalled 7.04. while booting from hard disk the following message comes

booting from local disk
Isolinux: Disk error 01, AX=0201, drive 80
Boot failed: press a key to restart.

also i am attaching the following:-

sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 294 2361523+ 83 Linux
/dev/sda2 4559 4865 2465977+ 82 Linux swap / Solaris
/dev/sda3 * 2362 4558 17647402+ 83 Linux
/dev/sda4 295 2361 16603177+ 83 Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 1 3187 25599546 7 HPFS/NTFS
/dev/sdb2 3188 16581 107587305 f W95 Ext'd (LBA)
/dev/sdb3 * 16582 19457 23101470 83 Linux
/dev/sdb5 3188 8286 40957686 7 HPFS/NTFS
/dev/sdb6 8287 13385 40957686 7 HPFS/NTFS
/dev/sdb7 13386 16451 24627613+ 7 HPFS/NTFS
/dev/sdb8 16452 16581 1044193+ 82 Linux swap / Solaris
ubuntu@ubuntu:~$

regards

---

### Post by Pumalite on 2007-10-12
If I were you I'd start again from the basics:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Make sure you do md5sum on iso, burn at 4x, I'd go with the Alternate CD (better results, more control)

---

### Post by sandysandy on 2007-10-12
thanx

---

### Post by sandysandy on 2007-10-12
thanx
 i will give it a try.

---

