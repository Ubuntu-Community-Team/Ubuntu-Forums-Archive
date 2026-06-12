---
title: "GRUB error 15"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by tomane on 2006-11-03
Hi everyone. 

I just installed Edgy on my PC, dual booting windows. The installation procedure went without any major complaints. After rebooting I get the Grub menu with entries for utuntu and WinXP. If I choose winxp it boots OK but if I choose ubuntu I get an error 15( file not found), regardless of choosing "normal" or "recovery mode".

Here's my setup:
P-ATA Seagate 80GB hard drive (can't remember exact P/N as I'm not near my comp)
Here's my partitions:
(pri)1: NTFS <- WinXP is here
(pri)2:  100MB, bootable, mounted on /boot
extended partition:
3
3.1  ext3, mounted on /
3.2 ext3, mounted on /home
3.3 swap area

During instalation I chosen to install grub to (hd0,1), which I believe is the second partition, or /boot. The hard drive is configured as master on the primary IDE channel.

Does anyone have any clue regarding this? This is my third attempt to install edgy to no avail. Dapper instalation was far more smooth :(

When I get near my machine I'll double check /dev/hda1 (/root) and see if vmlinuz exists there. 
If you need any aditional info, ask I'll try to post it.

Thanks in advance.

---

### Post by tomane on 2006-11-03
Just a thought, it grub is loading correctly and the menu is working as I can boot WinXP.
In case the kernel executable is missing from /boot, is it possible to install it to /boot without the need to reinstall the whole OS? I'v done two instalation attempts and this whole process is getting pretty tedious...

cheers,
--to

---

### Post by boban on 2006-11-03
Have you checked if kernel is really there? 

Post your /boot/grub/menu.lst...

Error 15 means that grub couldn't find file (in this case - your kernel)

---

### Post by tomane on 2006-11-03
OK, I finally managed to get home and now I'm using the live CD on my PC.

I mounted /dev/hda2, which is the partition for '/boot'
Here is the output of ls -la:
```
drwxr-xr-x 4 root root    1024 2006-11-03 20:49 .
drwxr-xr-x 3 root root      80 2006-11-04 00:54 ..
-rw-r--r-- 1 root root  285604 2006-10-13 19:09 abi-2.6.17-10-generic
-rw-r--r-- 1 root root   74645 2006-10-13 16:13 config-2.6.17-10-generic
drwxr-xr-x 2 root root    1024 2006-11-03 20:49 grub
-rw-r--r-- 1 root root 5697442 2006-11-03 20:49 initrd.img-2.6.17-10-generic
drwxr-xr-x 2 root root   12288 2006-11-03 20:34 lost+found
-rw-r--r-- 1 root root   94600 2006-10-20 11:44 memtest86+.bin
-rw-r--r-- 1 root root  728690 2006-10-13 19:09 System.map-2.6.17-10-generic
-rw-r--r-- 1 root root 1636681 2006-10-13 19:09 vmlinuz-2.6.17-10-generic

```Also, here's the content of /boot/grub/menu.lst:
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=1d2fb6ef-6821-4331-93cf-16327f92624f ro
# kopt_2_6=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
chainloader     +1

```
Can you find anything unusual here? :confused:

cheers,
--to

---

### Post by confused57 on 2006-11-03
I'm not sure, but if hda3 is an extended partition I would think your root would be on a logical parititon on hda4, root (hd0,3).
  When the grub menu displays, you could try highlighting the Dapper entry, press "e" & try changing the root to (hd0,3) and changing the kernel line to hda4...something you could try.

---

### Post by tomane on 2006-11-03
[OK, this is being rather stressfull and unstable; I'm trying to write this post while my machine keeps hanging. Good Thing, that firefox saves session data.....]

Thanks, for the sugestion, confused.

I tried it and changing from hda3 to hda4 results in error 17 (unable to mount partition). (hd0,2) to (hd0,3) yealds the same result. Maybe I have '/' as a primary partition. anyway, I should be sleeping quite some time ago so I can't confirm this...

I actually already managed to boot Edgy with a dirty trick.
Using the live CD I went to ckeck the menu.lst (via ssh) of my webserver running Dapper. The difference that I noticed is that the 'root ...' line points to /boot instead of '/' and that kernel and initrd are writen with an "absolute path relative to /boot", so created a modified entry in my menu.lst as follows:

title        Ubuntu, kernel 2.6.17-10-generic TEST_2
root        (hd0,1)
kernel        /vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd        /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

I basically made root point to /boot and changed the kernel and initrd paths to look like absolute, relative to /boot.

Now the system boots, but when fsck runs and exits with error 8
This is the error log:
```
Log of fsck -C -R -A -a 
Sat Nov  4 02:04:09 2006

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=E2A6-2D80' 
/dev/hda5: recovering journal
/dev/hda5: clean, 207/1974720 files, 96951/3943949 blocks
fsck died with exit status 8

Sat Nov  4 02:04:09 2006
----------------

```Looking at /dev/disk/by-uuid/ I have a symlink named E2A6-2D80, which pints to ../../hda1, i.e., the /boot partition.

What might be going wrong here?

Edgy has been showing quite a few sharp edges for me... ](*,)

cheers.
--to

---

