---
title: "Dual boot Ubuntu - Linux"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by dkmxbe on 2005-07-19
hi

not a long time ago, i've installed my xp again ( because my windows was a bit to slow ) 

alsow i have ubuntu @ my second hard drive ( i made a partition for it )

everything went fine ( i had a nice boot menu ) windows xp - ubuntu

no problem, but when i installed my xp again, i had no boot menu anymore  :mad: 

so i want to know what i must write under 


[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 


ps: i can't use a method like boot into ubuntu and then place that file on a disk and then add it to my c: .. . . 

because i don't  know how to boot into ubuntu >> and my default os is                                       

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

---

### Post by dave9191 on 2005-07-19
When you installed windows it decided to overwrite you grub menu that gave you the choice of both with just the windows one becuase its mean like that. There are pleanty of guides out there which tell you how to do what you are asking but you need to boot into linux to do that. 

[http://www.highlandsun.com/hyc/linuxboot.html](http://www.highlandsun.com/hyc/linuxboot.html)

I think that it would be better to install grub again and have that as a menu rather then mess around with the windows way, which requires you to copy over stuff from linux each time you make a change to the linux. 

The simlest thing to do would be to install ubuntu again, but you can also boot into linux using a Live CD of one sort or another and install grub into the mbr again. The latter way you wouldnt need to reinstall linux, just the boot loader. 

Dave

---

### Post by mingus on 2005-07-19
*because i don't  know how to boot into ubuntu *

Boot from the installation CD using "rescue" at the colon prompt.  You will be taken thru about 10 screens, the last one will ask you which partition root (/) is on.  That partition will be mounted and you will be dropped into a simple shell as root.  From there you can do:
#grub-install /dev/hda
that will reinstall grub in the Master Boot Record.

Note:  If grub-install is not avail as a command in that shell, type Ctrl-Alt-F2 for a different shell.  Grub-install should work from there.  Also, this procedure assumes you did not create a separate partition just for /boot - if you did, this procedure will need to be changed a bit.

---

### Post by Buffalo Soldier on 2005-07-19
Try the guide at [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

1. Boot-up computer into Ubuntu Installation CD

2. At "boot:" prompt, add "rescue" to the argument
```
boot: rescue
```

3. Assuming that /dev/hda is the location of /boot partition
```
grub-install /dev/hda
```

---

