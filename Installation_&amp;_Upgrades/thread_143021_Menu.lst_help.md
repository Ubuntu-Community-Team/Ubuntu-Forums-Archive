---
title: "Menu.lst help"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by WoodPost on 2006-03-11
I need help setting up my menu.lst, here is my fdisk -l

```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5933    47656791   fd  Linux raid autodetect
/dev/sda2   *        5934       30515   197454915   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10172    81706558+   b  W95 FAT32
/dev/sdb2           10173       24212   112776300    f  W95 Ext'd (LBA)
/dev/sdb3           24213       24577     2931862+  82  Linux swap / Solaris
/dev/sdb4           24578       30515    47696985   fd  Linux raid autodetect
/dev/sdb5           10173       24212   112776268+   7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9725    78116031    7  HPFS/NTFS
```

and my menu.lst
```

title		Ubuntu, kernel 2.6.12-9-386 
root		(sda2,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(sda2,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(sda2,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hda1,0)
savedefault
chainloader	+1
```

Thanks for the help

---

### Post by kaptainlange on 2006-03-11
What are you trying to accomplish exactly?

ie. boot to windows?

Need more specifics.

---

### Post by WoodPost on 2006-03-11
When i try to boot into anything, a get a grub error stage 2, error 15, "Error while parsing number."  I'm not sure what (X,Y) to use for my drives in grub.

---

### Post by kaptainlange on 2006-03-11
I'm not too sure what those number should be exactly for your system either.  Those would be what I would have put as well.

The only suggestion I could give you is go into the grub boot loader menu, don't boot anything, but instead go into grub's command line.

Once there type:

root (x,y)

and try different combinations that you think are appropriate for your system.  If the root you specify is valid, it should say what the filesystem of that new root is.  This way you can figure out which partitions your OS'es reside on.

Not the most elegant solution, but the best I can think of at the moment.  Let me know how it goes.

---

### Post by munga_bill on 2006-03-11
When you are in grub's command line try:[code] find /vmlinuz [code] and it should give you back the answer like (hd0,1) or something like that.

---

### Post by WoodPost on 2006-03-11
I've gotten ubuntu to boot fine, in grub all hard drives are named as (hd*x,y*), not sda, or sdb. Windows still won't boot, even with the right disk, (hd2,1)

---

### Post by DaBruGo on 2006-03-11
[QUOTE=WoodPost]I've gotten ubuntu to boot fine, in grub all hard drives are named as (hd*x,y*), not sda, or sdb. Windows still won't boot, even with the right disk, (hd2,1)[/QUOTE]

WoodPost,

If you are wanting to boot Windows from your GRUB menu, take a look at my setup guide down below in my signature lines.

In the first post of that thread, take a look at STEP 11. Then, look at post #2 to tweak your settings in GRUB menu.lst to boot Windows.

Let me know if that helps you get a little closer to success.


DAVE

---

### Post by munga_bill on 2006-03-12
Try DaBruGo's suggestion first, and if that works, then good...
If not, is Windows on your third disk, second partition? (hd2,1) or on your third disk, first partition (hd2,0)? Presuming it is (hd2,1) as you say, then try  and see if Windows will boot from the command line in Grub when you type:

map (hdO) (hd2)
map (hd2) (hd0)
rootnoverify (hd2,1)
makeactive
chainloader +1
boot

If not, try (hd2,0) instead of (hd2,1).
 The map commands are used to trick windows into thinking it's on the first hard disk. You could try different numbers there too, sorry, I'm not sure about how you particular set-up affects the numbering system either for 100% certian. When you get it to boot, then edit your /boot/grub/menu.lst with those commands.```

```Regards, munga_bill

---

### Post by WoodPost on 2006-03-12
I'm not sure how to set up the map command, so here is what i have,
```
title		Microsoft Windows XP Home Edition

root		(hd2,0)

savedefault

chainloader	+1
```
XP is on the third drive, first partation.
```
Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9725    78116031    7  HPFS/NTFS
```
My two SATA drive are listed before the 80gb IDE drive during boot.

---

### Post by munga_bill on 2006-03-12
If that works alright then good. (I'm not really sure whether you are still asking for help or are telling us you have solved it and you are okay now.)

If it doesn't, then experiment with the commands some more at the GRUB command line. (Type 'c' at the Grub menu). The GRUB command line is great because you can experiment there until you find something that works and it'll even give you a little helpful feedback sometimes.  
When you can get it to boot, remember the commands you used and then later, replace the commands in menu.lst with the ones that worked for you from the command line (when you have Ubuntu booted). 
I didn't know you could get away without using the map commands when Windows isn't on your first disk. The numbers already given should be right I think, given that XP is on your third drive. Maybe experiment with placing the map commands second or third in the series of commands.

---

### Post by WoodPost on 2006-03-12
I still can't get windows to boot. Now I'm gettihng the error on the "Map" part. It looks something like this;
error 15, "Error while parsing number"  Map (x,y) (x,y)

---

### Post by DaBruGo on 2006-03-13
[QUOTE=WoodPost]I'm not sure how to set up the map command, so here is what i have,
```
title		Microsoft Windows XP Home Edition

root		(hd2,0)

savedefault

chainloader	+1
```
XP is on the third drive, first partation.
```
Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9725    78116031    7  HPFS/NTFS
```
My two SATA drive are listed before the 80gb IDE drive during boot.[/QUOTE]

WoodPost,

If GRUB added the menu.lst line for XP that says ...

root		(hd2,0)

Then try these commands in your menu.lst file for XP ...

title     Microsoft Windows XP Home Edition
root     (hd2,0)
map     (hd2) (hd0)
chainloader +1


Those are the only commands I have in my menu.lst file for XP and it works for me. You shouldn't need both map commands in there. We just want to map XP to (hd0) so it thinks it is on the first drive in the system.

Just make sure you have the correct "root" command line for XP in your menu.lst file and then use that root info for the map command (without the partition info [,0] being used) and it should work for you.

[Here]("http://www.ubuntuforums.org/showpost.php?p=593793&postcount=112") is a forum link to help you temporarily edit GRUB when it freaks out at bootup to test which settings work. You can adapt it to see what drive/partition settings you need for XP.

Hope it works out. Let me know if you get it going.

DAVE

---

### Post by WoodPost on 2006-03-13
Thank you very much DaBruGo, that setup now boots my windows drive without a problem.

---

### Post by DaBruGo on 2006-03-13
[QUOTE=WoodPost]Thank you very much DaBruGo, that setup now boots my windows drive without a problem.[/QUOTE]

That's awesome! I'm glad I could help.



DAVE

---

### Post by WoodPost on 2006-03-14
And I thoguht I was done. I have one more little problem I would like help with. I know all the steps and how you supposed to set up Grub to boot what you want, but its not working for me. I'm sure its just a little error somewhere, can you help me? So heres my Menu.lst

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

default		9



## timeout sec

# Set a timeout, in SEC seconds, before automatically booting the default entry

# (normally the first entry defined).

timeout		5



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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single


## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash


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

title		Ubuntu, kernel 2.6.12-10-686-smp 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda2 ro quiet splash

initrd		/boot/initrd.img-2.6.12-10-686-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686-smp (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda2 ro single

initrd		/boot/initrd.img-2.6.12-10-686-smp
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro quiet splash

initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro single

initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro quiet splash

initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro single

initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/hda1

title Microsoft Windows XP Home Edition

root (hd2,0)

map (hd2) (hd0)

chainloader +1

savedefault
```

Aslo, how do you kepp it from double spacing when i put in the code tags?

---

### Post by DaBruGo on 2006-03-14
[QUOTE=WoodPost]And I thoguht I was done. I have one more little problem I would like help with. I know all the steps and how you supposed to set up Grub to boot what you want, but its not working for me. I'm sure its just a little error somewhere, can you help me? So heres my Menu.lst

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

default		9



## timeout sec

# Set a timeout, in SEC seconds, before automatically booting the default entry

# (normally the first entry defined).

timeout		5



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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single


## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash


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

title		Ubuntu, kernel 2.6.12-10-686-smp 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda2 ro quiet splash

initrd		/boot/initrd.img-2.6.12-10-686-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686-smp (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda2 ro single

initrd		/boot/initrd.img-2.6.12-10-686-smp
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro quiet splash

initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro single

initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro quiet splash

initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro single

initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/hda1

title Microsoft Windows XP Home Edition

root (hd2,0)

map (hd2) (hd0)

chainloader +1

savedefault
```

Aslo, how do you kepp it from double spacing when i put in the code tags?[/QUOTE]

Is windows still booting OK?


DAVE

---

### Post by WoodPost on 2006-03-14
Yes, windows is still booting fine, but my family prefers that windows is booted by defult, so they don't find themselfs in ubuntu.

---

### Post by DaBruGo on 2006-03-14
[quote=WoodPost]Yes, windows is still booting fine, but my family prefers that windows is booted by defult, so they don't find themselfs in ubuntu.[/quote] 
WoodPost,

 What I would do in that situation is place the Windows bootup lines above the automagic section in the menu.lst file (so it will always be first on the list) and set it as the default boot option by having it as the only configuration with savedefault in its lines. (See this [LINK]("http://ubuntuforums.org/showpost.php?p=774688&postcount=12") for details).

 By setting it that way, GRUB will always boot Windows by default (after so many seconds) unless you arrow down to another option manually before time runs out. Plus, the settings will never get messed up when updating the kernel for Ubuntu. ( Just make sure to use 0 on your default line near the top of the menu.lst file instead of 9. )

Then, what I would do, is experiment with the technique up in post #12 of this thread (print it out) to see what root commands will get your Ubuntu up and running.

Hope that helps.


DAVE

---

