---
title: "grub rinstallation issues"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by fuligin on 2007-02-07
HI everyone, 
Im trying to reinstall ubuntu, as I have been tinkering with it for the past 2 weeks and im sure that ive done some damage so i decided to reinstall it. 
As im dual booting Edgy 6.10 and xp, I deleted and formated the extended partion that was allocated for 6.10. 
Now this time i set aside 8gb for my root. 1gb for a fat 32 which i would use as a transfer area between both os ( this is th way you do it right?) and about 900mb for swap.
upon installation which i did twice i get no real options or grub, and it just boots me into ubuntu and i dont have the choice to boot to xp.  also i get a error with HAL.
what is the proper way to make this installation work. as ive reinstalled ubuntu twice. 
thanks for all ur help in advance.

---

### Post by mikewhatever on 2007-02-07
Can you please post you grub menu 
>  sudo gedit /boot/grub/menu.lst

---

### Post by fuligin on 2007-02-08
Thanks for the quick reply, I have delted that drive and will reinstall. However I am wondering what is the correct process in doing so. also since this has happend to me a few times, wouldnt it be that maybe i am leaving something behind after i format the drives. 
anyways i will reinstall the drive for the 4th time, what are the right measures for making sure grub is installed proplerly, additionally am i doing the right method for the shared folder?

tahnk u for ur help

---

### Post by mikewhatever on 2007-02-08
The Live CD installation guides are out there for you
[Installation Guide]("http://psychocats.net/ubuntu/installing")
[Another Installation Guide]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/index.html")

---

### Post by fuligin on 2007-02-08
Thanks for the 2 guides. 
The second one seems especially helpful since my laptop is a Thinkpad.
I will follow them closely and tell you what happens. 
Tuda

---

### Post by fuligin on 2007-02-08
I reinstalled and again my grub doesnt give me any options to enter xp, additionally the HAL error still occurs, I wil do a fixmbr so i can acess my xp section. however wont delete the ubuntu partion now incase i can save someting from it.  I understand i might be able to fix this from my live cd. 

below is the requested grub menu:


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
# kopt=root=UUID=9b85a15b-063a-4ebc-8f7f-4b2eec75d76f ro
# kopt_2_6=root=/dev/hda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by mikewhatever on 2007-02-08
Hi again,
First, I don't think you need to reinstall any more. The problem is with grub menu, since for some reason the Windows part is not there. I have Ubuntu and Windows installed on one HD, and this is what the end of my grub menu looks like:
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

You do not seem to have this part. Are there more then one HDs?

---

### Post by fuligin on 2007-02-08
Hello, Unfortunatly this is the only part that i have on my grub list. 
I only have one HD, which is partitioned into several sections. I havent reinstalled again, only did a fixmbr inroder to use my xp portion.
I dont understand why grub wont see my xp installation. and no clue wut the HAL error is 
:(

---

### Post by mikewhatever on 2007-02-08
You can try to manually edit the menu. Simply add the missing part to the end.

---

### Post by fuligin on 2007-02-08
I will attempt to do so, and see what happens, however in the meantime i need to reinstall my grub, i think i have seen some way to do that with the live cd somewhere, so i will try it asap. 
I really dont understand why this is happening since the first time i installed it it went very smoothly, didnt even have the HAL error :(
Ill try it and get back to you. Hopefully with a better outcome
Tuda.

---

### Post by confused57 on 2007-02-08
> **fuligin said:**
> I will attempt to do so, and see what happens, however in the meantime i need to reinstall my grub, i think i have seen some way to do that with the live cd somewhere, so i will try it asap. 
I really dont understand why this is happening since the first time i installed it it went very smoothly, didnt even have the HAL error :(
Ill try it and get back to you. Hopefully with a better outcome
Tuda.

If you haven't found it already:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by mikewhatever on 2007-02-09
Good morning Fuligin, 
how did GRUB reinstallation go? To make sure your Windows is indeed in (hd0,0), can you please post the output of 
> sudo fdisk -lu

---

### Post by fuligin on 2007-02-09
Good Afternoon Mike, 
Holiday today, tomorrow or sunday? Looks like another stormy weekend coming, if so you will get it soon.
I was able to get the grub back thanks to Confused 57's post.

However the not being able to see the partions still happens. HAL error didnt appear last time, I dont know why since i havent done antything in regards to that. But i did paste your last part with the new section but it doesnt show up, actually nothing shows up not even the various boot options.

I keep thinking maybe I have done something wrong in the first installation or there is some remainder from gub somewhere for it to go haywire like this. below is the list that you asked. Thanks for all your on going help !

Disk /dev/hda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    12292559     6146248+   7  HPFS/NTFS
/dev/hda2        12292560    78125039    32916240    f  W95 Ext'd (LBA)
/dev/hda5        12292624    15437519     1572448    7  HPFS/NTFS
/dev/hda6        38238544    78125039    19943248    7  HPFS/NTFS
/dev/hda7        15437583    25673759     5118088+  83  Linux
/dev/hda8        25673823    27730079     1028128+  82  Linux swap / Solaris
/dev/hda9        27730143    31827599     2048728+   b  W95 FAT32

---

### Post by mikewhatever on 2007-02-09
Hi there,
You quite right, the clouds are gathering :guitar: . Stop blaming yourself if something does not work. Actually, the last unsuccessful try can be my fault. I have SATA HD, which is not your case, so the Windows part of your menu should look something like this:
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1 

note the difference sda1 vs hda1

---

### Post by confused57 on 2007-02-09
Since you restored grub, I suppose you're automatically booting into Ubuntu...your grub menu should show up if you place a # in front of the line hiddenmenu:
```
#hiddenmenu
```

For Ubuntu to access your FAT32 partition, it has to be mounted:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

or this guide:

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

mikewhatever's Windows entry he suggested should work.

---

### Post by fuligin on 2007-02-09
Yipeeee !!! 
Got the grub to finally work, It was a combo of both things that i used. I used part of that post on resetting grub, also Confused suggestion about the hidden played a big role,as it was hidden, then  I added the windows section as you suggested. It worked for one reboot till Arconis boot manager messed things up for me again :( . Well back from square one same combination only this time i had disabled Arconis Boot manager. 
Same codes and now its working perfectly, I think the cause of this is my bad installation or uninstallation because there were some things in the grub that were remnant from my old grub, like my default 3 second setting. so possibly grub got all messed up when over writing ?
Well after seting up wireless (which really is on weak on here for some reason :( ) now im updating, the HAL error comes and goes but apart from that, the system is open game to tinkering and messing around with :) Next up mounting the transit partiton, and my ATI :)
Thanks fellas, hopefully I can master this system like XP, all the sudos are a headache since I feel like a blind man copying and pasting. 
Mike, next time im in your neighborhood, I owe u a couple of drinks. I know a few nice joints :), so i hope things calm down soon, off course the same would go for u frequent my neighborhood :).
THanks guys, 
Im sure u will hear from me again, Im a total newbie ubuntu but have a big appetite to tinker :grin:

Hmmmmm???? Now it keeps deleting my xp entry from the grub.

---

