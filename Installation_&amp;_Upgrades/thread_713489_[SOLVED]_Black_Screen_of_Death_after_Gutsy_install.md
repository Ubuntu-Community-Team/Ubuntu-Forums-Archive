---
title: "[SOLVED] Black Screen of Death after Gutsy install"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Boss Happy on 2008-03-02
I'm having a heck of a time installing Gutsy x86_64.  After several attempts and swapping motherboards in and out, I'm calling for help.

I have the following:
Intel Quad Core Q6600
4 GB RAM
Gigabyte GA-P35-DS3L LGA775 Motherboard
e-GeForce 8600 GT Graphics Card
Western Digitial Caviar 500 GB SATA Drive

The installation for the LiveCd of Gutsy, goes without incident.  However, on the reboot, I get to

"Grub Loading" message then the  black screen of death.

I don't understand why this installation isn't working.

Any help is appreciated.

---

### Post by wednesday allfather on 2008-03-02
Shot in the dark here.  I had a similar problem during installation.  I was using 32 bit install on a 64 bit system.  I think your system could be either one.  I just got the disks mixed up, and it bothered me for a day before I realized the mistake.

---

### Post by Boss Happy on 2008-03-03
Unfortunately, I'm using the 64 bit install.

---

### Post by BillDozer on 2008-03-03
Do you get error messages or is it just a totally black screen?

I had a problem when I added an extra graphics card to my PC, it would start with the first card and then after grub it would output to the onboard card.

---

### Post by Boss Happy on 2008-03-03
A totally black screen, no error messages.

I've been reading through other posts, and I think it's down to:

[LIST=1]
[*]SATA Issues
[*]GRUB menu not detecting correct partition
[*]Video Card
[*]All three
[/LIST]

---

### Post by BillDozer on 2008-03-03
Do you have a built-in videocard and a PCI/AGP videocard?

---

### Post by Boss Happy on 2008-03-03
No just a PCI card (by the way, I greatly appreciate your help :))

---

### Post by BillDozer on 2008-03-03
Can you press Esc to get into the grub menu?

Otherwise, you can try to put in the Live CD and start it up and check whether or not you can access your harddisk.

---

### Post by Boss Happy on 2008-03-03
I'm pretty sure the Esc key won't work, but I'll check when I get home.  What's the next step?

---

### Post by BillDozer on 2008-03-03
If the Esc key works. Then you can remove the splash and quiet from the boot option. Then you can check where the boot of the system hangs...

---

### Post by Boss Happy on 2008-03-03
The last  lines that appear are:

```

Begin: Running /scripts/local-premount ...
kinit: name_to_dev_t(/dev/disk/by-uuid/8582e6ae-7893-40bc-bb88-f260dd71aba2) = sda1(8,1)
kinit: trying to resume from /dev/disk/by-uuid/8582e6ae-7893-40bc-bb88-f260dd71aba2
[   29.206058] Attempting manual resume
kinit:  No resume image, doing normal boot...
Done.
[   29.246464] kjournald starting.  Commit interval 5 seconds
[   29.246472] EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ..
Done.
init: Error parsing configuration: No such file or directory
[   29.048756] Kernel panic - not syncing: Attempted to kill init!
```

Unfortunately, I don't know where the log file is, if you need the whole file, please point me in the right direction.

Thanks.

---

### Post by BillDozer on 2008-03-04
I assume that you could press the Esc key to edit grub and boot.

Unfortunately I am not that experienced in the boot process :-( But I still would like to be of assistance, it is never too late to learn. :-)

Have you tried to start in the fail safe mode?

Found this post: [http://ubuntuforums.org/showthread.php?t=613779]("http://ubuntuforums.org/showthread.php?t=613779").

It states that that either the /boot/grub/menu.lst or the /boot/initrd.img-XXXXX-generic (where XXXX is the kernel version). Can you post the contents of the menu.lst file. You can also try to make a copy of the kernel file and copy the kernel from the running live CD over the on on your harddrive.

Maybe you should also check the ubuntu cd for defects, it could be the kernel that is installed is defective on the CD and that that is the reason why you have the problem in the first place.

---

### Post by Boss Happy on 2008-03-04
Again I greatly appreciate your help. First, here's the contents of my menu.lst

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=d56342be-8d1c-43b1-8ea9-393a97950ac1 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d56342be-8d1c-43b1-8ea9-393a97950ac1 ro 
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d56342be-8d1c-43b1-8ea9-393a97950ac1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Here's the results from "fdisk -lu"

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d2329

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     9912104     4956021   82  Linux swap / Solaris
/dev/sda2   *     9912105    58733639    24410767+  83  Linux
/dev/sda3        58733640   781385534   361325947+   5  Extended
/dev/sda5        58733703   107555174    24410736   83  Linux
/dev/sda6       107555238   146625254    19535008+  83  Linux
/dev/sda7       146625318   185695334    19535008+  83  Linux
/dev/sda8       185695398   332176004    73240303+  83  Linux
/dev/sda9       332176068   625137344   146480638+  83  Linux
/dev/sda10      625137408   781385534    78124063+  83  Linux

```

Finally, here's my device.map
```

(hd0)   /dev/sda

```

I'll try the fail-safe kernel and let you know what happens.  Again, thanks.

---

### Post by BillDozer on 2008-03-04
You're welcome!

You've got a lot of partitions, did you make a special partition for /boot?

---

### Post by Boss Happy on 2008-03-04
Yeah, I like to keep things separate and if necessary be able to move them around, expand partitions, etc. :)  however, I didn't make a /boot partition.  :oops:

 I tried the fail-safe kernel and it failed with the same error. 

After reading your link and some others, I think you're on the right track.  I think it has to do with some module or another that needs to be compiled in the kernel.

Another question I have (just wondering out loud) why would the LiveCD load but the fail-safe not?

---

### Post by Boss Happy on 2008-03-04
Found this:
[http://ubuntuforums.org/archive/index.php/t-684613.html](http://ubuntuforums.org/archive/index.php/t-684613.html)

Of particular interest is:
> Sussed it nothing do with forcedeth....It was the way I partitioned my hard disks ie I had a separate /etc why you cannot I do not but when I revised by partitions it worked... this should be changed or at least the installer should warn the user...

I also have /etc in a separate partition.  When I get home tonight I'll try it out and let you know.

---

### Post by BillDozer on 2008-03-04
Maybe you should also check whether the UUID refers to the correct partition, otherwise you can try to change the root option to root=/dev/sd**X** where X is your root partition. 

You can either do it at bootup, change it with e and boot with b. Or you could add an extra group in the menu.lst with the corrected drive.

---

### Post by Boss Happy on 2008-03-05
[SOLVED] Apparently there is a bug with the LiveCD.  I had partitions for /etc, /usr, /var and /home.

When I did the re-install, I changed the partitions to /boot, /, and /home.  Everything is up and running.

Thanks for getting this going Bill.

---

### Post by BillDozer on 2008-03-05
Happy to hear that!

---

