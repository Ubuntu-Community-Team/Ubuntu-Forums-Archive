---
title: "Grub Error 17 on Intrepid upgrade"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BorgHunter on 2008-10-04
So I just upgraded to 8.10 beta, through the recommended "update-manager -d" procedure. It was pretty normal throughout (a couple packages had errors, but I figured I could fix everything after I had rebooted). I reboot and try to load 8.10, but I get Grub Error 17, something about being unable to mount the partition. Now, at this point I was in a panic, "oh noes my hard drive has been eaten", etc. Booting into Windows Vista (on a separate physical drive in the same machine) didn't assuage me at all, because the ext3 extension I installed in Vista couldn't mount my hard drive, saying it needed to be formatted. However, it looks like I dodged a bullet: I can mount and view that drive just fine from my old 8.04 live CD (which I fortuitously had laying around).

So what I'm wondering is, how do I get the drive straightened out without going through the irritating-and-not-optimal step of tossing my home folder onto an external drive and doing a fresh install?

---

### Post by caljohnsmith on 2008-10-04
From the Live CD, have you run an fsck on your Ubuntu partition yet? I would start with that:
```
sudo fsck -y /dev/sdX
```
Where sdX is your Ubuntu partition (make sure the partition is not mounted). Let me know how that goes or what errors it reports.

---

### Post by BorgHunter on 2008-10-04
> **caljohnsmith said:**
> From the Live CD, have you run an fsck on your Ubuntu partition yet? I would start with that:
```
sudo fsck -y /dev/sdX
```
Where sdX is your Ubuntu partition (make sure the partition is not mounted). Let me know how that goes or what errors it reports.

Looks like fsck ran and didn't find anything:

```
ubuntu@ubuntu:~$ sudo fsck -y /dev/sdb1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/ has been mounted 33 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/: 555658/9682944 files (3.5% non-contiguous), 12931990/19346268 blocks
```

---

### Post by caljohnsmith on 2008-10-04
OK, that's a good sign fsck didn't find anything wrong. When you get the Grub error 17, do you get it before you get the Grub menu or after you select Ubuntu? 

Please post:
```
sudo fdisk -lu
mount /dev/sdb1 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by BorgHunter on 2008-10-04
> **caljohnsmith said:**
> OK, that's a good sign fsck didn't find anything wrong. When you get the Grub error 17, do you get it before you get the Grub menu or after you select Ubuntu? 
After I select an option. Any of the options, except Windows, does it, even memtest86+.

[quote=caljohnsmith]Please post:
```
sudo fdisk -lu
mount /dev/sdb1 /mnt
cat /mnt/boot/grub/menu.lst
```[/QUOTE]
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x088e088e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   321669182   160834560    7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001e3a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   154770209    77385073+  83  Linux
/dev/sdb2       154770210   160826714     3028252+   5  Extended
/dev/sdb5       154770273   160826714     3028221   82  Linux swap / Solaris
```
Mounting the drive doesn't output anything to stdout.

menu.lst is a true beast of a file. Lots of old kernels have accumulated, it seems.
```
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
# kopt=root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro

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

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd1,0)
kernel		/boot/last-good-boot/vmlinuz root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash last-good-boot
initrd		/boot/last-good-boot/initrd.img
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.25-2-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.25-2-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.25-2-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.25-2-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.25-2-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.25-2-386

title		Ubuntu intrepid (development branch), kernel 2.6.24-21-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-21-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-21-386

title		Ubuntu intrepid (development branch), kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-20-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-20-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-20-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-20-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-20-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-20-386

title		Ubuntu intrepid (development branch), kernel 2.6.24-20-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-20-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-18-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-18-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-18-386

title		Ubuntu intrepid (development branch), kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-17-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-17-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-17-386

title		Ubuntu intrepid (development branch), kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-17-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-16-386

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu intrepid (development branch), kernel 2.6.22-14-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.22-14-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu intrepid (development branch), kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu intrepid (development branch), kernel 2.6.20-16-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.20-16-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu intrepid (development branch), kernel 2.6.17-10-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.17-10-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.17-10-386

title		Ubuntu intrepid (development branch), kernel 2.6.15-27-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.15-27-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.15-27-386

title		Ubuntu intrepid (development branch), kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu intrepid (development branch), kernel 2.6.15-25-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.15-25-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.15-25-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.15-25-386

title		Ubuntu intrepid (development branch), kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.15-23-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.15-23-386

title		Ubuntu intrepid (development branch), kernel 2.6.12-9-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.12-9-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=05982f11-4919-4ef6-8e01-c6af464b27ce ro  single
initrd		/boot/initrd.img-2.6.12-9-386

title		Ubuntu intrepid (development branch), memtest86+
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
title		Windows Vista Business
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by caljohnsmith on 2008-10-04
OK, I think I see your problem; if you can successfully boot Vista from your Grub menu, that means your Ubuntu entries should use (hd0,0) instead of (hd1,0). On start up when you get your Grub menu, select one of your Ubuntu entries, hit "e" to edit it, select the line that says "root (hd1,0)", press "e" to edit it, change it to "root (hd0,0)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent if it works once you get into Ubuntu. You can do that with: 
```
gksudo gedit /boot/grub/menu.lst
```
And change the line with "#groot=(hd1,0)" to:
```
#groot=(hd0,0)
```
Then save and quit. Next do:
```
sudo update-grub
```
And that should change all your countless Ubuntu entries to use (hd0,0) instead of (hd1,0). Let me know how it goes or if you run into problems.

---

### Post by BorgHunter on 2008-10-04
> **caljohnsmith said:**
> OK, I think I see your problem; if you can successfully boot Vista from your Grub menu, that means your Ubuntu entries should use (hd0,0) instead of (hd1,0).
Yeah, I saw that as I was staring at menu.lst. Can't believe I didn't see it earlier. That solved everything, thanks!

---

