---
title: "Dual boot ubuntu and vista - a specific request"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Capslock118 on 2007-05-01
Hello folks
   Before you make any assumptions, I have read in countless places on the "how-to" dual boot. I know what to copy and past into the /boot/grub/menu.lst however i dont understand what it is doing or what it nessesarily means, though I get the concept. What I am asking for is a little explanation since this dual boot technique is not working for me, so I thought if I understood what everything meant, I could figure it out:

I have ubuntu on an IDE with the grub bootloader there. I have vista an a SATA drive with its MBA on that drive. I found how to dual boot with grub looking at this webpage:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_boot_into_Windows_installed_on_a_seperate_SATA_drive]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_boot_into_Windows_installed_on_a_seperate_SATA_drive")

this is what it said to do:
```

1 title           Windows XP on SATA drive
2 map (hd0) (hd1)
3 map (hd1) (hd0)
4 chainloader (hd1,0)+1
```

with windows on drive hd1.

well, MY windows is on sdb1 with its bootloader on that drive and ubuntu is on /dev/hda2.
I tried replacing hd1 as sdb1 however this did not yield the correct result; instead an error number which currently escapes me.

Im looking for clarification as to what the map is doing and what the chainloader is doing.

You could also just tell me what info to put where, but ideally I am looking for explanation.

Thanks

---

### Post by bulldog on 2007-05-01
Everything you want to know about GRUB is here,
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Capslock118 on 2007-05-01
Well thank you for that link. I understand alot more than when I first started with this.

Here is my current problem; long story short, I found that for 

```

title Windows Vista
rootnoverify (sdb1,0)
map (hd0,sdb1)
map (sdb1,hd0)
chainloader +1

```

sdb1 was completely wrong and instead by checking my device.map, i SHOULD have put hd3 instead of sdb1.

So i did this and recieved this error message:
```

"Error 11: Unrecognized device string"

```

I am kinda short on time today but I have been looking around the net for an answer and havnt found one that fits my situation yet.

If someone would like to analyze and respond with any ideas, here is my device.map and menu.lst

device.map:
```

(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda
(hd3)   /dev/sdb

```
  where /dev/hda would be ubuntu and /dev/sdb would be Vista


menu.lst where the VISTA boot code is at the very bottom:
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
# kopt=root=UUID=ae82c5e0-1e5e-44dd-81e7-3f334688851c ro

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
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ae82c5e0-1e5e-44dd-81e7-3f334688851c ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ae82c5e0-1e5e-44dd-81e7-3f334688851c ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=ae82c5e0-1e5e-44dd-81e7-3f334688851c ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=ae82c5e0-1e5e-44dd-81e7-3f334688851c ro single
initrd          /boot/initrd.img-2.6.17-11-generic

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=ae82c5e0-1e5e-44dd-81e7-3f334688851c ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=ae82c5e0-1e5e-44dd-81e7-3f334688851c ro single
initrd          /boot/initrd.img-2.6.17-10-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows Vista
rootnoverify (hd3,0)
map (hd0,hd3)
map (hd3,hd0)
chainloader +1

```

Thanks again

---

### Post by bulldog on 2007-05-01
Hi there,

Ubuntu boots as it should?
Only a problem with Vista?
Can you perform in a terminal```
sudo fdisk -l
``` it's a lowercase L not a one.

Grub counts your hdd's,IDE and Sata,as hd0,hd1 and so on.
Partitions are pointed to as follows hd0,0.hd0,1 
The first hdd with the first partition should be hd0,0 the second partition hd0,1 so should the second hdd with the first partition be hd1,0 the second partition on the same hdd hd1,1.
So Grub start counting with 0 for hdd and partition as well.

Another question,can you boot Vista if you change the master boot device in your BIOS to the Sata hdd?

---

### Post by Capslock118 on 2007-05-01
Thank you for your response.

sudo fdisk -l gives me:

```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               3        4159     2095104    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2   *        4160       74492    35447422+  83  Linux
Partition 2 does not end on cylinder boundary.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9730    78148608    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9612    77208358+  83  Linux
/dev/hdb2            9613       19697    81007762+  83  Linux
/dev/hdb3           19698       30140    83883397+  83  Linux
/dev/hdb4           30141       30401     2096482+   5  Extended
/dev/hdb5           30141       30401     2096451   82  Linux swap / Solaris

Disk /dev/sdc: 512 MB, 512483328 bytes
255 heads, 63 sectors/track, 62 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          62      497983+   6  FAT16

```

everything seems to me to be in order.

mostly everything you said I have gathered from your previous link; which has been very helpful.

As to your last question that is the most interesting. If I were to load Vista by going into the BIOS and setting the first boot disk to the vista drive; yes, it works...it also works if I hit f11 (my select boot option key) and select that particular drive.

Ubuntu boots as it should, and grub shows ooo, about 7 kernels maybe? a memtest, and then finally windows vista which spits out the error 11 message if I select it.

hd0,0....I am happy you re-iterated that the second 0 meant the parition number, as I did not know that.....

perhaps that may be my issue? the ubuntu partition is considered hda2 because of the vista swap on the drive (hda1) however, unless grub fixed it automaticlly or something changed on its own..or it was just plain unnessesary it did not affact my ubuntu booting. 

I mention that because I just recently installed vista, while I have had ubuntu currently on my machine for a number of months now without any other os.

Curiously, for some reason Vista leaves 1Mb in front of the disk unformatted after it goes ahead and formats the drive....well I SHOULD say that is what gParted detects...vista however does not recognize that 1mb

---

### Post by bulldog on 2007-05-01
Can you give me the output of```
cat /boot/grub/device.map
```

EDIT;
as far as I see it,Vista is on the sdb which should be hd2,counting starts with zero,remember?
You map your Vista (hd0) (hd3) which should be (hd2) 
rootnoverify should be (hd2,0) too.

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows Vista
rootnoverify (hd2,0)
map (hd0)  (hd2)
map (hd2)  (hd0)
makeactive
chainloader +1
```

Your Vista entry should look like this one.

---

### Post by Capslock118 on 2007-05-01
my cat device.map is

```

(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda
(hd3)   /dev/sdb

```

---

### Post by bulldog on 2007-05-01
Take a look at my edit in previous post.
Try to copy and paste this in your menu.lst and
After you did copy it in a terminal```
sudo update-grub
```
...........well,try to boot Vista :) 

Let me know if it works.

---

### Post by Capslock118 on 2007-05-01
bulldog,
   Thank you very much for your help in this matter. I do believe that it was a mis-read on your part, words can mix and meld on the computer screen. If you notice on my device.map vista is actually on hd3 (/dev/sdb). In any case, using hd3 with your copy and past worked.

Now I tried that before you suggested what to copy and paste nearly exactly however it did not work. I determined my fault to be not using the:
```

sudo update-grub

```

I think if that was clarified more in other posts / wikis then this would have been solved sooner. Either way, it was that small command that you provided that fixed the issue entirely.

I think thats unofficial edgy guide should be updated to show you need to run that small command. If it allows me, I will take care of that now so the next sorry soul is not as confused as I was.

Thanks again!

---

### Post by bulldog on 2007-05-01
Yes I noticed in your device.map it was listed as hd3,but in your fdisk,which I used to make the entry,it is hd2 :) 

About sudo upgrade-grub,you have to enter this command every time you change something in your menu.lst,otherwise grub won't notice.

Well,I'm glad it worked out.

have fun with your ubuntu :guitar:

EDIT;
About your looong list with kernels,you can remove them with synaptic.
Search for linux-image and remove the ones you don't want to use any more.
Little advice,though,leave at least the two latest kernels on your hdd,if something goes wrong you can boot the older one.

---

