---
title: "XP wont boot after Ubuntu install!"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by rsvirani on 2005-09-15
Hey guys. I have recently installed 5.04 and it rocks. But, I need dreamweaver 8 and flash 8 and I think its going to be a long time before this can run properly with stuff like WINE etc. Anyway I have XP on the first partition and ubuntu's boot loader has taken over. I want to use it and not the XP loader but it will not load windows when i select to boot it. I tried to do a repair install on xp but it wont boot still. Anyoen have the same problem or have any suggestions? Is there misconfiguration in the boot loader on how to launch the windows install? I dont want to reinstall it and dont want to delete the partition. There must be some simple fix. Nothing is corrupt or missing. Can anyone help?

This is what is left after selecting to boot to it:

 save default
 make active
 chain loader +1

and it hangs there.

---

### Post by manicka on 2005-09-15
Can you post the contents of /boot/grub/menu.lst

---

### Post by Northy on 2005-09-15
I think there should be another line at the start, such as:

root (hd0,0)

'm afraid I only installed Linux a few days ago, so I'm pretty new to it.  I know the argument after the comma has to do with the type of partition format.  If you type "help root" into the command line of the GRUB then it might give you some more advice.  Alternatively, someone else may know more.

Hope that helps.

---

### Post by jackmacokc on 2005-09-15
[QUOTE=rsvirani]Hey guys. I have recently installed 5.04 and it rocks. But, I need dreamweaver 8 and flash 8 and I think its going to be a long time before this can run properly with stuff like WINE etc. Anyway I have XP on the first partition and ubuntu's boot loader has taken over. I want to use it and not the XP loader but it will not load windows when i select to boot it. I tried to do a repair install on xp but it wont boot still. Anyoen have the same problem or have any suggestions? Is there misconfiguration in the boot loader on how to launch the windows install? I dont want to reinstall it and dont want to delete the partition. There must be some simple fix. Nothing is corrupt or missing. Can anyone help?

This is what is left after selecting to boot to it:

 save default
 make active
 chain loader +1

and it hangs there.[/QUOTE]
 you can always reload the windows boot loader by booting in to the recovery console using a winxp cd, then using the command "fixboot" and "fixmbr". This will repair the master boot record to use the NT boot loader. 

You should have no problems using grub though..probably just need to set it to use the right partition. what you listed to boot to it selects no partition. what are you specifying as the root for your winxp entry? such as below

# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1

do you have a root entry?

---

### Post by rsvirani on 2005-09-15
Thanks for all the feedback guys.  I am actually not home in front of my system and wasnt expecting sucha quick response.  I will shortly post the following:
 
 /boot/grub/menu.lst
 
all lines including root entry

output of that command in the root console that lists partitions

Also, about the reply stating I could use fixboot and fixmbr to get back the XP boot screen, will it allow me to boot to ubuntu?  Can i make a simple change to my boot.ini to add the options that are equivalent to grub?  or will i need to use a boot disk :( ?

---

### Post by rsvirani on 2005-09-16
*****This is my menu.lst file******


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title        Ubuntu, kernel 2.6.10-5-386 
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash
initrd        /boot/initrd.img-2.6.10-5-386
savedefault
boot

title        Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro single
initrd        /boot/initrd.img-2.6.10-5-386
savedefault
boot

title        Ubuntu, kernel memtest86+ 
root        (hd0,2)
kernel        /boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

*****The above is also what the system displays when it hangs after selecting windows from GRUB******

This is the output of fdisk -l:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
16 heads, 63 sectors/track, 193821 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       58156    29310561    7  HPFS/NTFS
/dev/hda2           58156      154881    48749242+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3          154881      193816    19623397+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5           58157      153160    47881701    7  HPFS/NTFS
/dev/hda6          153160      154881      867478+  82  Linux swap / Solaris




What should I do?

---

### Post by manicka on 2005-09-16
I've never seen an fdisk output like that before, so I can't help you there

My windows grub entry looks like this

```
title TOCOS
	rootnoverify (hd0,0)
	makeactive
	chainloader +
```

TOCOS being my pet name for Windows

HTH

---

### Post by jackmacokc on 2005-09-16
[QUOTE=rsvirani]
Also, about the reply stating I could use fixboot and fixmbr to get back the XP boot screen, will it allow me to boot to ubuntu?  Can i make a simple change to my boot.ini to add the options that are equivalent to grub?  or will i need to use a boot disk :( ?[/QUOTE]

As far as I know the answer is no. I havent heard of anyone using NT bootloader to boot into ubuntu, but that doesnt mean its not possible. Most likely its not...personally, I find grub much better than NT bootloader. Much easier to mess with and much easier to fix.

---

### Post by jackmacokc on 2005-09-16
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1 

I bet if you change root (hd0,0) to root (hd1,0) it might work.

---

### Post by rsvirani on 2005-09-21
I still cant get it to work.  Any other suggestions?

---

### Post by ngms27 on 2005-09-21
Here is what is on my system:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-k7 
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-k7
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-k7 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.10-5-k7
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,6)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


This dual boots with no problems.

HTH

JonnyT

---

### Post by rsvirani on 2005-09-22
Your windows entry is identical to mine and has the same location as mine.  What else could be wrong.  Any suggestions?  Is there something i need to do to that partition to restore its bottability (besides reloading the windows OS chooser)?

---

### Post by dbott67 on 2005-09-22
[QUOTE=rsvirani]Your windows entry is identical to mine and has the same location as mine.  What else could be wrong.  Any suggestions?  Is there something i need to do to that partition to restore its bottability (besides reloading the windows OS chooser)?[/QUOTE]

Well, it's not really a fix, but it may do the trick:

You'll need to read & print out [these instructions](http://geodsoft.com/howto/dualboot/grub.htm) carefully and make a GRUB floppy disk.

You may also want to print out your current GRUB configuration file / partition information, as you may need it for reference.

1. Boot into Ubuntu, create a GRUB boot disk following the instructions from website (you'll install Grub after running FIXMBR in XP).  Follow the instructions on how to get it to boot from the floppy & allow you to get into Ubuntu.  Test it to make sure that you can boot from floppy into Ubuntu.

2. Reboot with XP CD & select REPAIR --- boot into the console.  Type: fixmbr
Note: this should hose GRUB on the HD, but should allow you to boot into XP

3. Reboot the computer to make sure you can get into XP.

4. Reboot with GRUB floppy & follow the instructions on how to install GRUB onto the hard drive from above webpage.  

HTH,
Dave

---

### Post by dbott67 on 2005-09-24
I found another method that may be easier to restore GRUB after using the FIXMBR command:

[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

-Dave

---

