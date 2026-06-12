---
title: "Making WIndows default"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by Jamesia on 2005-04-14
I installed Hoary recently, and I have a dual boot system with WIndows XP. Both Windows and Hoary work wonderfully, but I was wondering how to make Windows the default at boot up. Right now, Ubuntu is default, and unless I'm watching my laptop boot up, it defaults to Ubuntu. Needless to say, I don't usually watch my laptop boot up. Thanks!

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=Jamesia]I installed Hoary recently, and I have a dual boot system with WIndows XP. Both Windows and Hoary work wonderfully, but I was wondering how to make Windows the default at boot up. Right now, Ubuntu is default, and unless I'm watching my laptop boot up, it defaults to Ubuntu. Needless to say, I don't usually watch my laptop boot up. Thanks![/QUOTE]

You have to tweak GRUB's config. If I remember correctly, the file you want is "/boot/grub/menu.lst". Just find the entry for Windows, cut it, and paste it above all the Linux entries. If /boot/grub/menu.lst is empty or doesn't exist, do the same to /boot/grub/grub.conf. Make sure to read GRUB's documentation before meddling with  it.

---

### Post by p!=f on 2005-04-14
```

sudo gedit /boot/grub/menu.lst

```
> 
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

Change that number to match the entry for Windows in that file.

---

### Post by andvaranaut on 2005-04-14
Hi Jamesia,

In Ubuntu, edit /boot/grup/menu.lst (with gedit or any other). Then, locate the Windows bootup section. It should look like the following:

title Windows
	rootnoverify (hd0,0)
	chainloader +1

and will probably be the last one. Move these 3 lines towards the top of the file, just before the line that reads "BEGIN AUTOMAGIC KERNEL LIST" , and verify that there is a line which reads 'default 0' somewhere at the beginning of the file (it should). Note that the hd0,0 part might be different on your system.

Windows should now be the first option in the grub menu, and the first option is the one that gets booted by default. Reboot and enjoy.

Why anyone would prefer WinXP over Ubuntu is beyond me, but that's an entirely different matter ;)

Best regards

---

### Post by Buffalo Soldier on 2005-04-14
Example of a menu.lst entry:```
title		Ubuntu, kernel 2.6.10-5-k7 **<- entry number *0***
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-k7
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-k7 (recovery mode) **<- entry number *1***
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.10-5-k7
savedefault
boot

title		Ubuntu, kernel memtest86+ **<- entry number *2***
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems: **<- entry number *3***
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional **<- entry number *4***
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
So if what you want is to make WinXP the default OS when booting, substitute *0* with *4*. Example:```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
**default *4***
```

---

### Post by Jamesia on 2005-04-14
Hey, thank you all for the quick response! That works well!

---

### Post by LieToPurify3 on 2007-08-23
I tried doing this too, but when I go to save my modified menu.lst, it says that it is read only and I do not have permission.  It asks if I would like to try to replace the original file, but that does not work either bc of my permissions.  I don't know why I dont have permission.  I am the only user, so wouldn't I be the superuser?  I never created new users; this is the user I created during install

---

### Post by maybeway36 on 2007-08-23
Moves Windows to the top first, or else the default changes when you upgrade the kernel.

---

### Post by LieToPurify3 on 2007-08-23
thank you!

---

### Post by Herman on 2007-08-23
Ubuntu is Linux, it doesn't work like Windows, the ordinary user or possibly an internet cracker (theoretically), or malware writers are not allowed to make important system changes like in Windows without the superuser's password. 
You can navigate to the /boot/grub/menu.lst file in GUI mode easily enough, and you can even open the file and read it, you can even try to write to it, but Ubuntu won't let you save the changes.
The proper way to make important system changes in Ubuntu is to open the file as superuser, or root. Most of us use a sudo command,
```
sudo gedit /boot/grub/menu.lst
``` After you type that command (or copy it from here and paste it into your terminal, when you press enter, you will be asked for your password. Then the file will be opened and you can edit it and save the changes.

---

### Post by merlinus on 2007-08-23
I have read that it is better to use

gksudo

rather than sudo

for graphical apps.

e.g.

```

gksudo gedit /boot/grub/menu.lst

```-merlin

---

### Post by Herman on 2007-08-23
You can do it the way Buffalo Soldier described,
> Example of a menu.lst entry:     Code:
     title        Ubuntu, kernel 2.6.10-5-k7 **<- entry number *0***
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.10-5-k7 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.10-5-k7
savedefault
boot

title        Ubuntu, kernel 2.6.10-5-k7 (recovery mode) **<- entry number *1***
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.10-5-k7 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.10-5-k7
savedefault
boot

title        Ubuntu, kernel memtest86+ **<- entry number *2***
root        (hd0,1)
kernel        /boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems: **<- entry number *3***
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional **<- entry number *4***
root        (hd0,0)
savedefault
makeactive
chainloader    +1 
So if what you want is to make WinXP the default OS when booting, substitute *0* with *4*. Example:     Code:
     # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
**default *4***
Or you can do it something like the way andvaranaut described,
> In Ubuntu, edit /boot/[COLOR=Red]grub[/COLOR]/menu.lst (with gedit or any other). Then, locate the Windows bootup section. It should look like the following:

title Windows
    rootnoverify (hd0,0)
    chainloader +1

and will probably be the last one. Move these 3 lines towards the top of the file, just [COLOR=Red]above[/COLOR] the line that reads "BEGIN AUTOMAGIC KERNEL LIST" , and verify that there is a line which reads 'default 0' somewhere at the beginning of the file (it should). Note that the hd0,0 part might be different on your system.

Windows should now be the first option in the grub menu, and the first option is the one that gets booted by default. Reboot and enjoy.Whatever you do, don't paste your Windows entry anywhere inside the automagic kernels list, or it will be deleted whenever you have a kernel update.
The debain automagic kernels list begins with the line, ### BEGIN AUTOMAGIC KERNELS LIST
and ends with the line, ### END DEBIAN AUTOMAGIC KERNELS LIST
so  it is quite clearly marked, so no-one is likely to make a mistake.

---

