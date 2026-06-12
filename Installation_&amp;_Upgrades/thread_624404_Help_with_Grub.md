---
title: "Help with Grub"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by lucid_dream on 2007-11-26
Hello everyone, i am still a bit of a newbe with Linux. I have been playing around a little since  6.10. Well my issue today is that i just installed 7.10 as dual boot with XP. Install went good as always, rebooted and got right in. However on the 2nd reboot grub would not load. THe POST would start to load, flicker the grub for about half a second and then POST would restart. The PC gets stuck in a loop where the bios starts to come up than restart. I tried to reinstall 3 times and get the same thing. The initial reboot works but all subsequent reboots fail. Any ideas?

---

### Post by torgrot on 2007-11-26
When you see grub hit any key.  Go down to the grub entry and type e that should let you edit the command, down arrow to the line that starts with kernel and go to the end of the line.  On mine I had to add pci=biosirq to prevent the endless loop where it starts to boot and then reboots.  Other options are acpi=off or acpi=force or acpi=ht  Add them one at a time, then press, I believe b to boot.

torgrot

---

### Post by lucid_dream on 2007-11-26
Well the problem with your solution is that grub flashes past so fact i cant hit any keys

---

### Post by torgrot on 2007-11-26
After the post starts just hold a key down perhaps "e"

torgrot

---

### Post by lucid_dream on 2007-11-27
I tried your idea to no avail. I tried holding a few different keys and tried tapping a few keys,  i even put an "ANY" key on the keyboard with no luck. I pulled out my Ultimate boot disk and loaded up Super Grub Disk. While in SGD i was able to boot XP directly, this worked well. I tried to boot Ubuntu directly with the original result. It immediately  restarted the entire system. I tried to rewrite GRUB via the SGD but system kept freezing. Also tried to rewrite the XP MBR and again the system would freeze.  

I have XP on the master drive , Ubuntu on the slave. I tried switching to make XP the slave ... no luck there. Currently i have the Linux drive unplugged to see if i can at least get XP to boot without the help of the SGD. 

I am open to any suggestions short of trying to do a complete reinstall. As i mentioned I don't believe there was any system installation issues. I would much prefer to fix grub and try to work from that angle. Do you think perhaps i should try to boot with LiLo instead?

---

### Post by torgrot on 2007-11-27
If you have the Windows CD you can boot off that and select recovery console.  At the c:\ prompt type fixmbr that will restore the windows boot record to the c: drive.  Try looking at the following page [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)  it has instructions for repairing grub from the live CD.  I would fix the Windows MBR first, that way you have at least a bootable system.  I don't think you can boot Windows of a slave drive without some grub trickery.  I have two ide hard drives hda0 has Ubuntu and hda1 has windows XP  I will attach my menu.lst and fdisk -l  for you to see as an example.
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
default		saved

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
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


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
# kopt=root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro
# kopt_2_6=root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro acpi=force pci=biosirq

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=true

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro acpi=force pci=biosirq quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
savedefault

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro acpi=force pci=biosirq single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro acpi=force pci=biosirq quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro acpi=force pci=biosirq single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro acpi=force pci=biosirq quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu 7.10, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro acpi=force pci=biosirq single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu 7.10, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro acpi=force pci=biosirq quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro acpi=force pci=biosirq single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

```

here is the output of sudo fdisk -l

george@Ralph:~$ sudo fdisk -l
[sudo] password for george:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2568    20627428+  83  Linux
/dev/sda2            2569       19187   133492117+  83  Linux
/dev/sda3           19188       19457     2168775   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07066020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16709   134215011    7  HPFS/NTFS
/dev/sdb2           16710       19457    22073310    f  W95 Ext'd (LBA)
/dev/sdb5           16710       19457    22073278+   7  HPFS/NTFS

I hope this is enough to at least get you started.

torgrot

---

### Post by lucid_dream on 2007-11-27
Ill let you know how it goes. Thanks

---

### Post by torgrot on 2007-11-27
I had a multitude of problems when I first installed.  In my case, I had two hard drives.  I removed my Windows drive completely from the system.  I had the new drive as primary master and installed to a clean disk.  I let Ubuntu have the whole disk.  I created three partitions a /, swap and /home.  I ran into the reboot problem immediately.  With Herman's help I was finally able to get the parameters I needed see above added to the kernel default options so I wouldn't have to deal with it again.  When I had Ubuntu all set up nice and reliable, looking at the Herman's web page I was able to figure out how to add Windows to my grub after I reconnected windows as a secondary/slave drive.  I think the beauty of this method is that, should I ever decide that Ubuntu isn't for me, all I have to do is swap the drives and I can boot windows just like Ubuntu wasn't there, no grub no nothing Ubuntu.  If I want to use the drive all I have to do is partition/format with windows all done.  I wish you luck.

torgrot

---

### Post by lucid_dream on 2007-11-27
Well here is the deal, i loaded up XP recovery and did a fixmbr. Worked like a charm and only took about 0.023 seconds (once you wait 15 minutes to load the recovery councel that is) . So not i can boot XP normally again. I followed herman's instructions to recreate grub via my live CD. That worked can not boot ubuntu through grub everything i cherry...... or is it. i booted ubuntu a few times with no problem them i tried to boot XP again through grub.. it booted just fine . restarted and tried to boot again and not back to the original issue again. So i ran the fixmbr once more te get an operable system again and this is where i stand.

---

### Post by torgrot on 2007-11-27
I don't have any more suggestions.  The problem you are experiencing is out of my league.  Maybe someone else has some ideas.

torgrot

---

### Post by meierfra on 2007-11-27
Did you try using a different bootloader?

---

### Post by lucid_dream on 2007-11-28
No I have not tried any other bootloader. I do not even know how to begin to change to an alternative  loader

---

### Post by lucid_dream on 2007-11-28
Here is my current drive configuration:

(hda0) &#8211; XP, MBR for XP is located in (hda0, 0)
(hdb1) &#8211; Ubuntu, GRUB is located in (hdb1, 0)

I don&#8217;t know if this could be part of the problem but I just realized that GRUB is located on a different partition of a different drive. This could be why when I boot into XP it clobbers GRUB and GRUB no longer works properly. So I suppose my next mission is to find out how to rewrite GRUB onto the MBR on (hda0,0).  Any suggestions how I might approach this?

---

