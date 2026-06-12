---
title: "booting from CD but running from external USB drive"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by glennr on 2006-08-19
I have sucessfully installed XUbuntu Dapper onto an external USB disk drive.

If a PC bios does not have the option of booting from USB is it possible to boot from the live/install cd but to run using the USB disk?

I tried pressing F6 and changing the root=/dev/ram to root=/dev/sda1 but that didn't work.

Is this possible to do by giving the correct boot paramaters or do I need to make a custom boot floppy or CD to do this?

If the former then what are the correct parameters?

---

### Post by K.Mandla on 2006-08-20
I think a custom/boot floppy is in order. About a year ago I had an ancient P2 laptop that wouldn't boot from CD properly (reliably), and I managed to get it going from USB with the stuff from [www.BootDisk.com]("http://www.bootdisk.com").

You'll have to do some research to see what works best for you. I know there are a bunch of options for USB access off a boot floppy.

I should mention that I've never done that with Ubuntu, so I make no guarantees. ... ;)

---

### Post by glennr on 2006-08-21
Thanks for the tip, I found a bunch of stuff along the lines that you suggested but this seemed to be the simplest:

[http://ubuntuforums.org/archive/index.php/t-19428.html](http://ubuntuforums.org/archive/index.php/t-19428.html)

---

