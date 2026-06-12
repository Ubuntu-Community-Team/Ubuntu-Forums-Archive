---
title: "Bootable USB on Gigabyte motherboard"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by Tenorman on 2012-02-13
I'm having difficulty creating a bootable USB drive to run Ubuntu on a new (well, pre-owned) PC.  It has a Gigabyte GA EX 58UD5 motherboard.  There is a strange way to get these motherboards to boot from a USB - you have to ignore the Boot menu and instead go into Advanced BIOS settings and set the hard disk boot preferences there.  Anyway, after getting to this point, the intial boot seems to be working, until it reaches the Ubuntu logo and the five blinking lights under the word.  It never progresses beyond this point.  If I press escape or any F key I get the following errors.

```
(process:407): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
/init: line7: can't open /dev/sr0: No medium found
```

I have no idea what this refers to - anyone able to offer any help?

Cheers
Colin

---

### Post by oldfred on 2012-02-14
I have a different model Gigabyte board and yes it took me a while to learn that all the USB boot choices do not work for USB flash devices, but another hard drive is where it is found.

I also have nVidia and have to add nomodeset on new boots, USB boots, or CD boots to get it to work. After installing the nVidia driver then everything is ok.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

