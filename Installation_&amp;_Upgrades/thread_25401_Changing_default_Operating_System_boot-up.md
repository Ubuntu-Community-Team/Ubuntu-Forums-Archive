---
title: "Changing default Operating System boot-up"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by dworzec.net on 2005-04-10
hi,
I've just installed Kubuntu 5.4 but as I am the only one who uses it - the rest of my family (still) prefer Win XP, I am forced to make XP my default system on boot-up. In Mandrake there was this pretty easy tool for reconfiguring LILO, but in Kubunt I can't find anything like that... I found   [this](http://ubuntuforums.org/showpost.php?p=110768&postcount=4)    but I can't find grubconf in Kynaptic (I enabled universe).
I might try from ubuntu starter's guide this
> How to change default Operating System boot-up for GRUB menu?
$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
$ sudo gedit /boot/grub/menu.lst

Find this line 

...
default         0
...

Replace with the following line 

default         X_sequence

Save the edited file (sample)
but I'm a bit affraid of messing with grub (link to "sample" doesn't work). Did they mean this "default 0" at the very beginning of the file:
> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
**default		0**?
and should I replace it with "default         X_sequence" or put some kind of number in "X" place?
and final question - if how can I make floppy with grub (starting disk), just in case something goes wrong... or live cd is better solution to get to my harddisk in case of any problems with grub?
thanks,
dworzec.net

---

### Post by Buffalo Soldier on 2005-04-10
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

### Post by dworzec.net on 2005-04-10
thanks for the very fast answer! it's easier than I thought and there's nothing I could spoil...
btw. someone could activate this "sample" link in ubuntu starter's guide, as it's not working and someone may have the same doubts in future
thanks again,
dworzec.net

---

