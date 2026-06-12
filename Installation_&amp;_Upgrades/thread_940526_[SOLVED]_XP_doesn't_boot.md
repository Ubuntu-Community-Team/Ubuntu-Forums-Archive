---
title: "[SOLVED] XP doesn't boot"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by YldGuy on 2008-10-07
recently my friend had to do a windows recovery on his laptop using the recovery partition. before the recovery he had XP and Ubuntu running. after the recovery he lost the ubuntu partition and the xp now wont boot and said the disk is not bootable. so we tried reinstalling XP using the XP disk but it said "hdd not recognized". next we tried fiesty live cd and the hard disk showed up with only recovery partition and the nonbootable xp partition. thinking that having ubuntu will give the grub menu and make xp partition bootable, we loaded fiesty which worked fine. but the problem still remained, XP wont boot. we checked the menu.lst. that is fine and lists XP on the second partition hd(0,1) which is how it is. but somehow its not bootable. and we are stuck here not being able to boot to XP. it still says its not bootable. 

my guess is since XP is not on the first partition, its not being recognized. will changing the partition order, so that xp becomes the first partition and ubuntu becomes the second, help? if so how do i change the partition order? its a single harddisk with 4 primary partitions - Ubuntu, nonbootable XP, recovery partition, swap.

---

### Post by caljohnsmith on 2008-10-07
Please post the output of:
```
sudo fdisk -l
cat /boot/grub/menu.lst
```
Also, it sounds like there might be a problem with the HDD's partition table, so I think we should check that to make sure it is not the problem. First enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk with:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by YldGuy on 2008-12-20
> **caljohnsmith said:**
> Please post the output of:
```
sudo fdisk -l
cat /boot/grub/menu.lst
```
Also, it sounds like there might be a problem with the HDD's partition table, so I think we should check that to make sure it is not the problem. First enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk with:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

it has been unusually long time but certain things happened and i could look up this matter now only. my apologies.

however, i did the steps you mentioned.

here is the output of fdisk

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1920    15422368+  83  Linux
/dev/sda2   *        1921        8137    49938052+   b  W95 FAT32
/dev/sda3            8138        9598    11735482+   c  W95 FAT32 (LBA)
/dev/sda4            9599        9729     1052257+  82  Linux swap / Solaris


and here is the output of testdisk

Disk /dev/sda - 80 GB / 74 GiB - CHS 9730 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1  1919 254 63   30844737
P FAT32 LBA             1920   0  1  8136 254 63   99876105
P FAT32 LBA             8137   0  1  9597 254 63   23470965 [HP_RECOVERY]
P Linux Swap            9598   0  1  9728 254 63    2104515

Structure: Ok.

here is menu.lst

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
# kopt=root=UUID=87e2ce71-1f43-4645-b3df-c7be3b5514e3 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=87e2ce71-1f43-4645-b3df-c7be3b5514e3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=87e2ce71-1f43-4645-b3df-c7be3b5514e3 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Recovery Partition - DO NOT TOUCH
root		(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by infamous-online on 2008-12-20
A word of advice, **[COLOR="Red"]never[/COLOR]** install Ubuntu and Windows on the same harddrive. Always install them on seperate disks. 

Since your friend was on a laptop when he got this unfortunate error, I think he should either use the whole harddrive for ubuntu or use a flashdrive if the bios supports it.

Now to help, the reason xp isn't being recognized is that the MBR has been overwritten by grub when you installed ubuntu onto the hd, which is why I suggest you use a flash drive setup.

You're pretty much limited here, if you have valuable data on your windows partition, then I would use one of those kits to where you can hook your laptop hd in an enclosure through a usb port/sata/ieee and salvage (if possible) whatever you can and then perform a fresh re-install.

This may not be what you wanted to hear, but it's just one solution.

---

### Post by caljohnsmith on 2008-12-20
> **infamous-online said:**
> A word of advice, **[COLOR="Red"]never[/COLOR]** install Ubuntu and Windows on the same harddrive. Always install them on seperate disks. 

I disagree. Many, many, Ubuntu users, including myself, dual-boot Ubuntu with Windows on the same HDD. There is nothing wrong with doing that; it is not necessary to give Ubuntu its own HDD. 
> **infamous-online said:**
> 
Now to help, the reason xp isn't being recognized is that the MBR has been overwritten by grub when you installed ubuntu onto the hd, which is why I suggest you use a flash drive setup.

In my experience, Grub is perfectly capable of booting Windows for 99% of most setups, and having Grub in the MBR does not cause XP to not be "recognized." All you have to do is add the correct entry in Grub's menu.lst to boot Windows. That assumes of course that Windows doesn't have any issues, but unfortunately it sounds like YldGuy's Windows installation has problems right now.

**YldGuy**, what exactly happens when you try to boot the "Windows XP Media Center Edition" entry in the Grub menu on start up? In order to get a clearer picture of your setup, how about opening a terminal in Ubuntu (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and maybe what your problem might be.

---

### Post by YldGuy on 2008-12-20
> **infamous-online said:**
> A word of advice, **[COLOR="Red"]never[/COLOR]** install Ubuntu and Windows on the same harddrive. Always install them on seperate disks. 

Since your friend was on a laptop when he got this unfortunate error, I think he should either use the whole harddrive for ubuntu or use a flashdrive if the bios supports it.

Now to help, the reason xp isn't being recognized is that the MBR has been overwritten by grub when you installed ubuntu onto the hd, which is why I suggest you use a flash drive setup.

You're pretty much limited here, if you have valuable data on your windows partition, then I would use one of those kits to where you can hook your laptop hd in an enclosure through a usb port/sata/ieee and salvage (if possible) whatever you can and then perform a fresh re-install.

This may not be what you wanted to hear, but it's just one solution.

i dont think so. i have used ubuntu and XP both together on my laptop and it ran fine. i think i will try all the other options that i can try to salvage this XP.

---

### Post by YldGuy on 2008-12-20
> **caljohnsmith said:**
> 

**YldGuy**, what exactly happens when you try to boot the "Windows XP Media Center Edition" entry in the Grub menu on start up? In order to get a clearer picture of your setup, how about opening a terminal in Ubuntu (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and maybe what your problem might be.

the message thats flashed is "This partition cannot boot properly. please insert a boot floppy to continue booting properly". i press enter and it comes back to GRUB menu.

the script result is this:
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for its boot files.

sda1:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Ubuntu 8.04.1 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sda2:
    File system:  vfat
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: XP
    Boot files/directories present:  /menu.lst /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda3:
    File system:  vfat
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present:  /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda4:
    File system:  swap


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    30844799    15422368+  83  Linux
/dev/sda2   *    30844800   130720904    49938052+   b  W95 FAT32
/dev/sda3       130720905   154191869    11735482+   c  W95 FAT32 (LBA)
/dev/sda4       154191870   156296384     1052257+  82  Linux swap / Solaris
/dev/sda1: UUID="87e2ce71-1f43-4645-b3df-c7be3b5514e3" TYPE="ext3" 
/dev/sda2: LABEL="M-^?M-i\M-g@3M-!M-CgM-*^N" UUID="48E7-4C7D" TYPE="vfat" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="3EC6-2E70" TYPE="vfat" 
/dev/sda4: TYPE="swap" UUID="bf8576c6-aef1-4d49-826b-fb87ff36636e" 
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 30844737, Id=83
/dev/sda2 : start= 30844800, size= 99876105, Id= b, bootable
/dev/sda3 : start=130720905, size= 23470965, Id= c
/dev/sda4 : start=154191870, size=  2104515, Id=82

sda1/boot/grub/menu.lst

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
# kopt=root=UUID=87e2ce71-1f43-4645-b3df-c7be3b5514e3 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=87e2ce71-1f43-4645-b3df-c7be3b5514e3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=87e2ce71-1f43-4645-b3df-c7be3b5514e3 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Recovery Partition - DO NOT TOUCH
root		(hd0,2)
savedefault
makeactive
chainloader	+1


sda1/boot

total 18032
drwxr-xr-x  3 root root    4096 2008-12-20 12:12 .
drwxr-xr-x 21 root root    4096 2008-12-20 12:10 ..
-rw-r--r--  1 root root  422838 2008-11-25 04:17 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80062 2008-11-25 04:17 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2008-12-20 12:10 grub
-rw-r--r--  1 root root 7478419 2008-12-20 01:40 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7478080 2008-12-04 21:45 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 15:36 memtest86+.bin
-rw-r--r--  1 root root  905617 2008-11-25 04:17 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921176 2008-11-25 04:17 vmlinuz-2.6.24-22-generic

sda1/boot/grub

total 220
drwxr-xr-x 2 root root   4096 2008-12-20 12:10 .
drwxr-xr-x 3 root root   4096 2008-12-20 12:12 ..
-rw-r--r-- 1 root root    197 2008-10-04 20:33 default
-rw-r--r-- 1 root root     15 2008-10-04 20:33 device.map
-rw-r--r-- 1 root root   8660 2008-10-04 20:33 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2008-10-04 20:33 fat_stage1_5
-rw-r--r-- 1 root root     15 2008-10-04 20:33 installed-version
-rw-r--r-- 1 root root   9152 2008-10-04 20:33 jfs_stage1_5
-rw-r--r-- 1 root root   4774 2008-12-20 12:10 menu.lst
-rw-r--r-- 1 root root   4774 2008-12-20 12:10 menu.lst~
-rw-r--r-- 1 root root   7860 2008-10-04 20:33 minix_stage1_5
-rw-r--r-- 1 root root  10132 2008-10-04 20:33 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-10-04 20:33 stage1
-rw-r--r-- 1 root root 110292 2008-10-04 20:33 stage2
-rw-r--r-- 1 root root   9980 2008-10-04 20:33 xfs_stage1_5

sda2/menu.lst

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
# kopt=root=UUID=87e2ce71-1f43-4645-b3df-c7be3b5514e3 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=87e2ce71-1f43-4645-b3df-c7be3b5514e3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=87e2ce71-1f43-4645-b3df-c7be3b5514e3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows NT/2000/XP
root		(hd0,2)
savedefault
makeactive
chainloader	+1


sda2/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


sda3/boot.ini

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


StdErr Messages

---

### Post by caljohnsmith on 2008-12-20
OK, let's start by correcting your Windows boot.ini file, because it currently points to the wrong partition; please do the following:
```
sudo mount /dev/sda2 /mnt
gksudo gedit /mnt/boot.ini
```
And change it to use "2" for the partition like:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition[COLOR="Red"](2)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition[COLOR="Red"](2)[/COLOR]\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
```
Then reboot, try the "Windows XP Media Center Edition" entry in Grub, and let me know exactly what happens. We can work from there.

---

### Post by YldGuy on 2008-12-21
Thank you John for all your help. Unfortunately, I no longer have to work on this issue now. My friend lost his cool for one moment and erased his Ubuntu and installed XP over it. If only he had shown little patience. If only i had been at his home a little longer. I somehow feel that changing the partition number would have done the trick as the recovery partition was trying to put XP onto first partition and had configured the boot.ini accordingly.

I can't tell how sad and angry i am right now :|. Thanks anyways for your help John. I will keep this solution in mind if i come across any of this again. Thanks.

---

### Post by YldGuy on 2008-12-21
Thank you John for all your help. Unfortunately, I no longer have to work on this issue now. My friend lost his cool for one moment and erased his Ubuntu and installed XP over it. If only he had shown little patience. If only i had been at his home a little longer. I somehow feel that changing the partition number would have done the trick as the recovery partition was trying to put XP onto first partition and had configured the boot.ini accordingly.

I can't tell how sad and angry i am right now :|. Thanks anyways for your help John. I will keep this solution in mind if i come across any of this again. Thanks.

---

### Post by ShazZ on 2008-12-22
Hello...
It seems I have just about the same problem as **YldGuy**.

The main difference is this happened when I installed _Intrepid _ over _Hardy_ (because when I tried to update I had a weird graphical problem, and it seemed somehow the update un-installed the *xserver.xorg* after the update).
...So after I made the 8.10 installation CD (checked the md5sum hash) I installed it.  Once installation had completed, I rebooted into Linux to see that it worked; however, the when I tried to boot into Windows XP x64, it gave me the same error message that **YldGuy**'s friend had.

---

### Post by ShazZ on 2008-12-22
here is what the " /boot/grub/menu.lst" file shows under "other operating systems":

[B]title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP Professional x64 Edition
root        (hd0,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1[/B]



...and the Windows boot.ini file:
[B]
[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"[/B]

---

### Post by caljohnsmith on 2008-12-22
[QUOTE=YldGuy]Thank you John for all your help. Unfortunately, I no longer have to work on this issue now. My friend lost his cool for one moment and erased his Ubuntu and installed XP over it. If only he had shown little patience. If only i had been at his home a little longer. I somehow feel that changing the partition number would have done the trick as the recovery partition was trying to put XP onto first partition and had configured the boot.ini accordingly.

I can't tell how sad and angry i am right now . Thanks anyways for your help John. I will keep this solution in mind if i come across any of this again. Thanks.
[/QUOTE]

Oh well, at least you tried. Using Ubuntu definitely requires some patience and willingness to learn new things about an OS, so maybe it's best your friend stick with XP for now; maybe in the future he will be willing to give Ubuntu another try.

---

### Post by caljohnsmith on 2008-12-22
**ShazZ**, I see a couple of issues all ready; first the Windows entry in the menu.lst shouldn't have the mapping lines if Windows is truly on (hd0), and also I see from the Windows boot.ini file that at some point you installed Ubuntu inside of Windows via Wubi. In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by ShazZ on 2008-12-23
Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in partition #2 for its boot files.
Grub is installed in the MBR of /dev/sdb and looks on the same drive in partition #2 for its boot files.
Windows is installed in the MBR of /dev/sdc

sda1:
    File system:  vfat
    Boot sector  type:  Fat32
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdb1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sdb1 starts at sector 63.
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr /ubuntu/disks /ubuntu/disks/boot/ /ubuntu/disks/boot/grub /ubuntu/disks/boot/grub

sdb2:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb3:
    File system:  Extended Partition

sdb5:
    File system:  swap

sdc1:
    File system:  vfat
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000882a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001    b  W95 FAT32

/dev/sda: OK


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ce8e52f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156312449    78156193+   7  HPFS/NTFS
/dev/sdb2       156312450   302809184    73248367+  83  Linux
/dev/sdb3       302809185   312576704     4883760    5  Extended
/dev/sdb5       302809248   312576704     4883728+  82  Linux swap / Solaris

/dev/sda: OK
/dev/sdb: OK


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976768064   488384001    c  W95 FAT32 (LBA)

/dev/sda: OK
/dev/sdb: OK
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
partition 1: end: (c,h,s) expected (1023,254,63) found (1021,254,63)
/dev/sdc: OK

/dev/sda1: UUID="48BB-D198" TYPE="vfat" 
/dev/sdb1: UUID="9E807E30807E0ED1" TYPE="ntfs" 
/dev/sdb2: UUID="09dc2750-41cc-4f63-8464-32cdefe6d45f" TYPE="ext3" 
/dev/sdb5: UUID="735937a8-cda2-4e2d-8850-a48266887b76" TYPE="swap" 
/dev/sdc1: LABEL="My Book" UUID="9E28-EFAB" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

sdb1/boot.ini

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"


sdb1/ubuntu/disks

total 4
drwxrwxrwx 1 root root    0 2008-12-20 22:04 .
drwxrwxrwx 1 root root 4096 2008-12-20 22:04 ..
drwxrwxrwx 1 root root    0 2008-12-20 22:04 boot
drwxrwxrwx 1 root root    0 2008-12-20 22:04 shared

sdb1/ubuntu/disks/boot/

total 0
drwxrwxrwx 1 root root 0 2008-12-20 22:04 .
drwxrwxrwx 1 root root 0 2008-12-20 22:04 ..
drwxrwxrwx 1 root root 0 2008-12-20 22:04 grub

sdb1/ubuntu/disks/boot/grub

total 0
drwxrwxrwx 1 root root 0 2008-12-20 22:04 .
drwxrwxrwx 1 root root 0 2008-12-20 22:04 ..

sdb1/ubuntu/disks/boot/grub

total 0
drwxrwxrwx 1 root root 0 2008-12-20 22:04 .
drwxrwxrwx 1 root root 0 2008-12-20 22:04 ..

sdb2/boot/grub/menu.lst

default 0
timeout 27

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
# kopt=root=UUID=09dc2750-41cc-4f63-8464-32cdefe6d45f ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=09dc2750-41cc-4f63-8464-32cdefe6d45f

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

title Ubuntu 8.10, kernel 2.6.27-9-generic
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=09dc2750-41cc-4f63-8464-32cdefe6d45f ro xforcevesa quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=09dc2750-41cc-4f63-8464-32cdefe6d45f ro xforcevesa  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=09dc2750-41cc-4f63-8464-32cdefe6d45f ro xforcevesa quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=09dc2750-41cc-4f63-8464-32cdefe6d45f ro xforcevesa  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP Professional x64 Edition
root        (hd0,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


sdb2/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=09dc2750-41cc-4f63-8464-32cdefe6d45f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=735937a8-cda2-4e2d-8850-a48266887b76 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sdb2/boot

total 25516
drwxr-xr-x  3 root root    4096 2008-12-21 04:13 .
drwxr-xr-x 21 root root    4096 2008-12-21 04:13 ..
-rw-r--r--  1 root root  503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 23:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 20:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 23:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-22 05:19 grub
-rw-r--r--  1 root root 8664220 2008-12-21 04:13 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8663517 2008-12-21 04:13 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 23:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 23:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 20:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 23:30 vmlinuz-2.6.27-9-generic

sdb2/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-22 05:19 .
drwxr-xr-x 3 root root   4096 2008-12-21 04:13 ..
-rw-r--r-- 1 root root    197 2008-12-20 19:01 default
-rw-r--r-- 1 root root     45 2008-12-20 19:01 device.map
-rw-r--r-- 1 root root   8108 2008-12-20 19:01 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-20 19:01 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-20 19:01 installed-version
-rw-r--r-- 1 root root   8712 2008-12-20 19:01 jfs_stage1_5
-rw-r--r-- 1 root root   3471 2008-12-22 05:19 menu.lst
-rw-r--r-- 1 root root   3349 2008-12-21 05:33 menu.lst~
-rw-r--r-- 1 root root   5194 2008-12-21 04:35 menu.lst_original
-rw-r--r-- 1 root root   7352 2008-12-20 19:01 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-20 19:01 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-20 19:01 stage1
-rw-r--r-- 1 root root 121460 2008-12-20 19:01 stage2
-rw-r--r-- 1 root root   9556 2008-12-20 19:01 xfs_stage1_5

StdErr Messages 

Unknown BootLoader  on /dev/sdc1

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 40 20 00  |.Z.MSWIN4.1..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  02 4c 38 3a b4 d1 01 00  00 00 00 00 02 00 00 00  |.L8:............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ab ef 28 9e 4d  79 20 42 6f 6f 6b 20 20  |..)..(.My Book  |
00000050  20 20 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |  FAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

---

### Post by caljohnsmith on 2008-12-23
ShazZ, it looks like you have Grub installed to the MBR (Master Boot Record) of both your drives, so it is ambiguous which drive you are booting from on start up. That means we will have to try two possible entries in your Grub menu to boot Windows. How about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace the Windows entry at the bottom with the following two entries:
```

title Windows XP Professional x64 Edition (hd0)
root (hd0,0)
chainloader +1

title Windows XP Professional x64 Edition (hd1)
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```
I'm guessing that you are booting your sda drive on start up, and thus the second entry above should work. But give them both a try, and if for some reason neither works, let me know exactly what happens when you try each entry from your Grub menu. We can work from there.

---

### Post by ShazZ on 2008-12-23
Thanks a million.  The first option worked perfectly.  I tried it frist since I knew the my OS was on sdb (thats what the partition editor said).
and Windows is working great!

---

### Post by caljohnsmith on 2008-12-23
Glad to hear that worked OK, ShazZ. Cheers and happy holidays. :)

---

