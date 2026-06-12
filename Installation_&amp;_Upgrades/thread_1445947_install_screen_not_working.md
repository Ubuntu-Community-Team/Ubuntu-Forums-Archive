---
title: "install screen not working"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by lovo on 2010-04-03
Hi,
 I was about to install kubuntu 9.10 32bit as usual with my memory stick (rendered bootable with USBCreator) when I got the following screen:

[[IMG]http://img693.imageshack.us/img693/3807/p1010764.th.jpg[/IMG]](http://img693.imageshack.us/i/p1010764.jpg/)

When I press 'Enter' nothing is happening, it seems to relaunch the same screen.

in console mode, I can type "live-install" and I have the answer "could not find kernel image /casper/vmlinuz"

What should I do ? I tried different distributions (xubuntu, kubuntu) different usb stick (which were originally working)

lovo

---

### Post by ibuclaw on 2010-04-03
Try Unetbootin instead to make the pendrive bootable. It is yet to fail me. :)

---

### Post by C.S.Cameron on 2010-04-03
Check the MD5SUM of the iso image you are using to make the memory stick bootable.
I have had similar experiences due to a bad iso.

---

### Post by lovo on 2010-04-03
> **ibuclaw said:**
> Try Unetbootin instead to make the pendrive bootable. It is yet to fail me. :)

I tried with Unetbootin, I choose on the first screen ".. manufacturer.." and I then have several line in console, it changes the resolution and then that screen ...:

[[IMG]http://img38.imageshack.us/img38/3497/p1010765c.th.jpg[/IMG]](http://img38.imageshack.us/i/p1010765c.jpg/)

linux is complicated.


> **C.S.Cameron said:**
> Check the MD5SUM of the iso image you are using to make the memory stick bootable.
I have had similar experiences due to a bad iso.
I don't see what you mean. I know how to get the md5 of the downloaded file, but how does it make the usb bootable .. ?


thanks anyway to try to help me!

---

### Post by C.S.Cameron on 2010-04-03
If you are getting those opening screens your flash drive is bootable.
However the boot is not being completed thus the data on your flash drive is not complete or may be corrupt.
This could be due to a bad download of the iso.
I would guess this is the case if your iso is not working with either usb-creator or UNebootin.

---

### Post by lovo on 2010-04-03
Indeed, the file was corrupted. Thank you

---

