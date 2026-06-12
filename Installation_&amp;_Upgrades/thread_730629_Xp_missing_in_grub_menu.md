---
title: "Xp missing in grub menu"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by srikar on 2008-03-21
Firstly i installed xp in d drive then i installed mint in da c drive , surprisingly grub doesnt contain windows xp entry.

#fdisk -lu

```
srikar@opensource:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca9fca9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63   312560639   156280288+   f  W95 Ext'd (LBA)
/dev/sda5        61432623   112631714    25599546    b  W95 FAT32
/dev/sda6       112631778   215030024    51199123+   7  HPFS/NTFS
/dev/sda7       215030088   312560639    48765276    7  HPFS/NTFS
/dev/sda8             189     4000184     1999998   82  Linux swap / Solaris
/dev/sda9         4000248    61432559    28716156   83  Linux

Partition table entries are not in disk order
srikar@opensource:~$ 
```

this is my menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default		0

gfxmenu=/etc/grub/message.mint

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Linux Mint, kernel 2.6.22-14-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin 
boot

```

### END DEBIAN AUTOMAGIC KERNELS

---

### Post by srikar on 2008-03-21
what to do???

---

### Post by Mustard on 2008-03-21
Which is the master drive and which is the slave?

-edit-

Actually looking at your fdisk command above it looks like its all on one drive with separate partitions.  Is that right?

---

### Post by srikar on 2008-03-21
ya i hav only one hard disk.

---

### Post by srikar on 2008-03-21
> /dev/sda5        61432623   112631714    25599546    b  W95 FAT32

in sda5 i am havin windows.

---

### Post by Mustard on 2008-03-21
> **srikar said:**
> in sda5 i am havin windows.

Hmmm..ok..I'm curious now why it would be using FAT32, since XP uses NTFS filesystem.

---

### Post by srikar on 2008-03-21
when i installed windows i chose fat32 rather than ntfs.Thats da reason.

---

### Post by Mustard on 2008-03-21
I would assume you add an entry like this to the bottom of your menu.lst

```

# Other operating systems
title		Microsoft Windows XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1

```

---

### Post by srikar on 2008-03-21
i modified it, see it below.But when i click on windows xp in grub menu , i get an error " Invalid device"


```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Linux Mint, kernel 2.6.22-14-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin 
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

# Other operating systems
title		Microsoft Windows XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```

---

### Post by Mustard on 2008-03-21
I'm wondering wether xp is actually on sda5 then. :)

Whats on sda2?

What are the two NTFS partitions?

-edit-

I figure we need to boot xp from sda2 just looking over your fdisk output.  It's the bootable partition.

just change```
 (hd0,4) 
```to ```
(hd0,1)
``` and see how that goes....

If you keep stepping up from ```
(hd0,0)
``` eventually you should hit something hehehe...although your fdisk output doesnt seem to show a partition 1, but just starts with a partition 2.  Since grub starts counting at zero, (hd0,1) should be sda2

---

### Post by srikar on 2008-03-21
I get this error when i click on xp in grub menu during boot time :-

> root(hd0,4)
filesystem is fat, partition type oxb
save default
make active

error:12 
Invalid device requested  

I got this error when i edited grub both the times: (

---

### Post by Mustard on 2008-03-21
Did you try ```
(hd0,1)
``` ?

I'd suggest ```
(hd0,0)
``` but I can't see how that would work, since the partition numberins seems to start at 2 (sda2).  Maybe I've got it wrong though.  At his stage we have nothing to lose by try ```
(hd0,0)
```

---

### Post by srikar on 2008-03-21
ya i tried , i get the same error

root(hd0,1)
filesystem is unknown, partition type oxf
save default
make active

error:12
Invalid device requested

---

### Post by srikar on 2008-03-21
I came across a command "fixmbr" in microsoft site.Does it list all the operating systems in the menu???

---

### Post by Mustard on 2008-03-21
> **srikar said:**
> I came across a command "fixmbr" in microsoft site.Does it list all the operating systems in the menu???

What that will do is overwrite grub and restore your mbr.  That should allow you to boot into XP again, but will kill grub and you wont be able to boot Linux Mint.  You could then attempt to reinstall grub again.  I would search the forums a bit for reinstalling grub.  If you do a search for the forum user named Herman and have a look over his posts and visit his website, you can get a lot of information on dual booting and grub installations.

-edit-

Here is a link to his website

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Herman on 2008-03-21
> Firstly i installed xp in d drive then i installed mint in da c drive , surprisingly grub doesnt contain windows xp entry.#fdisk -lu
     ```
srikar@opensource:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca9fca9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63   312560639   156280288+   f  W95 Ext'd (LBA)
/dev/sda5        61432623   112631714    25599546    b  W95 FAT32
/dev/sda6       112631778   215030024    51199123+   7  HPFS/NTFS
/dev/sda7       215030088   312560639    48765276    7  HPFS/NTFS
/dev/sda8             189     4000184     1999998   82  Linux swap / Solaris
/dev/sda9         4000248    61432559    28716156   83  Linux

Partition table entries are not in disk order
srikar@opensource:~$
```Unfotunately, if you had Windows in the C drive and you installed another Windows and you didn't use GRUB to dual boot Windows with, you probably cannot boot your Windows in your D drive anymore.
When you set up Windows-Windows dual boot you can use GRUB's hide command to hide Windows in C drive before you install another Windows.
Then when you install another Windows, it will not 'see' the existsing Windows, and it will think it is the C drive.
Then you unhide the Windows you want to boot and hide the one you don't want to boot.
You need GRUB in a dedicated GRUB partition or GRUB for Windows.
[How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")  [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html")
or GAG Boot Manager, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

When you try to dual boot two Windows without GRUB or GAG Boot Manager and you don't hide the Windows that's already there it will set up a default Windows dual boot, which means all the vital boot loader files from your D drive (new installation), will be removed and copied into your old C drive installation, which you have now deleted and installed Ubuntu in.
So you have no boot sector for Windows, no NTdetect.com, no NTLDR, and no boot.ini files to boot with, so it won't boot.
Even if you manage to run FIXBOOT and install a boot sector, (I don't know if you can in a logical partition), or install syslinux in the boot sector instead, I don't think you can boot Windows in a logical partition without another primary Windows to boot through.
You can try getting a copy of NTLDR, NTdetect.com and boot.ini and paste them into the root of drive D if you like. You will need to do that or it won't boot.
You can get those files from your Windows CD or another Windows XP computer or  the CD or floppy disk from this web site, [How to fix: NTLDR is missing, press any key to restart.]("http://tinyempire.com/notes/ntldrismissing.htm")

I have not yet heard of anyone being successful in getting Windows to boot again in a logical partition in these circumstances, but I would be interested in trying it myself, and I would be curious to hear of someone trying, but you might be wasting your time. Actually, I think I have already tried it and wasn't able to.

Here is a link that explains more,  [Understanding MultiBooting and Booting Windows from an Extended Partition.]("http://www.goodells.net/multiboot/index.htm")

Maybe if you delete something in a primary partition and rescue all the data from Windows first, shrink the partition and copy it and paste it to a primary partition with GParted, then run FIXMBR and copy the bootloader files into it you might get it to boot again.
Unfortunately, since Windows is a propeietary operating system, it contains antipiracy boobytraps, and it will know that it has been copied and pasted, so it will activate a timer and it will work only for a while, then quit on you without any warning.
Unless you re-install Windows in C drive again, and set C drive up with the - no, that wouldn't work either, because you still won't have a boot sector, Your old boot sector got removed to the old C drive.

Windows really should warn people about this kind of crazyness it does to its customers.

The best thing to do is copy all your files into Ubuntu and delete Windows XP and just use Ubuntu instead. Ubuntu is much better.

Regards, Herman :)

---

### Post by srikar on 2008-03-21
I didnt install two windows ,

It was a fresh installation.
i installed windows in da d drive( c is empty) and then i installed linux in da c drive. the grub didnt detect windows.Why did this happen?????

---

### Post by Herman on 2008-03-21
Is Windows in partition number 2 or in partition number 5?
Actually, termas like 'C' drive and 'D' drive are rather meaningless to me, but I took it to mean you deleted your original Windows install, because naturally all Windows installations seem to think they are in 'C' drive unless there is already another Windows in 'C', hence the confusion.

If Windows is in partition 2, then it should have booted already when you tried this,
root (hd0,1)
filesystem is unknown, partition type oxf
savedefault
makeactive

:confused:

---

