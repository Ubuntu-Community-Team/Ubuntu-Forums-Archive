---
title: "Boot up Windows xp"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by TedAndrews on 2008-06-01
Ii have just installed Ubuntu 8.04 on my pc with Win XP.
The pc boots to Ubuntu by default without selecting from the boot window.
How can I alter this so Windows XP is the default boot program.
I am just exploring ubuntu and my wife also uses the pc so XP is needed.

---

### Post by logos34 on 2008-06-01
Change the 'default' line in menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

---

### Post by mrtomservo on 2008-06-01
At a terminal type 

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.backup
sudo gedit /boot/grub/menu.lst
```

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

Change the default number to whatever one corresponds to your Windows installation.

> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a24d3901-0aa9-4f2c-93f0-80aa280f6ed5 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a24d3901-0aa9-4f2c-93f0-80aa280f6ed5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

The counting starts at 0, so 0 is the main Ubuntu, 1 is the Rescue mode, 3 is the memory check, and 4 is windows.  

Hope that helps!

---

### Post by lswest on 2008-06-01
> **mrtomservo said:**
> At a terminal type 

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.backup
sudo gedit /boot/grub/menu.lst
```



Change the default number to whatever one corresponds to your Windows installation.


[B]
The counting starts at 0, so 0 is the main Ubuntu, 1 is the Rescue mode, 3 is the memory check, and 4 is windows.  [/B]

Hope that helps!

he means 0 is ubuntu, 1 is the rescue, 2 is the memory check, 4 is windows (3 would be the seperator)

If you don't want to edit system files you can do: ```
sudo apt-get install startupmanager
``` and then under system-->administration-->startup-manager  you can choose from a drop down list the "default operating system" which is the default choice for GRUB to load.

---

### Post by mihailojocic on 2008-06-01
Or just install Acronis OS selector and do that in seconds.

---

### Post by TedAndrews on 2008-06-01
Thanks to All. I am now booting into XP

---

