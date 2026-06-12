---
title: "Excellent old piece of hardware but..."
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by jose3 on 2006-10-13
Hi guys.
I came to this excellent piece of old hardware -Micron Powerdigm- with dual processor etc etc and thought.... This could be my stable server I was looking for!! but...the moment I tryed to boot Dapper FE it was not supperted by the bios neither network boot.

It is worth it to spend time doing investigation on how could I install ubuntu server on that machine? Where should I start? Isn´t dangerous to have a server that cannot be rescued with a live Cd or rescue Cd?

The question is. Stable machine with deprecated technology, where is the scale turning? What do you guys think?.

Thanks very much.

---

### Post by louieb on 2006-10-13
Just wondering. I have a couple of computers That even after changing the BIOS to boot from CD first still won't recognize a syslinux CD as being bootable. I got around this by creating a "Smart boot manager" floppy, booting to it, then have it boot the CD. Have you tried that? 
Just google sbootmgr.dsk dowload and copy it to a floppy. 
```
dd if=sbootmgr.dsk of=/dev/fd0
```
Don't know if the machine is worth using as a server. But it won't take much time to see if this method will allow you to boot from the install CD.

---

### Post by K.Mandla on 2006-10-14
There's also a wiki page for Smart Boot Manager.

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

I think it's worth a try. Even as a learning experience. :)

---

### Post by jose3 on 2006-10-14
It has worked !!! 

Thanks very much for the help guys.

Regards.

Jose

---

