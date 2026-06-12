---
title: "Triple booting with grub"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by dave_h on 2006-12-11
Hi very new to Linux and for various reasons, including I wanted to explore both KDE and Gnome, I installed XP, Ubutu and Kubuntu in that order. 

At start-up Grub shows me 2 instances of Ubuntu (which are really Ubuntu and Kubuntu) and allows me to manually select which OS to boot but if I don't select any it will default to Kubuntu. So in Ubuntu (which I am more familiar with) I tried to change the default in /boot/grub/menu.lst However I can see XP but I can only see one occurence of what I think is Ubuntu and no Kubuntu. Even if I change the default to "saved" it still boots up into Kubuntu.
 
Very new to all this and not sure what is going on and how to make Ubuntu the default.
Help please!

boot/grub/menu.lst is as follows:

------------------------------
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
# kopt=root=UUID=95cf39a6-b277-4906-826e-cfbd7e8faef0 ro
# kopt_2_6=root=/dev/hda2 ro

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
.

---

### Post by bulldog on 2006-12-11
Okay,an update,why don't you install Ubuntu,than install Kubuntu Desktop in Ubuntu and choose at login,which one you want to use??

It's perfectly possible to have one Ubuntu distro with different desktops.

Can you put the outcome of ```
sudo fdisk -l (l as in like)
```to the forum?

---

### Post by etaham on 2006-12-11
First off, you dont need to install 2 copies of linux to have both kde and gnome.  You can install KDE in ubunutu or gnome in kubuntu through synaptec. Once installed, you can choose which one you want from the login screen under SESSIONS.  I recommend that you delete one of the partitions are just install the other windows manager to the remaining one.

If you really want to keep your settings, try setting default to 0

---

### Post by bulldog on 2006-12-11
> **etaham said:**
> First off, you dont need to install 2 copies of linux to have both kde and gnome.  You can install KDE in ubunutu or gnome in kubuntu through synaptec. Once installed, you can choose which one you want from the login screen under SESSIONS.  I recommend that you delete one of the partitions are just install the other windows manager to the remaining one.

If you really want to keep your settings, try setting default to 0

If you take a look at his GRUB you can see he has just one ubuntu installed.
Probably he installed KDE in ubuntu and set this as default.
He should just at login choose for Gnome and make this the default and he's done.
No point to change the GRUB,there's nothing to change :D to make it work like TS wants.

---

### Post by dave_h on 2006-12-11
Hi Bulldog & Etaham,
I was aware you can use different desktops with one installation. But I am using Ubuntu and just investigating Kubuntu (actually KDE) so want them installed in separate partitions in case I screw up the whole thing and have to re-install again. The best way to learn is often to test to destruction. Besides that's the way it's installed now and I really dont want to start all over again. Or are you sayng its not possible to triple boot this way????

I have put the result of fdisk below.

Not sure why you say I have only one version of Ubuntu installed. The partiton for Ubuntu (hda/2) sizes at about 2.2 GB wheras Kubuntu (hda/4) is about 3GB. I have downloaded more programs into the Ubuntu install than the bare bones Kubuntu installation.

Also the splash screen, or whatever its called, after I reboot the PC and the BIOs has done its thing shows 2 versions of "Ubuntu" (in different partitions.) All of which seems to me (but admittedly a novice) as if I really have 2 installations.

To Etaham: Yes I have tried default 0 but still the same old thing. Always defaults to Kubuntu.

Help!
Dave



------------------------------------------------------
 Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3581    28764351    7  HPFS/NTFS
/dev/hda2            3582        6712    25149757+  83  Linux
/dev/hda3            9648        9964     2546302+   5  Extended
/dev/hda4            6713        9647    23575387+  83  Linux
/dev/hda5            9777        9964     1510078+  82  Linux swap / Solaris
/dev/hda6            9648        9776     1036129+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by dave_h on 2006-12-11
I meant to say the sizes 2.2GB for Ubuntu and 3GB for Kubuntu refer to the amount of hard disk space used. Should have been clearer. Sorry

---

### Post by dave_h on 2006-12-11
And in case this will help anyone here is the /boot/grub/menu.lst when running Kubuntu. The one above was when I was running Ubuntu.

Thanks.

------------------
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
# kopt=root=UUID=88cdd1de-1ac8-4c70-ab26-87b79504a5ee ro
# kopt_2_6=root=/dev/hda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# kopt=root=UUID=88cdd1de-1ac8-4c70-ab26-87b79504a5ee ro
# kopt_2_6=root=/dev/hda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, memtest86+ (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot## altoption boot targets option
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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, memtest86+ (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by geek_Man on 2006-12-11
Can you post your menu.lst from your Kubuntu partition?

EDIT: Sorry, posted too slow.

---

### Post by geek_Man on 2006-12-11
Maybe if you put your Ubuntu entries in your automagic area (I dunno what it's called), before where it says ## ## End Default Options ##. Also, if you put "[code]" tags around your menu.lst file it makes it a lot easier to read.

---

### Post by dave_h on 2006-12-11
Hi, Okay I want to try your suggestion but afraid to say I am ignorant how to change the menu.lst in KONSOLE. I would have done "gksudo gedit ..." in terminal but it's not the same is it? Sorry to be a newbie. 
Also not sure what you mean by "putting code tags" around the list. I did wonder whether to post such a long list but was concerned that if I edited it I might be chopping something relevant. Please advise as always willing to learn.
Thanks for your help.
Dave

---

### Post by bulldog on 2006-12-11
LOL,I saw your Ubuntu menu.lst and just one kernel so I thought you had just one kernel so you should have just one ubuntu :D 

The second menu.lst makes it much more clear what to do.
You have to change the default zero (0) to the entry which you want to be booted by default,the counting starts with a zero.
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0 <-----make this the number you want to boot by default I think it should be a 5
```

try this and  if it doesn't work make it 4.
You should be aware that the Ubuntu menu.lst is now integrated into kubuntu.

About the tags,you have to put your menu.lst between them.
You open with [code] and you close with the same tag but put a / before code like [/code ]<--this one has a space otherwise you can't see what I mean,you should not use the space of course.

---

### Post by dave_h on 2006-12-11
Okay thanks for that. I "think" I now understand how to tag code in these forums (time will tell) but I still have 2 queries.

1. to those who said just have a Ubuntu installation and at log- in decide whether to run KDE or Gnome, How is that done. I just installed KDE using Synaptic in Ubuntu but after re-booting I don't get the choice and Gnomeme always comes up. What to do?

2.Sorry for the complete ignorance of KDE (that's why I am trying to get it running as an optionto Gnome) but I would love to change the /boot/grub/menu.lst file but dont know how to do it in Konquerer (please see my previous post. Tried google and other avenues. Can someone help please. I am sure it's so easy but cant find it. 

gksudo gedit..in Gnome is what I know. Doesn't work in Konquerer of course. So what to do?
Thanks to anyone who can help
Dave

---

### Post by dave_h on 2006-12-11
Sorry....going quietly mad. I meant Konsole not Konquerer. Fraudian slip??
Dave

---

### Post by igknighted on 2006-12-11
1) You need to disable auto-login in order to choose sessions (or just logout after you log in).  There should be a menu on you login screen that lets you "Choose Session Type" and both KDE and GNOME should be listed.

2) The command for KDE would be 'kdesu kate /path/to/filename'.  Kate is the standard kde editor, but also kwrite is an option.  If GNOME is installed on the same partition you can still use gedit even in KDE.

---

### Post by dave_h on 2006-12-11
Hi and thanks for the info and help.
Now I know how to edit with kate (easy when you know how...impossible before someone guides you) I soon changed configurations but STILL cant get anything other than Kubuntu to load as default. 

Also when I (manually) boot to Ubuntu I dont see any session choices even if I log out and then log in again. And I found where auto-login is in Gnome and it was already disabled.

Any more ideas gratefully received.

I am a bit surprised that it seems few here have either seen this before or know it cant be done or dont know what may be going on as I thought grub was well established.

Thanks to all who have tried to help so far though.
Dave

---

### Post by dave_h on 2006-12-11
Well I can see session type selection if I boot into Kubuntu but not if I boot into Ubuntu. Anyone any ideas if this is normal, if what I am trying to do is impossible or how I can get the choice of KDE/Gnome when booting up Ubuntu. Thanks

---

### Post by bulldog on 2006-12-11
You already stated you have ubuntu as well as kubuntu installed on two different partitions.
This way you can choose which one you want to boot.
You should know however,which is which to do so.

If you boot in ubuntu (gnome) you can install ```
sudo aptitude install kubuntu-desktop
```so you have the choice in this install which you want to login.

To boot default to kubuntu install you have to change the option I provided in a previous post. {0 becomes 5}
This should work,however it could be four,but I don't think so.
You can change menu.lst ```
gksudo gedit /boot/grub/menu.lst
```
but before you do that,make a copy with this command```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
``` in case something goes wrong.

What you're trying to do isn't impossible,just a little over done,but hey,it's your computer.

---

### Post by dave_h on 2006-12-11
Bulldog! 
You get the Gold star award tonight. 
Firstly for your last statement " ...but hey it's your computer" saying that I may be trying something a bit unusual but why not. That to me is part of the spirit of Linux and Ubuntu but sadly something that I have not always found on some of the other newsgroups. I wont go on about that...although I'd love to.

Secondly for your advise about installing KDE within Ubuntu. It worked of course. But my surprise is that I did a similar install before using synaptic and it didn't work. ie i couldn't see KDE or more exactly a choice of sessions. 

I known that sometimes its best just to accept it and move on..... but I'd really like to know what I might have done wrong. Did I need to go into the CLI and do something like "install kde" ?? 

Anyway I now can select on log-in either a KDE or Gnome desktop under Ubuntu. (althought the splash screen at start-up say "Kubuntu"  any ideas how to change this.) But despite what you sugested I just can't get the thing to default to Ubuntu boot in Grub. Changed to default 4 and 5 but still no joy. 

The boot/grub/menu.lst files under Ubuntu and Kubuntu are still coming out different so is this the reason perhaps??
Dave

---

### Post by geek_Man on 2006-12-12
For your question about installing KDE, you would go to the terminal and type ```
sudo aptitude install kubuntu-desktop
```

---

### Post by Dr Dan on 2006-12-13
I'm quite new to linux, but maybe i can help. Ok, so .....

With regards to when you boot to ubuntu but you are getting a kubuntu splash screen try the instructions at [http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash) (when you installed kubuntu-desktop in ubuntu it changes the default, though your old splash is still there)

With regards to grub having kubuntu (on its own partition) as the default, i think the problem may be that you are editing the wrong menu.lst, i suspect grub is being run from you kubuntu partition not your ubuntu partition (ie going into ubuntu and editing it will have no effect). You should try selected the grub option which gets you into kubuntu, then editing the default in there to 4 and see if that helps.

good luck,
Dan :o :)

---

### Post by Herman on 2006-12-14
> Hi very new to Linux and for various reasons, including I wanted to explore both KDE and Gnome, I installed XP, Ubutu and Kubuntu in that order. 

At start-up Grub shows me 2 instances of Ubuntu (which are really Ubuntu and Kubuntu) and allows me to manually select which OS to boot but if I don't select any it will default to Kubuntu. So in Ubuntu (which I am more familiar with) I tried to change the default in /boot/grub/menu.lst However I can see XP but I can only see one occurence of what I think is Ubuntu and no Kubuntu. Even if I change the default to "saved" it still boots up into Kubuntu. Hello dave_h,
I think the best way to configure Grub to boot more than one Linux installation is to use 'configfile booting' for the other operating system rather than trying to directly boot the other kernel. That way you won't need to edit your menu.lst files is there is a kernel update. You can even configure Grub to boot backwards and forwards from one operating system's Grub menu to the other, by making a 'configfile' boot entry in the second system, that will bring up the first Grub menu again.

For example, you could edit your Ubuntu /boot/grub/menu.lst like this,
```
## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda4.
title        Kubuntu, (configfile boot on /dev/hda4)
savedefault
configfile    (hd0,3)/boot/grub/menu.lst



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

```And then also edit your Kubuntu /boot/grub/menu.lst like this,
```
## ## End Default Options ##

title Kubuntu, kernel 2.6.17-10-generic
root (hd0,3)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Kubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,3)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Kubuntu, memtest86+
root (hd0,3)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title         Ubuntu, (configfile boot on /dev/hda2)
savedefault
configfile    (hd0,1)/boot/grub/menu.lst



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
```If it is your Kubuntu Grub menu that is coming up instead of your Ubuntu menu, the best thing to do, (in my opinion), is to re-install Ubuntu's Grub to MBR.
Here's a link about how to do that using a LiveCD, and actually you can do the same thing from a terminal in either operating system just as easily.
                                      Re-install Grub with a GRUB shell eg; with Live CD..........................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

Those things are what I would do if it were my computer anyway. There is nothing wrong with booting as many Linux installations as you like. The computer I'm typing from now has Ubuntu 'Breezy Badger', 'Dapper Drake' with both KDE and Xubuntu desktops, and Ubuntu 'Edgy Eft'. When I'm ready, I'll add Feisty Fawn as well.
I feel more at home with the Gnome desktop, maybe because that's the one I'm familiar with and it seems nice and easy to use.
KDE seems more complicated, but there are some little things it seems to be able to do better. 

My main advice to people who want to triple or multiple boot is to use 'configfile' booting for other Linuxes. It's much better than trying to direct boot their kernels all the time.

Regards, Herman :D

---

### Post by albatroz2k on 2006-12-16
Does it may work for installing the edubuntu or xubuntu desktop too?

> **geek_Man said:**
> For your question about installing KDE, you would go to the terminal and type ```
sudo aptitude install kubuntu-desktop
```

---

### Post by geek_Man on 2006-12-17
> **albatroz2k said:**
> Does it may work for installing the edubuntu or xubuntu desktop too?

It should. You can pretty much sudo aptitude install anything. I don't know if the edubuntu desktop would be called edubuntu-desktop, maybe it is. But I'm sure xubuntu-desktop would work.

---

