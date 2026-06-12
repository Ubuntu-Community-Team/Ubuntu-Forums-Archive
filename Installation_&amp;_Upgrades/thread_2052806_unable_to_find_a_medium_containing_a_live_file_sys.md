---
title: "unable to find a medium containing a live file system."
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by MahZadYar on 2012-09-04
I'm using an old VAIO laptop PCG-Z505GA ([COLOR="red"]Pentium III 700MHz - 128MB of RAM[/COLOR]) with an [COLOR="red"]external ATAPI CD-ROM drive[/COLOR] an [COLOR="red"]no UBS boot option on BIOS[/COLOR]! I have tried to install a couple of Ubuntu based GNU/Linux Distributions ([COLOR="red"]Ubuntu, Lubuntu, Peppermint and Debian[/COLOR]) by booting from CDs.
It [COLOR="red"]boots correctly[/COLOR] but when I select "try without installing" or "install" or "Check for Disk integrity" it says:
```

stdin: error 0
/init: line 7: can't open /dev/sdb: No medium found
/init: line 7: can't open /dev/sdb: No medium found
uable to open '/dev/zram0'

```
repeatedly while the read light on the CD-ROM drive is off and it doesn't try to read anything from the CD. (it doesn't blink even once!)
then after a while:
```
(initramfs) unable to find a medium containing a live file system.
```
I know the problem is not from the CD itself or the integrity or burning issues stuff, cause I've tried lots of CDs, in different Ubuntu based distros burnt on low speed.
So... [COLOR="red"]What's up with it[/COLOR]?!!

---

### Post by MahZadYar on 2012-09-04
I made a bootable USB from the CD (can't boot from it cause there is no USB boot option in the damn old BIOS!) , I put it in, boot it from the CD
I checked the disk for defects it strangely it started to [COLOR="Red"]read from the USB[/COLOR] Drive, checked all the stuff from the USB ([COLOR="red"]the CD-ROM light was constantly off[/COLOR]) and it said [COLOR="red"]there is no probs with it[/COLOR]! then i started to install it this way: [COLOR="red"]Boot from the CD with the exact stuff on the USB[/COLOR]!
The so-mentioned errors was gone and some other stuff passed by untill the screen blanked and i saw [COLOR="red"]a mouse pointer on a black screen[/COLOR]... the usb light kept blinking but [COLOR="red"]nothing happened during 4 hours[/COLOR]!
so... [COLOR="red"]HELP[/COLOR]!

---

### Post by Torello on 2012-10-15
Hello, I think I've found universal solution, for this problem:

Use this steps:

1) Download linux iso image, which you want to install.
2) Download LinuxLiveUsb from [http://www.linuxliveusb.com/download](http://www.linuxliveusb.com/download)
3) You will need both usb-stick so and dvd-disk. ( Size of usb-stick must be more then size of Linux iso image ).
4) Write a downloaded Linux image on dvd-disk.
5) Write same Linux image on usb-stick, using LinuxLiveUsb.
Warning: You will lose all your data, that already on usb-stick, so if it contains something useful, backup it first.
6) Now insert in your pc both usb-stick and DVD-disk.
7) Boot from DVD( on Asus motherboards you can use F8 to choose boot device, on some Gigabyte motherboards you can use F11 key ).
8.) Now try to install your Linux.

I've came to that solution, when I've try to install Linux Mint 13 on one of my old computers( It has not any option to boot from usb ). So if I'm right that's why it work: we use loader from DVD, then when Linux try to find media with it installation data, it fails to find DVD, but it can find a usb-stick, and it continues installation, using this usb-stick.

Please, leave a post, if that solution helps you.

---

### Post by dummeelke on 2012-10-17
hi
the suggested solution didn't work for sony pcg-n505x
neither did 
cdrom-detect/try-usb=true 
from
[http://ubuntuforums.org/showthread.php?t=1553872](http://ubuntuforums.org/showthread.php?t=1553872)
there's no usb boot option in bios and the proprietary 
sony vaio cdrom drive pcga-cd51 wouldn't be recognized
during the installation.. any suggestions?

---

