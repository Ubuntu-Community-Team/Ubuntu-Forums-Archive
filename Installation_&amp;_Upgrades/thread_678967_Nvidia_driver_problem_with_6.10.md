---
title: "Nvidia driver problem with 6.10"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by omgapolarbear on 2008-01-26
Not sure if this is the right forum but here goes. I've been installing ubuntu 6.10 and every time i try and install the nvidia drivers when I restart it goes to a black screen when its  login time. Whats up with it? did I do something wrong?

My laptop is a HP dv6000 btw

---

### Post by cotcot on 2008-01-26
Could try to give vga=771 as boot parameter in menu.lst

example 
> kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda5 [COLOR="Red"]vga=771[/COLOR] ro single

---

