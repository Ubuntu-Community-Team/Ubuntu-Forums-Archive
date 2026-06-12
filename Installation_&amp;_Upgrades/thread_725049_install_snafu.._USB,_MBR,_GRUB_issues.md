---
title: "install snafu.. USB, MBR, GRUB issues"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by Rob Hodge on 2008-03-15
well, this is my first time trying out ubuntu... used to work in IT years ago and haven't used linix in ages... in fact last time i installed any linux was when SLink was released as the unstable branch of debian!

really had to rub my eyes in disbelief when seeing the desktop on the live CD for the first time.... so much more polished and filled out!

anyway, i'm going to be using more linux in the future so i decided to get an install going to play around with it. problem is, the only machine i have acess to right now is me and my wife's laptop, running vista. the (so i thought) briliant idea i had was to install ubuntu to a 8 gig USB stick and have it higher up in the boot order, so if the stick is inserted, it boots to linux and it's a full production environment, unlike the live cd.

well, it went smootly. untill it came time to re-boot. the instalation program put grub on the MBR of the main disk on the laptop. 

so, when the usb stick was in, it said 'missing operating system'. when it booted from the hard drive with the usb stick removed, it died becasue it couldn't find the USB stick. and vista couldn't be booted. and my wife was due home in an hour and a half. 

so, i did what a normal husband would do. i panicked. the wifi wouldn't work on the live CD, so i unpluged the tivo and slid over to the entertainment center to get internet. i dug out the cd that came with the laptop (the 'pay more to unlock a better version of VISTA' cd) and spent 45 minutes googling how to restore the MBR. google was no help, microsoft support pages was a joke. so finaly i booted to the vista cd, and started poking around on the cd at the command prompt. after half an hour i found a command that looks like it'd work and issued it. 

presto. vista booted. my wife could check her e-mail again. and i breathed a sigh of relief. 

now, I'm stuck with a full installation on a USB drive, and i can't get grub installed on the USB sticks boot record so it will run.  i have zero experiance with grub, all i've ever used was LILO. i've fiddled around with grub on the live cd boot, but whenever i think i get the right command, i get some sort of error.

does anyone have an idea of a way to accomplish what i want to do? a full install on a bootable USB drive with zero footprint on the host computer? would i be better to re-install, get it running with grub on the MBR, then  ust that running install to install grub on the USB, then re- wipe the MR with vista?

Cheers,
Rob Hodge

---

### Post by Pumalite on 2008-03-15
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
Be careful in step 8>Advanced TAB and change (hd0) for /dev/???
??? corresponding to your USB
You can find out booting Ubuntu Live CD with your external plugged in  and running at the Terminal:
sudo fdisk -lu

---

### Post by dstew on 2008-03-15
If your BIOS boots a disk (usual case)  you need to install grub onto the MBR of the USB stick. If your BIOS can boot a *partition*, you can install grub to the Ubuntu root partition. Either way, when it is plugged in, it will boot, but when it is not plugged in, the BIOS will go down the list and boot the hard drive.

To install grub stage1 onto the MBR of the USB stick, you have to know what the grub-name of the stick is. Sometimes this involves some guesswork. One way to figure it out is to try to use grub (running from the Live CD) to try to boot the USB Ubuntu installation using commands entered on the grub command line. With the USB drive plugged in, from the Live CD, do```
sudo fdisk -l
```That will give a list of the drives. Is the USB drive there? If it is, you can use as a first guess that the grub-name of the drive will be (hd*n*), with *n* being the number corresponding to the place of the USB drive in the list, counting from 0. So, if the USB drive is /dev/sdb the grub name might be (hd1). If the Ubuntu root partition is the first one on that drive, its grub name should be (hd1,0).

So, keeping the above names as an example, try to boot the USB installation this way. Get a grub command line from a Live CD terminal by typing **sudo grub**. That should get you the grub command line with the grub> prompt. On the command line, enter```
root (hd1,0)
```Then type **kernel** but do not press enter. Press the Tab key. This uses the "auto complete" feature of the grub command line to list the kernels it can see. If more that one is present, pick the first one. It should be the generic kernel. You will need to add to the kernel line** root=/dev/sdb1** (whatever the Linux name of the root partition is) and the letters **ro** The whole kernel line should look something like this:```
/boot/vmlinuz-2.6.20-16-generic root=/dev/sdb1 ro
```If you are happy with the kernel line, press enter. Next, do **initrd** and press tab. You should get something like```
 /boot/initrd.img-2.6.20-16-generic
```The intird image file should have the same numbers as the kernel image. If you are happy with the initrd line, press enter. Then type **boot** and enter. If the USB Ubuntu installation boots, you know for sure what grub names to use. Then, you can install grub from the Live CD onto the USB stick with confidence:```
root (hd1,0)
setup (hd1)
quit
```

---

### Post by Rob Hodge on 2008-03-15
well, i re-installed and found the advanced tap abd had it install grub to /dev/sdb.

that part worked.  it starts to boot, and gives me a list of kernel entries to pick. 

however, whenever i pick any of them it says can't mount partition, gives me an error code, then bumps back to the chooser menu.

any suggestions?

---

### Post by Pumalite on 2008-03-15
Boot your Live CD and give me 2 things>
sudo fdisk -lu
cat....menu.lst (from your external drive).

---

### Post by Rob Hodge on 2008-03-15
here's the partition info:

> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1754eea6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   183751469    91875703+   7  HPFS/NTFS
/dev/sda2       183751470   195366464     5807497+   7  HPFS/NTFS

Disk /dev/sdb: 8086 MB, 8086617600 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794175 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15020774     7510356   83  Linux
/dev/sdb2        15020775    15791894      385560    5  Extended
/dev/sdb5        15020838    15791894      385528+  82  Linux swap / Solaris

and here's menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1


---

### Post by Pumalite on 2008-03-15
I imagine you don't want to boot your Windows from your external drive, so remove those entries. (I'm assuming this is the menu.lst that got installed in your external)
Change this:
title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet
To this:
title Ubuntu 7.10, kernel 2.6.22-14-generic
rootnoverify (hd1,0)
map  (hd0,0)  (hd1,0)
map  (hd1,0)  (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

I'm also assuming hdb1,0 is your external
Post:
blkid

---

### Post by Rob Hodge on 2008-03-15
it still is giving me an error about mounting the filesystem...

maybe i need a kernel image with usb built in instead of as a module? 

anyway, got any other ideas?

---

### Post by Pumalite on 2008-03-15
I ran out of ideas. Check these and see if you can find something helpful:
[http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-21-when-trying-to-boot-xp-after-installing-ubuntu-7.04-on-seperate-hdd-552043/](http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-21-when-trying-to-boot-xp-after-installing-ubuntu-7.04-on-seperate-hdd-552043/)

[http://ubuntuforums.org/showthread.php?t=606409](http://ubuntuforums.org/showthread.php?t=606409)
[http://ubuntuforums.org/showthread.php?t=598961&highlight=boot+from+external+drive](http://ubuntuforums.org/showthread.php?t=598961&highlight=boot+from+external+drive)
[http://ubuntuforums.org/showthread.php?t=598787&highlight=boot+from+external+drive](http://ubuntuforums.org/showthread.php?t=598787&highlight=boot+from+external+drive)
[http://ubuntuforums.org/showthread.php?t=598961](http://ubuntuforums.org/showthread.php?t=598961)
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
[http://ubuntuforums.org/showthread.php?t=614913](http://ubuntuforums.org/showthread.php?t=614913)
[http://ubuntuforums.org/showthread.php?t=614863](http://ubuntuforums.org/showthread.php?t=614863)
Also, try removing 'splash' from the kernel line in menu.lst.
Good luck

---

### Post by dstew on 2008-03-15
What is the error message you get when it says "can't mount partition"? One idea: maybe the UUID of the kernel root is not correct. From a command line do ```
sudo vol_id /dev/sdb1
```to see if the UUID matches the one in the kernel line:```
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975
```

---

### Post by Rob Hodge on 2008-03-16
well, they seem to match. i'll re-boot and see what the error message is exactly.

here's the outut of vol_id /dev/sdb1

> ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975
ID_FS_UUID_ENC=7ed0f17a-e140-40c4-aaa7-4f362de06975
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=


---

### Post by Rob Hodge on 2008-03-16
ok, here's the error message grub is giving me

Error 17 : cannot mount partition.

does this give you guys any leads to what's causing this?

maybe this has something to do with  it... here's my device.map file
> 
(hd0)	/dev/sda
(hd1)	/dev/sdb

---

### Post by Pumalite on 2008-03-16
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Rob Hodge on 2008-03-16
i tried reversing the device.map settings, but to no avail.

---

### Post by Rob Hodge on 2008-03-16
Solved iafter reading around on  what error 17 was... it seemed to be a misidentification of drves at boot.. so idecided to do trial and error. 

so i decided to do a trial and error of all possible combinations i could feed to grub. 

i changed the relevant part of my menu.list to this:

> 

title		Ubuntu 7.10, kernel 2.6.22-14-generic 1
rootnoverify	(hd1,0)
map		(hd0,0) (hd1,0)
map		(hd1,0) (hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic 2
rootnoverify	(hd0,0)
map		(hd0,0) (hd1,0)
map		(hd1,0) (hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic 3
rootnoverify	(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic 4
rootnoverify	(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
rootnoverify	(hd1,0)
map		(hd0,0) (hd1,0)
map		(hd1,0) (hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet


and proceded to go down the list and try them in order.

well, #2 fired right up and i'm now posting this from a full install of ubuntu, with everything including the swap file residing on one $29 8 gig usb drive. zero footprint on the family's laptop. and a full environment to play with for myself. 

all i've got to do is re-edit the map file back so there is a normal, resuce and memtest option using #2's settigns and i'm good to go.


only question i have is if i should try it without the map commands?
Cheers,
Rob Hodge

---

### Post by Pumalite on 2008-03-16
You can try anything. You are on your way to being an expert. Backup your handy work first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old

---

### Post by Rob Hodge on 2008-03-17
ok, i'm going to call this one solved.. but in case anyone else searches and finds this dealing with a similar problem, here's some follow up.

first: if you jus tmake the changes to the grub boot list like i did, you'll have an issue. whenever you get an update to the grub packages, your changes will be over written.

here's the fix i found:
in that file is some configuration lines for grub's update function. 

i had to find these lines
> 
## default grub root device
## e.g. groot=(hd0,0)
# groot=(h1,0)
and replace with these
> 
## default grub root device
## e.g. groot=(hd0,0)
# groot=(h0,0)

this change will make all upgrades to your system not break your boot setup.

and, i did find that this set of lines was enough to make it boot

> 
title	Ubuntu 7.10, kernel 2.6.22-14-generic 
root 	(hd0,0)
kernel 	/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro quiet splash
initrd 	/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root	(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed0f17a-e140-40c4-aaa7-4f362de06975 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root 	(hd0,0)
kernel		/boot/memtest86+.bin
quiet

now obviously your root uuid is going to be different, but you get the picture. i didn't need a root no verify oe any map statements.

Cheers,
Rob Hodge

---

