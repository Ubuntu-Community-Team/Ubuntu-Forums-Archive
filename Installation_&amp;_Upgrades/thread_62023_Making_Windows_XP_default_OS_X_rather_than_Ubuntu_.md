---
title: "Making Windows XP default OS X rather than Ubuntu in Grub.conf file"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by TJ07985 on 2005-09-03
Hi.

At this point in time, I have both Windows XP and Ubuntu installed on the same hard drive, on two separate partitions.  When I installed Ubuntu, I just picked the default install where Ubuntu used the remaining free space on the drive for its partition.

Anyway, what I want to do now is change the GRUB.conf file so that Windows XP, rather Ubuntu, is the default OS that the computer boots up to.  How do I do this?
Is there any particular commands or lines of code I need to add the GRUB.conf file?  Please let me know, thanks.  I'm relatively new at this, so you'll have to walk me through it step by step.

---

### Post by fuse3k on 2005-09-03
[http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)

On a default GRUB config your Windows option is more then likely 4.

---

### Post by manicka on 2005-09-03
In hoary I used to just copy/move the XP entry to the top of the list.

Breezy has a nice control panel that does this for you now

---

### Post by fuse3k on 2005-09-03
I made some small changes to mine. Sound like this is what you want for the mos part. This is what it looks like (dont' copy it, just use it as reference):

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
[COLOR=Red]**default         0**[/COLOR]

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
## by the debian update-grub script except for the default optons below

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
# groot=(hd0,1)

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu Linux 5.04 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		--  
root

title		--  
root

title		Other operating systems:
root

title		Ubuntu Linux 5.04 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu Linux 5.04 memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


```

---

### Post by TJ07985 on 2005-09-03
[QUOTE=fuse3k][http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)

On a default GRUB config your Windows option is more then likely 4.[/QUOTE]


Yes, on my GRUB.config file, Windows XP IS option #4.  However, I'm still confused as to what changes need to be made to the grub.conf file to get Windows XP as the default OS.  Perhpaps you could color code the text that needs to be added in the example grub.conf file?

---

### Post by TJ07985 on 2005-09-03
[QUOTE=fuse3k]I made some small changes to mine. Sound like this is what you want for the mos part. This is what it looks like (dont' copy it, just use it as reference):

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
default         0

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
## by the debian update-grub script except for the default optons below

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
# groot=(hd0,1)

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu Linux 5.04 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		--  
root

title		--  
root

title		Other operating systems:
root

title		Ubuntu Linux 5.04 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu Linux 5.04 memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


```[/QUOTE]


**Perhaps you could color code the text that needs to be added to the sample grub.conf file?  I'm not quite sure what you did is different from the example grub.conf contained in the link in one of the replies above.**

---

### Post by MetalMusicAddict on 2005-09-03
Isnt "GrubConfig" in the repos now? That would be the easiest. Honestly though youll learn more if you leave it set to Ubuntu. *Kinda* forces you to work in it.

---

### Post by Buffalo Soldier on 2005-09-03
There is a way to change the default boot from Ubuntu to WinXP. Refer to: [http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)

note: X_sequence = the order of the *title* entry on the menu. For example if WinXP is the fifth entry on the menu then your X_sequence should be 4. (start counting from 0).

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
[color=red]default		**0**[/color]

**title**		Ubuntu, kernel 2.6.10-5-686 [color=red]<- first entry[/color]
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

**title**	Ubuntu, kernel 2.6.10-5-686 (recovery mode) [color=red]<- second entry[/color]
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

**title**	Ubuntu, kernel memtest86+ [color=red]<- third entry[/color]
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
**title**	Other operating systems: [color=red]<-  fourth entry[/color]
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
**title**		Microsoft Windows XP Home Edition [color=red]<- fifth entry[/color]
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by xmastree on 2005-09-03
[QUOTE=TJ07985]Yes, on my GRUB.config file, Windows XP IS option #4.  However, I'm still confused as to what changes need to be made to the grub.conf file to get Windows XP as the default OS.  Perhpaps you could color code the text that needs to be added in the example grub.conf file?[/QUOTE]
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
[COLOR=Red]**default         0**[/COLOR]
```

---

### Post by fuse3k on 2005-09-03
[QUOTE=xmastree]```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
[COLOR=Red]**default         0**[/COLOR]
```[/QUOTE]
 Thanks for for highlighting. btw, remember starting counting from 0 and not 1. As you can see My WinXP OS is the first one, hence "default        0"

---

### Post by chippy57 on 2005-09-03
[QUOTE=TJ07985]Yes, on my GRUB.config file, Windows XP IS option #4.  However, I'm still confused as to what changes need to be made to the grub.conf file to get Windows XP as the default OS.  Perhpaps you could color code the text that needs to be added in the example grub.conf file?[/QUOTE]

I had the same problem as you, looked for hours for an answer until I stumbled on this thread and thanks to you guy's I now have harmony in my household  \\:D/  and now I can ubuntu to my hearts content. Anyway it all I did was change :-

default    **[COLOR=Red]0[/COLOR]**

to

default    **[COLOR=Red]4[/COLOR]**

as my winxp was the 5th entry, I even changed the timeout to 5 secs...and so after my quivering sphincter settled I bit my lip clicked on save and rebooted......voila after 5 secs xp booted in....no stopping me now.

thanks a million guys... now on to setting up my RAID  ADSL da da da etc.....sigh!reminds me of my old amiga days.

best regards

chips

---

