---
title: "boot problems"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by arkara on 2007-09-09
i have a toshiba laptop and have the following problem

i had instaled pclinuxos i did not like it so much so got to the windows recovery console and typed fixmbr

then booted to windows normaly and deleted the partitions normaly through mycomp>manage

then rebooted with ubuntu live cd and tryed to install the system

during the installation ubuntu poped a msg about not able to mount a library.... i got scared

and clicked go back.. and not continue but the install stoped and me not knowing what to do
like a stupid 10 year old with no exp with pcs i rebooted only to see ms crap

ERROR OPERATING SYSTEM CANNOT LOAD or sth like that

anyway.. i got winxp disc in and entered recovey console in which i typed
fixmbr> then reboot > same prob
fixboot> then reboot >same prob
bootcfg /rebuild > then reboot > same prob

then diskpart and deleted the linux parts then reboot with ubuntu cd and re-install
this time the install was good and grub is ok
it boots both in windows and linux but
the /boot/grub/menu.lst is weird and so is grub
just look at it
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=58781033-8be8-4c44-8e23-2596ec1549d0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=58781033-8be8-4c44-8e23-2596ec1549d0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
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
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

so what happens here is that windows nt/xp/(loader) is actually  a link to windows xp boot loader in which the only option is : microsoft windows xp professional
from there windows boot normaly
so what can be done in order to boot directly to windows xp  through grub

cananyone help me??

---

### Post by merlinus on 2007-09-09
It is possible that grub did not get installed to the mbr.

If you have only one hdd, this may work:

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```

Substitute results from find for (hdx,y) and setup (hdx).

Given your menu.lst, it may well be:

root (hd0,1)
setup (hd0)

---

### Post by Herman on 2007-09-09
Hello arkara,
You can relax and be happy. :)
GRUB is not made for booting Windows directly, everyone's GRUB in the world works the same way when it comes to booting Windows or another operating system not supported by GRUB. GRUB hands over control to another boot loader at the first sector (boot sector), of the unsupported operating system's partition, that process is called 'chainloading'.

Probably it would be easy enough to design GRUB to boot Windows directly, but the GRUB developers probably don't want to, maybe because they don't want to be sued by Microsoft. I'm not a lawyer, but I am led to believe that Microsoft has a lot of strict rules and most people are scared to touch Microsoft's code too much at all I think. The licence agreement says something about not being allowed to 'disseminate' the software. So I guess that's why GRUB or LiLo or any other Linux bootloader will only 'chainload' Windows by it's boot sector.

Anyway, it works okay, that's the main thing. If you want to customize your GRUB, try looking in my third sig link, (at the bottom of this post), there is a  web page there about how to modify your GRUB to look and perform the way you like best. :)

Happy computing,
Regards, Herman :)

---

### Post by Herman on 2007-09-09
>  then diskpart and deleted the linux parts then reboot with ubuntu cd and re-install
this time the install was good and grub is ok
it boots both in windows and linux but
the /boot/grub/menu.lst is weird and so is grub
> so what happens here is that windows nt/xp/(loader) is actually a link to windows xp boot loader in which the only option is : microsoft windows xp professional
from there windows boot normaly
so what can be done in order to boot directly to windows xp  through grub

cananyone help me?? Now that I have read your post again, I think maybe you are asking how to make Windows first in teh boot order so it will boot by default if no keys are pressed.

Just copy your Windows boot entry, for example, this part,
```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
and paste it right up around the midddle of your /boot/grub/menu.lst file.
Make sure it is** above** the line that says,
[URL="http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST"]```
### BEGIN AUTOMAGIC KERNELS LIST
```[/URL]
It must be above that line and not inside the Debain Automagic Kernels list or else it will be automatically deleted when you get a kernel update for Ubuntu. But if it's above that line it will be okay.

Regards, Herman :)

---

### Post by arkara on 2007-09-09
the funny thing is that its not the fist time that i install ubuntu

the last time grub booted windows directly and i didnt have to choose it twice
but now i have to do double check

thats the broplem i need windows to boot directly from grub

---

