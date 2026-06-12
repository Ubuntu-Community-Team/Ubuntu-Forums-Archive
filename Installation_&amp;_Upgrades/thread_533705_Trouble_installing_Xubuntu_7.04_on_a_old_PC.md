---
title: "Trouble installing Xubuntu 7.04 on a old PC"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by tiachopvutru on 2007-08-24
When I install I get this error:

The ext3 file system creation in partition #1 of IDE1 master (hda) failed.


I have used gparted and erase all partitions and format them to ext3, but the same message keeps popping up.

I don't know what I'm doing wrong here and obviously don't know what I'm doing, either.

It's an old PC. It has the Pentium 3 sticker and I think, 320MB of RAM. (not really sure though)

---

### Post by Pumalite on 2007-08-24
Go to BIOS and make sure all your drives are recognized (IDE Conf). Check your drives with rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by tiachopvutru on 2007-08-24
Pardon but can I have a more detailed instruction regarding the sysresccd? Also, I don't know how to access the BIOS but I already burned the disc containing sysresccd runs fine when I bootup my computer

---

### Post by Pumalite on 2007-08-24
Accessing the BIOS is essential, since the probabilities of your problem to be there are greater. Consult your motherboard manual. In general: (at the time of boot, hitting repeatedly) DEL, Esc, or Tab are some of the keys that work in different computers.

---

### Post by A3sthetix on 2007-08-24
BIOS access: usually when booting up, the PC will prompt "Press FX for Setup"

It might be F2 or ESC or something like that.

---

### Post by A3sthetix on 2007-08-24
Out of curiosity, while installing, did you format the drive? You might need to start fresh. Definitely check your drive.

---

### Post by ArtF10 on 2007-08-24
Something similar happend to me although it wasn't the same error message.  I found AFTER SEVERAL ATTEMPTS, that XUbuntu needs to have the specific partition(s) pointed out to it while the Ubuntu LiveCD does not require this, when installing to the ENTIRE drive.  Maybe just the way I did things but still.....

I created an extended partition, with a /home, / and swap partition and just selected manual partition.  I then specified the two partitions (there's onyl one swap so it picks it up automatically), edited them (when selected you get the option to edit them) and specified which one I wanted as / and which as /home.

After reading through a LOT of threads on here I was "counseled" by quite a few people to have a /boot partition as well although I haven't but it is not something I will be too concerned about right now since I am new here.

---

### Post by tiachopvutru on 2007-08-24
> **A3sthetix said:**
> Out of curiosity, while installing, did you format the drive? You might need to start fresh. Definitely check your drive.

Yes, before I did the install, I did reformat the drive (using gparted). I have had two attempts when 1) I just deleted the partitions 2) I reformatted it into ext3.


> **ArtF10 said:**
> Something similar happend to me although it wasn't the same error message. I found AFTER SEVERAL ATTEMPTS, that XUbuntu needs to have the specific partition(s) pointed out to it while the Ubuntu LiveCD does not require this, when installing to the ENTIRE drive.  Maybe just the way I did things but still.....

I created an extended partition, with a /home, / and swap partition and just selected manual partition.  I then specified the two partitions (there's onyl one swap so it picks it up automatically), edited them (when selected you get the option to edit them) and specified which one I wanted as / and which as /home.

After reading through a LOT of threads on here I was "counseled" by quite a few people to have a /boot partition as well although I haven't but it is not something I will be too concerned about right now since I am new here.

In other word. I need to manually partition it? That sucks since I don't understand what those /home, / , swap, and /boot suppose to be and where they belong. And I can't really do a lot of reading right now. I was trying to install Xubuntu thinking it would be Insert CD done like how I did with Ubuntu on the same machine (that I later uninstalled) and ended up staying up all night. Should I just go off to Ubuntu? The RAM is okay, I think, but the processor's clock speed is pretty low, like between 400 MHz - 500 MHz. It should probably run fine (but slow) except I have to do the whole wireless configuration again which I forgot how. XD

---

### Post by dulbirakan on 2007-08-24
> **ArtF10 said:**
> Something similar happend to me although it wasn't the same error message.  I found AFTER SEVERAL ATTEMPTS, that XUbuntu needs to have the specific partition(s) pointed out to it while the Ubuntu LiveCD does not require this, when installing to the ENTIRE drive.  Maybe just the way I did things but still.....

I created an extended partition, with a /home, / and swap partition and just selected manual partition.  I then specified the two partitions (there's onyl one swap so it picks it up automatically), edited them (when selected you get the option to edit them) and specified which one I wanted as / and which as /home.

I had the exact same problem a while ago when I tried to install Xubuntu on a machine that was too slow for Ubuntu. 

I think tiachopvutru does not need to check bios settings or disk integrity because the disk can be detected from gparted.

I guess Art's solution would solve the problem...

More information on recovery cd's: [UBCD]("http://www.ultimatebootcd.com/")

---

### Post by dulbirakan on 2007-08-24
> **tiachopvutru said:**
>  In other word. I need to manually partition it? That sucks since I don't understand what those /home, / , swap, and /boot suppose to be and where they belong. And I can't really do a lot of reading right now.

I am no expert myself but as far as I know you should create a partition that is double the amount of your ram (e.g. if you have 256MB of ram you should partition 512MB) as swap space and the rest can be "/" . As far as I know /home is optional and is required to store user's files like home folder so anything left after "/" (where the OS will be set) and Swap should be good for it.

---

### Post by tiachopvutru on 2007-08-24
Alright, thanks for the help I was able to successfully install Xubuntu 7.04

However, my computer is obsessed of the Xubuntu CD (I think), it won't start Xubuntu... (Something about the drive, but I don't understand it at all)

Anyway, after the install, my computer was restarted, the drive was ejected and I took the CD out. Press the drive back in. Then press ENTER. Afterward, it rebooted again and now I see this



Verifying DMI Pool Data .........
Boot from ATAPI CD-ROM : Non Bootable CD ...
Not found any [active partition] in HDD
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER


So, what do I do? :confused:

---

### Post by merlinus on 2007-08-24
You probably need to set the boot flag on your xubuntu partition.

You can use gparted live cd to do this.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by tiachopvutru on 2007-08-24
I have swap on partition #1 and ext3 mounted / as partition #2. So do I choose either 1 of these 2 options?

[B]Boot partition #1 on first hard drive
Boot partition #2 on first hard drive[/B]


Or do I choose "**Boot MBR on first hard drive**"?

---

### Post by merlinus on 2007-08-24
I would try boot partition #2 first, and if that does not work, boot mbr.

Booting your swap partition will most likely not work.

-merlin

---

### Post by tiachopvutru on 2007-08-24
Yay, it runs. Couldn't boot from partition #2 but booting from MBR did the trick. The thing is, do I have to do the same thing everytime I turn the computer on? :confused:  What could possibly be the problem, btw? I'm pretty sure it's not hard drive failure...

---

### Post by merlinus on 2007-08-24
Are you using grub to boot xubuntu?  Does a menu appear?

Also, post output of:

```

cat /boot/grub/menu.lst

```

-merlin

---

### Post by tiachopvutru on 2007-08-24
I don't really understand what you mean by using GRUB to load Xubuntu (I'm still nab)...

As for the code. Do I run it in terminal? I try to open it but everytime it just goes to a black screen (with some words on it) then instantly changes back to logon screen and then I have to log on again

---

### Post by merlinus on 2007-08-25
If you cannot get a terminal to work, then something is probably wrong with your installation.

grub is the bootloader used by ubuntu.  

Can you open Thunar (file manager) and navigate to File System/boot/grub and see if menu.lst is in there?

-merlin

---

### Post by tiachopvutru on 2007-08-25
Yes, it's there. I put it into a USB flash drive and transfer it to this computer and then open the file with Microsoft Word. Here's what's inside

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
#      password --md5 **[taken out]**
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
# kopt=root=UUID=73b9543b-5d03-481c-bf42-53655b68cdf9 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=73b9543b-5d03-481c-bf42-53655b68cdf9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=73b9543b-5d03-481c-bf42-53655b68cdf9 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```


Oh, and if you are wondering, I took out the password when I pasted this

---

### Post by merlinus on 2007-08-25
It looks correct.  If you place a # in front of the hiddenmenu line (near the top of the file), the grub menu will appear upon startup.  That way you will have some control over the booting process.

-merlin

---

### Post by tiachopvutru on 2007-08-25
I can't save after I edit it. It says "Can't open file to write"

And I'm able to open the terminal now. It's a bug on Xubuntu 7.04 according to a thread I read.

---

### Post by merlinus on 2007-08-25
Try this in the terminal:

```

sudo nano /boot/grub/menu.lst

```

Nano is a text-editor.  This command will allow you to open the file with root privileges so you can edit and save.

If you get a message that nano cannot be found, look in your menus for the name of the installed text editor and substitute that.

-merlin

---

### Post by tiachopvutru on 2007-08-25
I'm able to change the menu.lst but when I restart I still receive the BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER error :confused:

Does it have anything to do with the BIOS. I checked and it is CDROM, A, C.

---

### Post by merlinus on 2007-08-25
If you can boot into xubuntu, run this command in a terminal and post output:

```

sudo fdisk -l

```

My best guess is that you will have to set the boot flag on your xubuntu partition, and then reinstall grub:

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```

Substitute results from find for (hdx,y) and setup (hdx).  It will probably be (hd0,1).

-merlin

---

### Post by tiachopvutru on 2007-08-25
Here's what I got from sudo fdisk -l

```
Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          62      497983+  82  Linux swap / Solaris
/dev/hda2              63        1027     7751362+  83  Linux
```


I'm currently doing the rest of the stuff right now

EDIT:
Done with it. Still receive the boot failure. Actually... how do I set a boot flag?

---

### Post by merlinus on 2007-08-25
Use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It will show your partitions, and there is an option to set the boot flag.  Set it on hda2 -- your main xubuntu partition.

That may be why your computer is giving the error message --

Not found any [active partition] in HDD.

-merlin

---

### Post by tiachopvutru on 2007-08-25
Hurray! It now boot without the need of gparted disc.

Thanks for taking your time, constantly checking back and for your patience... Right now I'm pretty much good to go but I still have one more question. A few hours ago I went to BIOS Setup and checked Load BIOS Default and now I have no idea how to undo it. It's not terribly important, just that I feel I'm better off not having to be greeted by the screen that tells me to press F1 to continue or DEL to enter Setup, especially that I would rather not having to press F1 everytime I power up my computer.

---

### Post by merlinus on 2007-08-25
Glad it is finally working!

As to having to press F1 to continue, I am not certain what BIOS setting may be causing that.  Have a look in there.

It may simply be normal for your machine.

Good luck!

-merlin

---

### Post by tiachopvutru on 2007-08-25
I found a way to disable it. I went Setup and find Halt On and chose No Error option. Now there's only wireless to go but I'm probably able to do it myself. Thank you for your help.

---

