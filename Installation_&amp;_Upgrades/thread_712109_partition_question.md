---
title: "partition question"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by rico4295 on 2008-03-01
is there a way to restore the partition back to the main ntfs partition?

---

### Post by Pumalite on 2008-03-01
From what? What's the whole story?

---

### Post by rico4295 on 2008-03-01
I had ubuntu 7.10 working fine but somehow it got corupted. It booted up to black/white fullscreen terminal. Someone told me to try startx but it said the libX* 's could not be found. I reinstalled but I get error 22 right after grub says starting. fdsik shows (I'm not on that pc)
sda1  *    ntfs
sda3        extended
sda5        swap
sda6        linux

I've tried editing the menu.lst but with no luck yet getting the installed ver to load

does the extended part get dropped during a normal boot making
 sda1 *   ntfs
sda5      swap
sda6      linux


was hoping to just revert back untill i can get a seperate hd to install ubuntu on

---

### Post by Pumalite on 2008-03-01
If you were dual booting, you can restore the Windows MBR with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Or your Windows installation CD>Recovery>FIXMBR>FIXBOOT.
Come back for the other question if you can get that fixed.

---

### Post by rico4295 on 2008-03-01
not sure what to do on the xp disk. it want to install xp- create or delete partitions.  I tried the recorery and it wanted an automated recovery disk put in drive a:

---

### Post by Pumalite on 2008-03-01
From the installation XP you have to go to Recovery first>FIXMBR>FIXBOOT.
We'll deal with the partitions later. You can use Super Grub too.
Unless you want to erase everything in your drive and install Ubuntu. Let me know.

---

### Post by rico4295 on 2008-03-01
Sorry but i'm still lost. I'm not seeing anything about fixmbr or fixboot in the xp cd after it loads up. The f2 recovery option wants a floppy disk that i don't have.

---

### Post by Pumalite on 2008-03-01
Use Super Grub.

---

### Post by rico4295 on 2008-03-01
thank you for your time and if you don't mind let's try this route. i tried to d/l the super grub disk but it said connection denied.
here is what fdisk is showing me ( i'm on the pc on the live cd load)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27c927c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   167766794    83883366    7  HPFS/NTFS
/dev/sda3       167766795   234436544    33334875    5  Extended
/dev/sda5       231593103   234436544     1421721   82  Linux swap / Solaris
/dev/sda6       167766921   231593039    31913059+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 27.3 GB, 27373731840 bytes
255 heads, 63 sectors/track, 3328 cylinders, total 53464320 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb08ae147

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *       16065    53464319    26724127+   f  W95 Ext'd (LBA)
/dev/hdb5           16128    53464319    26724096    b  W95 FAT32


and the menu.lst  

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
# kopt=root=UUID=521cc732-1c47-4b38-add9-95788503de3f ro

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
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=521cc732-1c47-4b38-add9-95788503de3f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=521cc732-1c47-4b38-add9-95788503de3f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1

i comented out the map commands again, it helped me last time i had problems
i've tried changing the root for linux to (hd0,?) i've tried 2,3,5,6

---

### Post by Pumalite on 2008-03-01
What do you want to do?

---

### Post by rico4295 on 2008-03-01
well i'm not sure. linux is installed already so i'd like to try and fix that

---

### Post by Pumalite on 2008-03-01
This is you original question:
'is there a way to restore the partition back to the main ntfs partition?'

---

### Post by Pumalite on 2008-03-01
Backup menu.lst
gksudo gedit /boot/grub/menu.lst
Change:
root (hd0,2)
to:
root (hd0,5)
Save, exit and reboot.

---

### Post by rico4295 on 2008-03-01
I get the same error
grub loading stage1.5.

grub loading  plaese wait
error 22

---

### Post by Pumalite on 2008-03-01
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by dstew on 2008-03-01
> I get error 22 right after grub says startingYou are getting a grub stage1.5 error. You will have to re-install grub as Pumalite says. In addition, you have a lot of work to do on your menu.lst, because the entries do not match your fdisk output. But you need to re-install grub first. This error 22 problem cannot be fixed by editing the menu.lst file.

---

### Post by vligu on 2008-03-01
Hello,
well im a new bie to Linux and i just installed Ubuntu 7.10 at a 2GB RAM, AMD 3800+ 64bits machine. I have now a dual boot machine one of those OS is win xp pro. Since i installed ubuntu i cant see my win xp pro partition. It seems that it doesn't recognize it. I use a reifers file system to ubuntu. So i can't access win xp pro from ubuntu neither to see that partition. I have been a linux user before and i had ubuntu 6.10 and everything was perfect. I was able to access win xp pro before, offcourse not to write on it but read only. Can anyone pls help me?
Thanks for any help! (Well i tried to open a new post for make someone to help me but it seems nobody answer, so i write here hoping someone to help)

---

### Post by dstew on 2008-03-01
vligu: Your problem is very different than the problem being addressed in this thread. Please copy your post and start a new thread. I would recommend posting to the Absolute Beginner Talk forum. I am sure someone will help you there.

---

### Post by vligu on 2008-03-01
well thanks but i posted on a new thread the same msg and i get no answer, i have been about 1hour waiting for and nothing. So if you know anything about you can help, the thread i posted is "Ubuntu 7.10 doesn't recognize win xp pro partition". thanks bye the way!

---

### Post by Pumalite on 2008-03-01
See my answer to your PM.

---

