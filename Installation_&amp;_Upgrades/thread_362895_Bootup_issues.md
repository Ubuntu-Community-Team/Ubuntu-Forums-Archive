---
title: "Bootup issues"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by dhoodle on 2007-02-16
Hey all...

I would like to start with - **[COLOR="DarkOrange"]I am a complete and utter newbie[/COLOR]**:lolflag: 

I have setup ubuntu on a fresh HDD - 60GB partitioned - 15GB and 45GB...

I had no idea what was happening with the partition and boot setup - but I vaguely remember making the 15GB mount the / and the 45GB mount the /Swap...... *(unsure if it is the right wording, hopefully you know what I mean)*

Ok so when I restarted the machine - I get the error - **No Boot Drive found** *(or something along those lines)*

So i poped the ubuntu install disk in again and got to the menu, and booted from HDD - and went into the OS...

I have no idea where I went wrong - but i have a hunch that it was when i was blindly configuring the boot setup and partitions....

any ideas guys - and i dont really want to set it up again - I have configured everything else on it now.. such as networking with windows etc.

Thanks in advance :D

---

### Post by Kateikyoushi on 2007-02-16
I bet you did not install grub and also if your swap partition is either 15 or 45GB you would better resize it it is a total waste to make it bigger than 1 GB.
You can resize it from the live cd with using gparted.
Check this guide to install grub on your hard disk. [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by mikewhatever on 2007-02-16
Recheck that your hard drive is set as a boot device in the BIOS. 15GB for root (/) looks right, but 45 GB for swap is really a waste. You do not need more then 1GB for that. If you decide to redo it, please use a guide
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
and write down whatever you're doing, just to have a clearer picture.

---

### Post by dhoodle on 2007-02-16
ok,

I tried **[COLOR="DarkOrange"]Kateikyoushi[/COLOR]** way, reinstalling the grub - but this did not work...

My HDD is the primary boot device....

i resized the swap with gparted also...

what am i missing ?

---

### Post by dhoodle on 2007-02-16
The error i am receiving is: **Hard Disk boot sector invalid.**

I have configured the grub - i may have to reinstall...

---

### Post by dhoodle on 2007-02-16
can anyone help ?

---

### Post by dhoodle on 2007-02-16
jeez....

Reinstalled the whole thing, restructured my partitions, but still cannot boot...

---

### Post by Kateikyoushi on 2007-02-16
What is your hard drive setting in Bios ?
Auto LBA large ? It might be that the disc geometry is not read correctly.

---

### Post by dhoodle on 2007-02-17
BenQ Notebook - Joybook A32

**[COLOR="DarkOrange"]Devices[/COLOR]**
IDE Primary - Fujitsu MHT206AT
IDE Second - MATSHITAUJ-840D

**[COLOR="DarkOrange"]Boot Sequence - [/COLOR]**
1. HDD
2. CD
3. LAN
4. Floppy



**[COLOR="DarkOrange"]GParted Partitions.[/COLOR]**

/dev/hda1 - EXT3 - 14.65GB    -  /
/dev/hda2 - EXTENDED
      /dev/hda5 - SWAP - 996MB - Swap
      /dev/hda6 - EXT3 - 40.27 GB       - /home


When I set the GRUB up in the install I chose (hd0) - unsure if this is correct or do i use (hd1) becuase the / folder is set up on hda1 ?

Thanks in advance

---

### Post by Kateikyoushi on 2007-02-17
It is best if you install grub in the MBR which is hd0.

---

### Post by dhoodle on 2007-02-17
ok, so i have done everything right - so what could be going on... I can get into the system if i boot from the CD and use the Boot from first HDD option...

I have no idea...

why is Linux so hard ? lol

---

### Post by dhoodle on 2007-02-18
anyone ?

---

### Post by bulldog on 2007-02-18
> **dhoodle said:**
> anyone ?
It seems you have GRUB on hd0 and ubuntu on hd1,so it's very possible GRUB points to the wrong partitions.
To see if that is the case you have to provide us your menu.lst so we can see.

If you can boot into your ubuntu install try this```
cat /boot/grub/menu.lst
```in your terminal and copy the output to the forum.

---

### Post by dhoodle on 2007-02-18
OK - here it is...

is there an easy way to change this ? or will I have to reinstall for a 3rd time ? :lolflag: 

```

dhoodle@dhoodle-laptop:~$ cat /boot/grub/menu.lst
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
timeout         3

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
# kopt=root=UUID=a085b90f-aeb9-4bf4-8e30-c43f3d3e828e ro
# kopt_2_6=root=/dev/hda1 ro

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
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by bulldog on 2007-02-18
No you won't have to reinstall as far as I can see.
There seems to be nothing wrong with the menu.lst,can you provide me the output of```
sudo disk -l
``` and ```
cat /boot/grub/device.map
```

---

### Post by dhoodle on 2007-02-18
ok

This code came up with nothing ? is this bad ?
```
dhoodle@dhoodle-laptop:~$ **sudo disk -l**
Password:
sudo: disk: command not found
```



```

dhoodle@dhoodle-laptop:~$ **cat /boot/grub/device.map**
(hd0)   /dev/hda
```

---

### Post by bulldog on 2007-02-18
Sorry my mistake,it should be ```
 sudo fdisk -l
```

**EDIT**
You've stated there where two hdd's in your system,may I ask were the second one is?
Devices
IDE Primary - Fujitsu MHT206AT
IDE Second - MATSHITAUJ-840D

---

### Post by dhoodle on 2007-02-18
```
dhoodle@dhoodle-laptop:~$ **sudo fdisk -l**

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1912    15358108+  83  Linux
/dev/hda2            1913        7296    43246980    5  Extended
/dev/hda5            1913        2039     1020096   82  Linux swap / Solaris
/dev/hda6            2040        7296    42226821   83  Linux
```

---

### Post by dhoodle on 2007-02-18
i believe that the other one is the DVD...

---

### Post by bulldog on 2007-02-18
See my previous post Edit....

You have to understand that if you've installed ubuntu with two hdd's connected,and disconnecting one after that,you're heading for trouble.

---

### Post by dhoodle on 2007-02-18
nah i didnt do that mate - i believe that one of them is the DVD Drive...

can you see anything else wrong with it ?

---

### Post by bulldog on 2007-02-18
> **dhoodle said:**
> ```
dhoodle@dhoodle-laptop:~$ **sudo fdisk -l**

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1912    15358108+  83  Linux
/dev/hda2            1913        7296    43246980    5  Extended
/dev/hda5            1913        2039     1020096   82  Linux swap / Solaris
/dev/hda6            2040        7296    42226821   83  Linux
```

Okay one hdd and one DVD,I can live with that :) 

But another thing I don't understand is:/dev/hda1 =Linux and /dev/hda6 =Linux.
You boot from hda1 but are you sure this is your ubuntu or should it be hda6?

**EDIT**
To be sure which one you have to use you can use the live cd to reinstall grub and correct the errors.
If you have boot into the live cd,open a terminal and,
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

If you get a response of hda6 on the find command,that is were things where going wrong.

---

### Post by dhoodle on 2007-02-18
the hda 6 - I made it as /home... it is the left over space(40GB)

i have done this, and it comes up (hd0,0)....

i dont know...

---

### Post by bulldog on 2007-02-18
I don't know either,your settings look good to me,you can have a look in fstab to see if the partition with root is properly listed there,otherwise I can't think of any thing else to do.

---

