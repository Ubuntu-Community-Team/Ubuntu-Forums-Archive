---
title: "Grub error 15 on fresh Kubuntu raid 0 install - menu.lst &amp;&amp; fstab posted"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by ejw2076 on 2007-07-07
Here is my setup:
Abit fatal1ty motherboard with fakeraid
2 WD 36 gig raptors running raid 0

I booted the live cd and followed the [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto#head-b7614c2e2ed565bf6c1a2c0e067d58af9eaf01aa").   

I installed and ran dmraid -ay, this mapped my drive to /dev/mapper/pdc_iaf

I then formatted with fdisk as 
a 70gb reiserfs partition set up as boot
a 1 gig swap partition 

After I got the disk set up and formated I mounted it to /target as shown in tutorial.  then installed all software the tutorial asks for without any errors.  It is setting up the bootloader that I believe the problem came into play.


So I have in my /dev both:
/dev/sda 
/dev/sdb
These are the two WD drives

 then the raid stripe: 
/dev/mapper/pdc_iaf 
and its partitions 
/dev/mapper/pdc_iaf1 (70gig boot drive)
/dev/mapper/pdc_iaf2 (1 gig swap drive).

in grub I ran:
device (hd0) /dev/mapper/pdc_iaf1
root (hd0,0)

I then modified the menu.lst file and set up password:

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
password --md5 $1$tCCD2$EkvclNlfiqBD/QuRKB9Kg0
#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,0)
# kernel	/vmlinuz root=/dev/mapper/pdc_iaf1 ro
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
# kopt=root=/dev/mapper/pdc_iaf1 ro

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
# lockalternative=true

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

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=/dev/mapper/pdc_iaf1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
lock
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=/dev/mapper/pdc_iaf1 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Then set up my fstab:
```
# UNCONFIGURED FSTAB FOR BASE SYSTEM
proc /proc proc rw 0 0
/dev/mapper/pdc_iaf1 / reiserfs defaults 0 1
/dev/mapper/pdc_iaf2 none swap sw 00

```


The error is thrown right when grub tries to start up:

Error 15: file not found

Press any key to continue


recovery mode runs no problem at all, but I cant get it to boot correctly.  Any advice would be appreciated.

---

### Post by HJam72 on 2007-07-07
I believe I'm having a very similar problem with the same error message, except I get that error message for everything but Win XP. I've tried to reinstall grub at least 3 times with the same results. I now have XP, Ubuntu, and Fedora, but only XP boots. Also, my list of OSs shown when grub starts includes like a dozen variations of Ubuntu, one copy of XP (which is correct), and not one copy of Fedora--despite the fact that grub was last reinstalled by a Fedora installation CD. 

I have a feeling that reinstalling Ubuntu would solve this problem, but I don't want to do that--and it might happen again anyway.

---

### Post by ejw2076 on 2007-07-07
i think all the os's on you comp that load as selections before booting are at the bottom of the menu.lst file.  If every time you went to reload grub it added different items here then it would make sense that you had multiple ones.  I'm still trying working on this a bit.  I'm going to try to make sure I have the boot options right at the bottom of menu.lst and I redid my fstab file with the output (relating to raid and proc only) from 

cat /etc/mtab

---

### Post by HJam72 on 2007-07-09
Wanna hear something strange?

I coincides with this problem I (we) am (are) having.

Before I had my current copy of Ubuntu installed. There was a previously installed copy on that partition. I messed it on one way that I didn't know how to fix, so I deleted it first with gedit on CD. Then, when I had this problem that we're having, I fiddled around with grub and got Ubuntu to start--ONLY THE OLD DELETED AND WRITTEN OVER COPY WAS WHAT BOOTED UP!!!  :confused:

Then, I deleted it again with Norton PM and redid the whole thing, only to have the same problem again. The old copy was booting, despite being deleted and written over. Then, I installed Fedora on another partition, allowed it to reinstall grub (again), and I am now unable to boot Fedora or any kind of Ubuntu. I can't even boot them with my old GAG floppy. 

The old, deleted and copied over copy of Ubuntu booting up really freaked me out the first time it happened, and I still can't make any sense of that.

---

