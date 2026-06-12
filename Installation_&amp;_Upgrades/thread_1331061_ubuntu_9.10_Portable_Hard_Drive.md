---
title: "ubuntu 9.10 Portable Hard Drive"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by Venku7337 on 2009-11-18
I am wondering if i could install ubuntu 9.10 onto a portable hard drive. i was also wondering if i could have it set up so that i could boot from it on other computers and then install it like a LiveCD, however i would want to be able to use it like a normal ubuntu installation. Is this possible, if so how. 
I was thinking that if i just install it onto my Portable hard drive then i could get other computers to boot from it, however because i am unsure of this, before i precede i was wondering if i am correct. 

Thanks.

---

### Post by tommcd on 2009-11-19
You should be able to install Ubuntu to the external drive and then connect it to different computers to use it. Just set the computers to boot from the usb drive (where the external drive will be plugged into) as the first boot device.
The only problem you may run into is that you may need to configure different hardware on the different computers. For example, if one computer has nvidia graphics and another computer has ati and you want 3D graphics. For the most part Ubuntu should just boot right up.

You won't be able to use the installed Ubuntu on the external drive to install Ubuntu to other computers though.
You could use a Clonezilla live CD to try to clone the Ubuntu install on the external hard drive onto a different computer:
[http://clonezilla.org/](http://clonezilla.org/)

---

