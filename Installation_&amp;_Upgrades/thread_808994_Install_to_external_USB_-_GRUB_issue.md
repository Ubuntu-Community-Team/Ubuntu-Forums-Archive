---
title: "Install to external USB - GRUB issue"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by rosenrosen on 2008-05-27
I successfully installed 8.04 to an external USB but I think I made a mistake with GRUB.  My plan was not to interfere with the normal booting of my system and allow it to continue to boot to XP unless I entered the "Boot Menu" manually during initial boot up.  The install asked if I wanted to install GRUB on the master boot record and I declined.  It then asked me where to put GRUB.  I wasn't sure how to specify my external drive (hd0? hd3?) so I left it blank and selected continue.  Anyway my system boots into XP as desired but when I interrupt the process and tell it to boot off the external drive where I believe I have successfully installed it says:

No boot device available, Press ENTER key to retry
SATA-0: Installed
SATA-1: Installed
SATA-4: Installed
SATA-5: Installed

(I have 2 internal disks and 3 external).  Can I fix this by somehow making my external Ubuntu bootable?  If I have to reinstall how do I know where to put GRUB when it asks?  Thanks.

---

### Post by meierfra. on 2008-05-27
It seems that grub did not get installed at all. But this can be fixed without reinstalling.

Boot from the Live Cd. Open a terminal (Applications->Accessories-Terminal) and type

```
sudo fdisk -l
```

Looking at the output you should be able to determine the Linux name of your ubuntu root partition. It should be something like /dev/sdb2 or /dev/hdc4. In the following I will pretend it is /dev/sdb2. But of course you will have to replace /dev/sdb2 by the correct Linux name.


```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb2 /ubuntu
sudo mount -t proc none /ubuntu/proc
sudo mount -o bind /dev /ubuntu/dev
sudo chroot /ubuntu 
mkdir /boot/grub/
grub-install /dev/sdb  (use the Linux name without the number)
update-grub 
```

This should be  it, but sometimes update-grub gets things wrong. We will also make sure that the grub-menu is not  hidden during boot up:

```
nano /boot/grub/menu.lst
```
change "#hiddenmenu"  to "hiddenmenu"
change  "timeout 3" to "timeout 10"
look for the line

#groot (hd1,2)  

(of course the numbers might be different for you) If  the first number is  not a zero, change  it to  "0". So "#groot (hd1,2)" needs to be changed to "#groot (hd0,2)". Save the file and do 

```
update-grub
```
again. Type "exit" a couple of times to close the terminal

Reboot from  your ubuntu drive. 

If things  go wrong or you need further help, post the output of "sudo fdisk -l" and the content of "/boot/grub/menu.lst" from the ubuntu partition.

---

### Post by rosenrosen on 2008-05-27
Thanks for the reply!  I'm still having an issue.  I booted from the Live CD and using fdisk -l, I'm confident that my external is being seen as /dev/sdd.  When I tried to mount /dev/sdd2 on /ubuntu it complained that this was an extended partition so I mounted /dev/sdd1 which worked and I think is what you intended.  The other mounts and chroot also worked.  I saw that I already had a /boot/grub directory so I ran:
 
> root@ubuntu:/boot/grub# grub-install /dev/sdd
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.

I got the same result if I cleared out the /boot/grub directory first.  Any additional suggestions?  I'll include the /boot/grub/menu.lst file as well.

root@ubuntu:/boot/grub# cat menu.lst
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
# kopt=root=UUID=afda34f3-734f-4e55-88f0-061ba84e7ce1 ro

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
# defoptions=quiet splash irqpoll

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=afda34f3-734f-4e55-88f0-061ba84e7ce1 ro quiet splash irqpoll
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=afda34f3-734f-4e55-88f0-061ba84e7ce1 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by meierfra. on 2008-05-27
Your menu.lst looks right. So you only have to  get the "grub-install /dev/sdd" part to work. 


> The file /boot/grub/stage1 not read correctly. 

Well, that is an error message I have not seen yet.

Mount the  ubuntu partition as before.

See whether you have a  file  named "stage1"  in

/ubuntu/usr/lib/grub/i386-pc/

or in 

/ubuntu/boot/grub

(Or you might search the computer for "stage1")

You might try reinstall grub: chroot as before

Check whether you have a working internet connection in the chroot environment:

```
ping -c 3 www.google.com
```
If yes:

```
apt-get update
apt-get purge grub
apt-get install grub
```

If no;

```
 apt-get install --reinstall grub
```


After you reinstalled grub try

```
 grub-install /dev/sdd 
```
again (in the chroot)


If you have a stage1 file in /ubuntu/boot/grub you can also try this in place of "grub-install /dev/sdd" (you don't have to chroot)



```

sudo grub
```

and at the "grub>" prompt:


```
 find /boot/grub/stage1 
```
The output will be something of the form "(hdx,0)" (probably x=3)
then  at the "grub>" prompt:

```
root (hdx,0)
setup (hdx)
quit

```


(I do NOT recommend this yet. But you should be  able to solve your problem by reinstalling Ubuntu and using "/dev/sdd" for the  grub location in the "advanced" button. You might have to fix menu.lst, but since you already know how it's supposed to look like, that will be easy: all (hd?,?) need to be (hd0,0))

---

### Post by rosenrosen on 2008-05-28
Apparently the error message I was seeing was due to the fact that there was some confusion over the logical name of the external disk I installed to.  There was a line in /et/mtab that referenced /dev/sdc even though my external was currently being recognized as /dev/sdd.  I manually changed /etc/mtab and the commands in the first reply worked perfectly.  Thanks.

---

### Post by meierfra. on 2008-05-28
> There was a line in /etc/mtab that referenced /dev/sdc even though my external was currently being recognized as /dev/sdd. 

Good job. I never would have   thought about looking at /etc/mtab. Well, one learns something new everyday.

---

