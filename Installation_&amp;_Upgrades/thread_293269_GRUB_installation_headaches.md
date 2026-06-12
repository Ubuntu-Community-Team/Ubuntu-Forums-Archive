---
title: "GRUB installation headaches"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by ranger0293 on 2006-11-05
I'm trying to set up a Vista RC2/Kubuntu system, but getting GRUB working is proving to be a hassle.

I have 4 SATA hard drives, /dev/sda through /dev/sdd.

/dev/sda and /dev/sdd are storage drives that have no OS on them.

/dev/sdc is my 120GB Vista drive that, until today, was booting perfectly.

/dev/sdb is my 80GB drive with Kubuntu freshly installed on it.

When I was installing, it said it would install GRUB to (hd0).  Upon restart I get an "Operating System Missing" error, so I guess GRUB was installed to the wrong place.

I wanted to get into Vista again, so I booted from the RC2 disk.  When I went to the "repair" option, it asked me to pick my Vista install from an empty list.  Clearly something has been overwritten that shouldn't have been.

My question is how can I fix GRUB so that I can get those two dual booting correctly.  I don't have a preference at all whether it's GRUB that gives me the option to boot to Kubuntu or Vista, or whether it's Vista's bootloader, so long as one of them works.

Is there a way to install GRUB to the correct place?  Is the fact that the Vista install CD doesn't see a Vista install mean that that install was damaged?  Is it recoverable.

Any help is greatly appreciated.

---

### Post by amohanty on 2006-11-05
The reason you cant find anything is that you installed grub to hd0 and it pretty much assumes thats where the OS is but in your case it isnt. And the reason you dont see Vista is because the MBR is overwritten and windows bootloaders have never really been quite smart (intentionally or otherwise).

You can do one of two things:
1. Switch sda with sdc ie make sdc primary master (change sata leads on mb) and look for:
restore grub mbr 
in the forums and follow instructions
OR
2. When grub shows up, press e and edit the
root (hd0,0) (or something like this)
to be 
root(hd2,0) (if you have multiple partition ons sdc the second # is the partition on which /boot resides starting from 0)

HTH
AM

---

### Post by youboontoo on 2006-11-05
/dev/sdc is probably hd2 to Grub. So you most likely should
have installed Grub to hd2 instead of hd0.

You might try looking at these:

Ubuntu Grub Howto
[URL="https://help.ubuntu.com/community/GrubHowto?highlight=%28%28GrubHowto"]
https://help.ubuntu.com/community/GrubHowto?highlight=%28%28GrubHowto[/URL]

GNU Grub Manual
[URL="http://www.gnu.org/software/grub/manual/html_node/index.html"]
http://www.gnu.org/software/grub/manual/html_node/index.html[/URL]

As for your Vista installation it is hard to see how installing Grub on
one hard disk could erase Vista from a another one. Is there some way to 
read the disk that Vista was installed on?

---

### Post by ranger0293 on 2006-11-05
Thanks for the help.

When I do a "root (hd2,0)" from a grub prompt, I get the error "Error 21: Selected disk does not exist".  Do I need to mount it or something first?  How would I go about doing that?

As for the Vista disk, yes the data is still there.  I can cd to it in the Vista command prompt mode, so the data is not corrupt.  I just assume that the boot record being overwritten confused everything somehow.

---

### Post by amohanty on 2006-11-05
Whoops missed that kubuntu is sdb try (hd1,0) instead
Sorry about that

AM

---

### Post by ranger0293 on 2006-11-05
Quick update:

I reinstalled, this time specifying "(hd2)" insted of the default "(hd0)" at installation time.  I restarted and got into GRUB thankfully, but it gave me an error (15 I think) that it couldn't mount the selected partition.

I edited the selection and changed the root(h2,0) to root(hd0,0) and it booted up Kubuntu. (hurray)

Now I need to go about getting Vista to be bootable.  Is there an easy way to add operating systems to it?  Hopefully the Vista install isn't broken.

---

### Post by amohanty on 2006-11-05
> I edited the selection and changed the root(h2,0) to root(hd0,0) and it booted up Kubuntu. (hurray)

Did you change the relevant entry in /boot/grub/menu.lst?
Could you post the contents of that file?

AM

---

### Post by confused57 on 2006-11-05
This thread may help:
[http://www.ubuntuforums.org/showthread.php?t=207870&highlight=vista](http://www.ubuntuforums.org/showthread.php?t=207870&highlight=vista)

---

### Post by ranger0293 on 2006-11-05
Yeah, I changed that file once I successfully booted into linux.

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
# kopt=root=UUID=4d704f6c-ae6e-42ca-ab61-8ec8ea3f66ef ro
# kopt_2_6=root=/dev/sdc1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdc1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by amohanty on 2006-11-05
Cool.

---

