---
title: "Dual booting XP/Ubuntu, lost my XP partition?"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by SnowPunk98 on 2007-02-19
So I had Windows XP and Ubuntu (Edgy) setup and running fine on my Dell E1705 laptop. This laptop has a "feature" called MediaDirect which I guess hides itself in a HPA ([http://en.wikipedia.org/wiki/Host_Protected_Area](http://en.wikipedia.org/wiki/Host_Protected_Area)) which I thought I had gotten rid of but apparently not. 

Anyways, I accidentally pushed the MediaDirect button on the laptop and it started booting this deal and I powered it off in hopes of saving my partitions. To my dismay I was able to bring up Ubuntu fine but Windows seems like its gone. If I choose Windows from GRUB it starts the MediaDirect and my Windows partition no longer shows up in Linux.

Anyone know how I can salvage my Windows OS or is it gone? If it is gone what is the best way to restore Windows without screwing up linux?

---

### Post by orb9220 on 2007-02-19
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

Will rerun the grub install which should see your xp partition.

---

### Post by Poisond on 2007-02-19
Hi Snowpunk,

I'm a total newb at linux, just installed it today actually. 

Anyways before I installed it, I was notified to download and burn a cd called Super Grub Disk. Url: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Apparently this program can repair both windows and linux mbrs, dunno if that helps any.

If you don't believe that the mediadirect program formatted the xp partition or drive, dunno if you have 2 separate drives or partitioned drives.

I have used the following program numerous times to help me recover data that is "lost".
Url: [http://www.recoversoft.com/](http://www.recoversoft.com/)

It is alot of money but its already paid for itself 3 times for me. Nothing sucks more than losing data, I can personally vouch for this program.

Good Luck.

---

### Post by SnowPunk98 on 2007-02-20
I can see the XP partition from GRUB but when I select it MediaDirect starts instead of XP.

Thanks for the info poisond I will check it out.

---

### Post by mikewhatever on 2007-02-20
The links above should be useful, but if you need more help, post the output of these two:
sudo fdisk -l
sudo gedit /boot/grub/menu.lst

---

### Post by SnowPunk98 on 2007-02-20
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        8863        9123     2096451    c  W95 FAT32 (LBA)
/dev/sda2            1913        6374    35841015    7  HPFS/NTFS
/dev/sda3            6375        9729    26949037+   5  Extended
/dev/sda5            6375        7649    10241406   83  Linux
/dev/sda6            7650        7776     1020096   82  Linux swap / Solaris
/dev/sda7            7777        9729    15687441    b  W95 FAT32
```

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
# kopt=root=UUID=caf7de0d-941f-4049-9922-66113b7326c7 ro
# kopt_2_6=root=/dev/sda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

# title		Ubuntu, kernel 2.6.17-10-generic
# root		(hd0,4)
# kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
# initrd		/boot/initrd.img-2.6.17-10-generic
# quiet
# savedefault
# boot

# title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
# root		(hd0,4)
# kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
# initrd		/boot/initrd.img-2.6.17-10-generic
# boot

# title		Ubuntu, memtest86+
# root		(hd0,4)
# kernel		/boot/memtest86+.bin
# quiet
# boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by mikewhatever on 2007-02-20
There seems to be a problem in this section:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
your Windows partition is sda2, which is (hd0,1) in terms of GRUB. Try changing the number from 0 to 1. To edit the file:
gksudo gedit /boot/grub/menu.lst

save and exit. It should boot OK now, but I wonder how it got changed like this.:confused:

---

### Post by SnowPunk98 on 2007-02-20
Cool, I will try that when I get home. I think what happened is when I pushed the MediaDirect button it took itself out of the HPA and reinstalled the application in the hidden space or something and pushed XP out of the way. 

If this were actually the case wouldn't I be able to also add an entry to GRUB to boot that as well?

---

### Post by confused57 on 2007-02-20
> **SnowPunk98 said:**
> 

If this were actually the case wouldn't I be able to also add an entry to GRUB to boot that as well?

Yes, you could do that...when I first installed Ubuntu on my Dell, I had root (hd0,0), which actually booted into the Dell Utility on the first partition...root (hd0,1) booted to Windows.

---

### Post by SnowPunk98 on 2007-02-21
Well I made the change but got a nice NTLDR is missing message so it looks like MediaDirect screwed up my Windows partition. I think I am going to try the following, and maybe fixboot fixmbr but I dont want to screw up linux.

Windows XP users

   1. Insert the Windows XP bootable CD into the computer.
   2. When prompted to press any key to boot from the CD, press any key.
   3. Once in the Windows XP setup menu press the "R" key to repair Windows.
   4. Log into your Windows installation by pressing the "1" key and pressing enter.
   5. You will then be prompted for your administrator password, enter that password.
   6. Copy the below two files to the root directory of the primary hard disk. In the below example we are copying these files from the CD-ROM drive letter "E". This letter may be different on your computer.

      copy e:\i386\ntldr c:\
      copy e:\i386\ntdetect.com c:\

   7. Once both of these files have been successfully copied, remove the CD from the computer and reboot.

---

### Post by confused57 on 2007-02-21
I've seen those instructions, but have never actually had to follow them(I've been lucky)...good luck, hope it works.

If it doesn't you could always try replacing:

root (hd0,1)

with

rootnoverify (hd0,1)

Sometimes it works in certain situations.

---

