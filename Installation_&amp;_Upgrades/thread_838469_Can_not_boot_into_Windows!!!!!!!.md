---
title: "Can not boot into Windows!!!!!!!"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by daniel7860 on 2008-06-23
i had a windows partition and a linux one. i wanted to reinstall linux and in the partition manger accidently deleted the little file that i think i used to boot into windows.so when i turn on the computer i dont get the option to boot windows.i kept the windows partition though and i can access it through ubuntu. 
does anybody know how i could boot windows again without reinstalling it?:confused:

---

### Post by arpanaut on 2008-06-23
While re-installing did you allow grub to be installed in the default location or did you specify somewhere else?

Just a shot in the dark..
In a terminal try:

```
sudo update-grub
```

Some added info: If you need to reinstall grub, 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

also good read:  [http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

if all else fails:  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by daniel7860 on 2008-06-23
this is what happened when i typed in update-grub:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by arpanaut on 2008-06-23
post the contents of:

/boot/grub/menu.lst

is there a reference to your windows install in there?
If not a reinstall of grub may be necessary...
Let's see whats in your menu.lst

---

### Post by daniel7860 on 2008-06-23
well i tried some stuff and i dont think i did ut right, and those links u gave me are too complicated.:(:(:(:confused::confused::confused:

---

### Post by daniel7860 on 2008-06-23
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
# kopt=root=UUID=79392c58-fdac-45b8-b2ec-5f465a25985b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=79392c58-fdac-45b8-b2ec-5f465a25985b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=79392c58-fdac-45b8-b2ec-5f465a25985b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=79392c58-fdac-45b8-b2ec-5f465a25985b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=79392c58-fdac-45b8-b2ec-5f465a25985b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by arpanaut on 2008-06-23
From the terminal,
Post the result of:

```
sudo fdisk -l
```

Grub is not seeing your win installation and that must be fixed.
In the meantime dl the supergrub disk and burn it is a very handy tool to have for situations like this.  If your win install is intact IT will allow you to boot to it until this is fixed.

Help from more skilled members of the forum is gladly welcomed here! :)

---

### Post by daniel7860 on 2008-06-23
-o#-o:roll::roll::roll::icon_frown::-s:-k:-k...............................

---

### Post by daniel7860 on 2008-06-23
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4766    38282863+   7  HPFS/NTFS
/dev/sda2            4767        7296    20322225   83  Linux

---

### Post by arpanaut on 2008-06-23
Sorry about the delay I'm looking for more info.
I've nerver had grub not find my win partitions, so I'm a little lost now...
hence my appeal for more help!

Will get back soon though. Hopefully with a solution.
Please do get the SGrub disk though as it will help a lot until we get you fixed up!

---

### Post by meierfra. on 2008-06-23
Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

Change

"timeout 3" to "timeout 10"

and

"hiddenmenu"  to "#hiddenmenu"


Add this to the very end of the file:

title  Windows XP
root (hd0,0)
chainloader +1


Save the file and reboot.

---

### Post by daniel7860 on 2008-06-23
it does give me an option : Windows XP but when i choose it it says   NTLDR missing ctrl+alt+del to reboot

---

### Post by daniel7860 on 2008-06-23
this is my menu.lst file again:

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
# kopt=root=UUID=79392c58-fdac-45b8-b2ec-5f465a25985b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=79392c58-fdac-45b8-b2ec-5f465a25985b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=79392c58-fdac-45b8-b2ec-5f465a25985b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=79392c58-fdac-45b8-b2ec-5f465a25985b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=79392c58-fdac-45b8-b2ec-5f465a25985b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title Windows XP
root (hd0,0)
chainloader +1

---

### Post by meierfra. on 2008-06-23
> i wanted to reinstall linux and in the partition manger accidently deleted the little file that i think i used to boot into windows

???? The partition manager would not deleted any files.

But did  you delete any partitions?

---

### Post by daniel7860 on 2008-06-23
there was 3 one with ubuntu which i wanted to replace one with windows and  a third one which was very small and i deleted it.

---

### Post by meierfra. on 2008-06-23
> third one which was very small and i deleted it. 

That probably was your swap partition, which would not contain any boot files. But lets check  whether any of your boot files are missing:


```
sudo mkdir /windows   
sudo mount /dev/sda1 /windows
ls  /windows
```

This  list all the files in the System directory of your Windows Partition. If any of the files "boot.ini", "NTLDR" and "NTDETECT.COM" are missing:

Download this file: [http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573]("http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573")
and save it to your home folder (/home/your_username/) Then


```
cd /windows
sudo tar -xvzf /home/your_username/Archive.tar.gz
ls  /windows
```

Make sure you now have the files "boot.ini", "NTLDR" and "NTDETECT.COM"

Reboot and hope for the best.


[B]
If this did not solve your problem:[/B]


Boot from your WindowsCD, press "r" to enter the repair console
and type

```

chkdsk

chkdsk /r   (do this only if chkdsk found some errors)

fixboot

exit
```


**You might also try **

title Windows XP
rootnoverify (hd0,0)
chainloader +1 

in menu.lst

---

### Post by daniel7860 on 2008-06-23
:):):):):KS:KS:KS:guitar:
the first one did it.
thank you so much.

---

### Post by meierfra. on 2008-06-23
> the first one did it.
thank you so much.

You are welcome. Glad to be of help.   (Thanks arpanaut, for directing me to this thread)

---

