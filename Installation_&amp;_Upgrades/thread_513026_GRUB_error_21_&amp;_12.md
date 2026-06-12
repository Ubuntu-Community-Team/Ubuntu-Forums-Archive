---
title: "GRUB error 21 &amp; 12"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by steiny on 2007-07-30
Hi,

I have read through a couple of "how to"s but I'm still stuck. 

I have 2 80GB hard drives configured with RAID (the details of this I don't know, my friend set this up for me ages ago).I had Vista installed on C: and D: has all my files and backups etc. on it.

I used the Vista partition tool and partitioned C: with around 15GB (can't remember exactly). Then I used the Live CD of Ubuntu 7.04 to install. I created a partition of 1GB for the SWAP and 15GB as ext3. (I'm not sure what the story is with all the partitions etc. while installing it said I have about 80000MB of free space which seems a little odd)

Then when I restarted I got the following message:
"GRUB loading stage 1.5.
GRUB loading, please wait...
Error 21"

I tried following the post for reinstalling GRUB and the GRUB command "find /boot/grub/stage1" returns:
"(hd1,1)"

Then I tried the GRUB command "setup (hd1)" but this threw the following error:
"Error 12 - invalid device request"


Here is the output from sudo fdisk -l:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8099    65049312+   7  HPFS/NTFS
/dev/sda2            9729       19458    78156225    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         124      995998+  82  Linux swap / Solaris
/dev/sdb2             125        1991    14996677+  83  Linux


Well it seems I may have just found a major problem while writing this, the /boot/grub/menu.lst file seems to be completely empty.

---

### Post by Shazaam on 2007-07-30
Maybe I am having a senior moment here but according to fdisk it looks like you lost half of your raid array. Can you still boot Windows? Could be you have a first generation motherboard that used onboard raid to access SATA disks. My Soyo KT600 is like that.

sda= one hard drive.
sdb= the other hard drive.
Was this a Raid0 setup?

---

### Post by steiny on 2007-07-30
No I can't boot windows because GRUB tries to start each time and throws the error then it just sits there with a "_" prompt.

Im not sure what kind of raid it is, how do I find out?

So does this mean all my data on both is lost due to how raid works? Sorry Im a bit of a noob (but I learn pretty fast). I backed up all my uni work its just a few saved games I will have lost but no biggy.

---

### Post by confused57 on 2007-07-30
> **steiny said:**
> No I can't boot windows because GRUB tries to start each time and throws the error then it just sits there with a "_" prompt.

Im not sure what kind of raid it is, how do I find out?

So does this mean all my data on both is lost due to how raid works? Sorry Im a bit of a noob (but I learn pretty fast). I backed up all my uni work its just a few saved games I will have lost but no biggy.
You might try reinstalling Window's IPL to the Windows drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you have access to another pc, the Super Grub Disk is probably the easiest method.

---

### Post by Raincaller on 2007-07-30
I am having similar issue.

I run 2x150GB Raptors in RAID 0 where Vista 32 bit (the horror) is. 

Then I have 2 extra 250 gb disks, and installed Ubuntu on one. 

Result: Grub error 21

I have tried swapping boot orders from BIOS, etc, but nothing seems to help. 

I need to use Super GRUB disk to boot to windows. 

Could really use help as well if anyone can. 

I keep experimenting with this and if I become any wiser I post here.

---

### Post by Ryoushi19 on 2007-07-30
If you used the Vista partition tool to make the partition, that itself is your problem.  Vista creates an "NTFS" partition, which is 100% incompatible with Linux.  Partition with the LiveCD.  Also, if you somehow managed to partition an ext3 system with Vista, use e2fsck to check for errors.

---

### Post by steiny on 2007-07-31
Ok I've read a little bit and learned a few things since (I really shouldnt have jumped into dual booting so quickly).

BTW: I'm using the LiveCD to boot at the moment so at least I can boot with that for now.

> **Ryoushi19 said:**
> If you used the Vista partition tool to make the partition, that itself is your problem.  Vista creates an "NTFS" partition, which is 100% incompatible with Linux.  Partition with the LiveCD.  Also, if you somehow managed to partition an ext3 system with Vista, use e2fsck to check for errors.

That makes sense, although why it in the tutorial: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
I do not know.

I tried SuperGRUB on a USB and went through the tutorial at: [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
and everything seemed to go ok. I changed my BIOS to boot from USB but then it seemed to be stuck at "Verifying DMI Pool Data........" and never goes any further.

As you probably already figured out, the root partition Ubuntu is installed on is sdb2, and the SWAP on sdb1. With the LiveCD my root partition is being mounted at /media/disk. The directory /boot is empty but /media/disk/boot has all the grub files in it.

I tried installing GRUB on the root partition (sdb2) via the method in post #5 of:
[http://ubuntuforums.org/showthread.php?t=24113&highlight=howto+fix+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=howto+fix+grub)
With the GRUB setup command, should I have used (hd1,1) or (hd1)? I used (hd1,1). I'll wait for your response before trying anything else so I don't do anything I shouldn't.

---

### Post by steiny on 2007-07-31
Just in case you need it, here is the contents of /media/disk/boot/grub/menu.lst


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
# kopt=root=UUID=deb34387-bc22-4727-8bba-83f91040056f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=deb34387-bc22-4727-8bba-83f91040056f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=deb34387-bc22-4727-8bba-83f91040056f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by steiny on 2007-07-31
I've tried installing GRUB to both (hd1,1) and (hd1) but neither worked, I still get GRUB Error 21 when booting.

Also I still cannot get Super GRUB to boot off the USB.

I will try install the GAG Boot Manager when I get home, but if anyone can shed light on my problem I will be very grateful

---

### Post by steiny on 2007-08-03
I give up

---

