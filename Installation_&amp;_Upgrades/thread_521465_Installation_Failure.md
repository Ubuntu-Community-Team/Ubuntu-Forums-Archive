---
title: "Installation Failure?"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by rjcambridgegembrook on 2007-08-09
I installed from a cd Feisty Fawn on:-
Intel Duo T2350 with 2Gb RAM with no OS previously installed. The installation went well apart from moaning about the Intel WM3945AGM2WB tri-band wireless card.
However when rebooting I'm informed that there is No Operating System! I've tried both ubuntu and kubuntu. Anything obvious I've missed?
:confused:

---

### Post by merlinus on 2007-08-09
You might try booting from a live cd, opening a terminal and post results of:

```
 
sudo fdisk -l
cat /boot/grub/menu.lst

```

-merlin

---

### Post by rjcambridgegembrook on 2007-08-09
After the last attempt, I illegally load Windows XP to check the system was bootable (it was),  I've reloaded ubuntu. 
menu.1st:-

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
# kopt=root=UUID=83c4dab3-7250-4920-9952-2bdb1ecfb3ce ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=83c4dab3-7250-4920-9952-2bdb1ecfb3ce ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=83c4dab3-7250-4920-9952-2bdb1ecfb3ce ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2007-08-09
/boot/grub/menu.lst looks okay.  

What about these:

```

sudo fdisk -l
blkid

```And just to be certain, is there a cd in the drive when restarting?

-merlin

---

### Post by rjcambridgegembrook on 2007-08-09
There was no CD in the drive. I've managed to almost boot by using the Live CD and choosing boot from first hard disk option.
Did I send you the default meno.1st last time as I sent the file. We is the output from blkid?

---

### Post by merlinus on 2007-08-09
You sent menu.lst, but not results of the other two terminal commands.

-merlin

---

### Post by rjcambridgegembrook on 2007-08-09
Sorry Merlin, I wasn't very clear. The terminal screen is blank after submitting the commands where does the result appear?
Oh I've just been summoned - it's 1-15 am here so I'll get back to you tomorrow - thanks for everything so far.

---

### Post by rjcambridgegembrook on 2007-08-10
sudo fdisk -l screen:-

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 82252800 bytes

     Device Boot                Start               End               Blocks              Id    System
/dev/sda1     *                       1            9327         74919096               83   Linux
/dev/sda2                       9328             9729           3229065                 5   Extended
/dev/sda5                       9328              9729          3229033+            82   Linux swap / Solaris


The other item to follow.blkid

blkid returns nothing just the prompt.

---

### Post by rjcambridgegembrook on 2007-08-10
Sorry, I'm being stupid when I type sudo blkid I get:-

/dev/sda1: UUID="83c4dab3-7250-4920-9952-2bdb1ecfb3ce" SEC_TYPE="ext2" TYPE="ext 3"
/dev/sda5: UUID="12de8d51-6ae9-4f74-9b2c-dfdd0917c84f" TYPE="swap"

---

### Post by merlinus on 2007-08-10
So far, everything looks as it should.

Do you get a grub menu upon startup?  It should have three options.

Since the default timeout is 3 seconds, press the down arrow when it appears (if it does).

-merlin

---

### Post by rjcambridgegembrook on 2007-08-10
When trying to boot without the live CD, it is so quick that by the time the screen is alive, it's trying the last option from the BIOS - PXE booting. I've looked at the bios but there seems to be noway of disabling pxe.

---

### Post by logos34 on 2007-08-10
Is the Bios still recognizing  the hard disk?  Should be set to 'auto'[detect]...Settings can change for no apparent reason.  Try setting the hard disk first, ahead of the cdrom, in device boot order.

---

### Post by rjcambridgegembrook on 2007-08-10
Checked the BIOS :
IDE Channel 0 Master was set to "Auto" 32 Bit I/O: was disabled but changing this made no difference. The hard disk was moved to boot option 1. - No luck.

---

### Post by rjcambridgegembrook on 2007-08-10
If I boot from hard disk from the CD menu, I can get GRUB, which has two versions of the kernal, both with recovery mode and a memtest86+.

---

### Post by merlinus on 2007-08-10
And do any of the grub options work?

-merlin

---

### Post by rjcambridgegembrook on 2007-08-10
They all seem to work but remember this is booting via the CD!

---

### Post by merlinus on 2007-08-10
You may be booting from the cd, but it seems that you are accessing your hard drive installation.

Try this:

```

cat /etc/fstab

```

-merlin

---

### Post by rjcambridgegembrook on 2007-08-10
will do thanks so far but I've got to go now.

---

### Post by rjcambridgegembrook on 2007-08-10
It says:

# /etc/fstab: static file system information
#
# <file system> <mount point>  <type>  <options>          <dump>   <pass>
proc                    /proc                  proc        defaults               0              0
# /dev/sda5
UUID=12de8d51-6ae9-4f74-9b2c-dfdd0917c84f    none                swap           sw             0         0
/dev/scd0         /media/cdrom0          udf, iso9660 user, noauto         0                 o

---

### Post by merlinus on 2007-08-10
According to this, your swap partition and cdrom are being mounted, but not your main linux partition (sda1).

Are you able to access any of your data folders and files?

-merlin

---

### Post by logos34 on 2007-08-10
you need to manually mount sda1:

menu bar>places>home folder>click on root on left panel to mount. (it will probably show up as 'disk')

now run cat /media/disk/etc/fstab

or navigate to it thu nautilus

---

### Post by merlinus on 2007-08-10
Hi, logos34.  You confirmed what I was thinking, that the /etc/fstab he posted was from the live cd and not hard disk installation.

But I wanted to be sure, so asked if could access any of his data.

Do you think a reinstall would be best?  Or are you suspecting something else?

I am surprised that the grub menu showed the various kernel and other options, though.

> 
If I boot from hard disk from the CD menu, I can get GRUB, which has two versions of the kernal, both with recovery mode and a memtest86+.


-merlin

---

### Post by rjcambridgegembrook on 2007-08-10
Hi,

Just rebooted via Live CD and run Cat / etc/fstab and got these results:-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=83c4dab3-7250-4920-9952-2bdb1ecfb3ce /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=12de8d51-6ae9-4f74-9b2c-dfdd0917c84f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


I can get the forum on the note book so these are genuine results not copies.


I think that I can get data files as I've saved and retreived a couple of test files. Before join the forum I tried to reload Ubuntu twice

---

### Post by merlinus on 2007-08-10
So your / partition is definitely listed, accorded to /etc/fstab.  Can you navigate to it via nautilus and see your data?

Also, once again, what does this give:

```

blkid

```

-merlin

---

### Post by rjcambridgegembrook on 2007-08-10
I can see my data using nautalus. 

blkid gives :-

rjc@rjc-laptop:~$ blkid
/dev/sda1: UUID="83c4dab3-7250-4920-9952-2bdb1ecfb3ce" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="12de8d51-6ae9-4f74-9b2c-dfdd0917c84f" TYPE="swap" 
rjc@rjc-laptop:~$

---

### Post by merlinus on 2007-08-10
So the UUID for entries in /etc/fstab are correct.

Just to review --

Does the grub menu appear when booting from your hard drive?

What is the default in /boot/grub/menu.lst?  (the entry is near the top of the file)

It was 0 in your original post of this file.  Change it to at least 10 so you can view the grub menu.

-merlin

---

### Post by rjcambridgegembrook on 2007-08-10
No the GRUB didn't appear when booting from hdd. I now change the setting and try again.

---

### Post by logos34 on 2007-08-10
> **merlinus said:**
> Hi, logos34.  You confirmed what I was thinking, that the /etc/fstab he posted was from the live cd and not hard disk installation.

But I wanted to be sure, so asked if could access any of his data.

Do you think a reinstall would be best?  Or are you suspecting something else?

I am surprised that the grub menu showed the various kernel and other options, though.

hi merlin,

about the only thing I can think to add is I just noticed "hiddenmenu" option is enabled.  Comment it out (#):

**#hiddenmenu**

But that doesn't explain why it just doesn't just load default kernel, or why OP can only boot from hard disk via live cd.  He's tried kubuntu and ubuntu.  I don't know what's up with the 'pxe' bios part--maybe it's trying to boot from the lan (I think you'll find settings under power mngmt in bios).  

"missing operating system" or "operating system not found" can mean something's wrong with the boot sector on the very first part of the disk (but why does windows work?)  edit: or rather why does it boot then via live cd?

Reinstall Grub to MBR?  Or try putting it on (hd0,0).

---

### Post by rjcambridgegembrook on 2007-08-10
It does boot in Windows albeit illegally, as a work round, I going to "hibernate" it tonight and see if its still alive in the morning, after all linux isn't like Windows requiring a boot every day? 
I'll rem out the "hiddenmenu"

---

### Post by logos34 on 2007-08-10
leave us this info:

what make and model lappy is this?  It'll help track down the mobo/bios info.  I'm more familiar with amd platforms, but it seems it may be trying to boot from a server on the network (even though not connected). Look under the boot tab in the bios for anything about PXE or network boot. (I thought it might be under power but I was confusing it with PME-WakeonLan).  If you can get the board info, Intel will have the answer somewhere.  

That's my stab in the dark at this problem.

---

### Post by rjcambridgegembrook on 2007-08-11
The machine is a clone PC Notebook MR052 Motherboad (Intel?) from Stone Computers (UK) - it is assembled in the uk - I've seen the production line. According to the test sheet:-
Intel CoreDuo processor T2350(1.86GHz). PheonixBIOS NAPA0001.86c.0000.X.0000000000.
Network Device: Intel WM3945AGM2WB Mini PCIe Tri Band Wireless
Memory: 2 * 1Gb Kingston 667 DDR 2 PC5300 200pin
Hard Drive: Hitachi 80gb SATA 150, 5400rpm 8mb Hard drive

Incidentally the unit was tested using an HPC Linux server image

---

### Post by logos34 on 2007-08-11
> However when rebooting I'm informed that there is No Operating System! I've tried both ubuntu and kubuntu....

After the last attempt, I illegally load Windows XP to check the system was bootable (it was), I've reloaded ubuntu....

When trying to boot without the live CD, it is so quick that by the time the screen is alive, it's trying the last option from the BIOS - PXE booting. I've looked at the bios but there seems to be noway of disabling pxe....

Checked the BIOS :
IDE Channel 0 Master was set to "Auto" 32 Bit I/O: was disabled but changing this made no difference. The hard disk was moved to boot option 1. - No luck....

If I boot from hard disk from the CD menu, I can get GRUB, which has two versions of the kernal, both with recovery mode and a memtest86+....

They all seem to work but remember this is booting via the CD!...

No the GRUB didn't appear when booting from hdd. I now change the setting and try again....

It does boot in Windows albeit illegally...

I guess I'm out out of my depth here because I just don't know why Grub doesn't come up when you boot directly from the hard disk.  Grub is there, it appears when you boot "from first hard disk" via the live cd menu screen, and you can get into ubuntu from there.  If it was a bios-related issue then you wouldn't be able to boot windows.  For some reason it just skips grub/hard disk and tries to boot from the network/pxe.  You've reinstalled (ubuntu and Kubuntu), so I doubt reinstalling grub to the mbr would help, although you could try putting it on the root partition:

> sudo grub
root (hd0,0)
setup (hd0,0)
quit

I had trouble tracking down your Intel-platform notebook, but it's probably a 945GM-based chipset.  (If this was a desktop, it would be relatively easy to find the manual). Even though this may not be a bios-problem after all, you could try either going through the interactive Setup or reset the bios to default (F9):

**[http://www.phoenix.com/en/Customer+Services/BIOS/BIOS+FAQ/default.htm#Q32](http://www.phoenix.com/en/Customer+Services/BIOS/BIOS+FAQ/default.htm#Q32)**

Maybe someone else has some ideas.

---

### Post by merlinus on 2007-08-11
The only other thing I can think of is to remove or disable the wireless card, and see what happens.

-merlin

---

### Post by rjcambridgegembrook on 2007-08-12
As a matter of interest, I load OpenSUSE instead and that wouldn't boot either but Windows does, so I can't return the computer! I'm now having difficulty in rebuild Ubuntu 7.04 but 6.10 (a DVD with Begging Ubuntu book installs (doesn't boot of course), so I'm going to download the update files.

I will disable the WiFi and remove the wired connection and try again!

---

