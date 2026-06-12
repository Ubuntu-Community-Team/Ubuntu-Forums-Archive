---
title: "Cannot boot from LiveCD or WUBI - Blinking Cursor"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by Jetfirehack on 2012-07-31
I am trying to do a fresh installation of Ubuntu 12.04 on my laptop.

However, following a screen like this as I boot from LiveCD:
[IMG]http://pricklytech.files.wordpress.com/2010/07/ubuntu-boot-01.png[/IMG]

I get a blinking cursor on my screen. Like this:
[IMG]http://3.bp.blogspot.com/_GY7CglwXFAQ/SBeCFMkVWWI/AAAAAAAAA8Q/jbSxIZ-aBLI/s400/BlinkingCursor.jpg[/IMG]

I've tried booting from WUBI as well, and that also won't boot properly. The CD is working, as it does run on my desktop.

My laptop specs:
[http://www.msi.com/product/nb/GT780DX-GT780DXR-.html#/?div=Specification](http://www.msi.com/product/nb/GT780DX-GT780DXR-.html#/?div=Specification)
(Scroll down to specifications)

If anyone could help, that'd be great. Thanks.

*I've also tried bootrec, which produces an error on fixboot. (Something to do with the file system)

---

### Post by Ubun2to on 2012-08-01
Can you burn a new CD and boot from that?

---

### Post by Jetfirehack on 2012-08-01
> **Ubun2to said:**
> Can you burn a new CD and boot from that?

Hi. The CD isn't broken. And I did recently burn it.

---

### Post by Shark711 on 2013-05-31
You need to blacklist the Nouveau Driver:
[http://robertmassaioli.wordpress.com/2012/04/28/installing-ubuntu-linux-on-the-msi-gt780dx/](http://robertmassaioli.wordpress.com/2012/04/28/installing-ubuntu-linux-on-the-msi-gt780dx/)

---

