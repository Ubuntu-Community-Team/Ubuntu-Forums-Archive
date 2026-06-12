---
title: "NTLDR missing error when booting Windows from Grub"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by rvs070 on 2008-09-20
Hello,

Can anyone help me fix my dual boot machine? I set up the windows entry in the menu as follows (thanks ubuntu forums :) ):

title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

With the drive on which XP is installed being the slave on IDE channel 0. Everything worked great for little while. Then something happened, and now instead of loading windows, I get an "NTLDR missing" message. I'm pretty sure this is not an issue with the windows drive or the windows installation, since windows loads fine when I make the windows drive master and the ubuntu drive slave (by switching jumpers). Also, the "NTLDR missing" message appears pretty much instantly after I select the "Windows XP" menu entry. I don't hear any drives being spun, making me think that the windows drive is not even being accessed.

Any suggestions?

---

### Post by caljohnsmith on 2008-09-20
Did you possibly make any BIOS changes around the time you started having problems booting Windows?

Also, try this menu entry in you menu.lst and let me know what happens:
```
title Windows XP
rootnoverify (hd1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
Can you think of any other events that occurred around the time that Grub stopped booting Windows?

---

### Post by rvs070 on 2008-09-21
I tried 'rootnoverify', but got the same result.

Here's exactly what happened. Just prior to setting up the dual boot machine I cloned my windows drive and put the clone in the dual boot. That drive looks to have been defective, as I first got BSOD a couple of times and then windows stopped loading with that "NTLDR missing" error. Ubuntu was and is loading fine this entire time.

When the windows drive crapped out, I swapped it out for the original drive from which it was cloned. Again, the cloning was done just prior to building the dual boot, so the two installations are identical. This process, of course, involved some adjustment of the BIOS, but everything is back to the same arrangement that worked previously (Ubuntu drive is Master on IDE 0 and Windows drive is Slave on IDE 0).

Now, even with the new windows drive, I'm getting the same "NTLDR missing" error, despite the fact that Windows loads fine when the windows drive is Master. This is why I'm now convinced that the problem is on the Ubuntu drive, not the Windows drive.

Does that make sense?

---

### Post by caljohnsmith on 2008-09-21
OK, that makes sense I think based on what you've said so far. When you start up, does your BIOS give you the option to press F12 or F10 or some other key to temporarily change which drive you boot from? If you can, try doing that to boot your Windows slave drive and see if it works; I suspect it won't, but let me know what happens.

---

### Post by rvs070 on 2008-09-21
I didn't see a way to temporarily change the boot drive, so I just went into the bios and changed the priority of hd booting so that the primary slave is at the top. To my surprise, Windows booted fine. Now I'm even more convinced that the problem is somewhere on the ubuntu disk (probably in Grub).

---

### Post by caljohnsmith on 2008-09-21
OK, give the following a try in your menu.lst:
```
title Windows XP (hd2)
rootnoverify (hd2)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```
And you are opening the menu.lst file as root and saving it that way? Just want to make sure, or let me know if you need help with that. 

Also, please post:
```
sudo fdisk -lu
```

---

### Post by rvs070 on 2008-09-21
Changing hd1 to hd2 didn't help - NTLDR is still missing. Here is the output of fdisk -lu. Now that I think about it, I remember something about aliasing hd's as sd's during ubuntu intallation. Could it be that the file where the aliasing information was stored has been corrupted or destroyed?

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1eb91eb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   136713149    68356543+  83  Linux
/dev/sda2       136713150   156360644     9823747+   5  Extended
/dev/sda5       136713213   148424534     5855661   82  Linux swap / Solaris
/dev/sda6       148424598   156360644     3968023+   b  W95 FAT32

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x765ea672

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    39070079    19535008+   7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9665ab6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sdc2        81915435   398283479   158184022+   f  W95 Ext'd (LBA)
/dev/sdc5        81915498   398283479   158183991    7  HPFS/NTFS

---

### Post by meierfra. on 2008-09-21
Could you also post the output of

```
cat /boot/grub/menu.lst
```

---

### Post by rvs070 on 2008-09-22
Here is the menu.lst file:

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=244a6273-8f1e-44d6-9c0d-b51ba2eaab1e ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=244a6273-8f1e-44d6-9c0d-b51ba2eaab1e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=244a6273-8f1e-44d6-9c0d-b51ba2eaab1e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd1,0)
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

And here is the boot.ini:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
```

---

### Post by rvs070 on 2008-09-22
And yes, I'm editing menu.lst as root.

---

### Post by meierfra. on 2008-09-22
Every looks fine, so I don't really see what the problem could be. 

Did you notice that caljohnsmith had  recommended 
"rootnoverify (hd1)" and not "rootnoverify (hd1,0)" ?

and did you try both:  "rootnoverify (hd2)" and "rootnoverify (hd2,0)"  ?

You also might try reinstalling grub:

```
sudo grub
```
and at the grub prompt:
```

root (hd0,0)
setup (hd0)
```

If none of this works, I suggest to add Ubuntu to the Windows Boot loader. (I'm on my way to bed, so you will have to wait until tomorrow for further instruction from either me or caljohnsmith)

---

### Post by rvs070 on 2008-09-22
Reinstalling grub fixed it. Thanks!

---

### Post by prongs_386 on 2008-11-20
I thought I'd post my experience and solution to this problem.

I had a drive on ide and 2 sata drives as well.
Now windows was on my 1st sata drive and linux on my second.

By using fdisk -l it would show that my IDE drive was sda, and my 1st and second sata were sdb and sdc.

Now I noticed that within grub, my IDE drive was actually hd2, not hd0 as I would have expected based on the fdisk output.

So I think for anyone who has a combination of IDE and sata drives... this is a possible problem.

I was able to boot by using
```

title		Windows XP
root		(hd2,0)
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader +1

```

So now I was actually pointing to hd2 which was sda under fdisk.
This then booted correctly... It did not work unless I used the map directive.

Hope I've helped.

---

### Post by skozzy on 2008-11-20
I am not sure if this relates to your problem you had, but on my computer regardless of the drive order I set in bios Grub will also use its own drive list order. If I reset bios (removing the battery or setting the blank bios jumper), the default order of drives then equals that of Grub.

I had the same problem as you a long time back with NTLDR missing, Windows seems to follow the Bios Drive Order the user sets, but Grub seems to use a real Drive order list from first to last drive regardless of any settings in bios.

As I said, this is on my computer. Might not be what your problem was.

---

