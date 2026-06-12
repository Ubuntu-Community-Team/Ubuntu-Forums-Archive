---
title: "Booting to a login screen"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by Leo Simon on 2012-10-13
Hi 

I've just installed 12.04, which is nice but a little too automated for my liking.

I would like to be able to boot to a tty login screen, as I used to be able to do in 8.04.    After logging in, I'd like to be able to login and then manually open my windows manager, as I did with 8.04.    Could somebody explain how I might do this in 12.04?

Following another post, I tried changing the default run level in /etc/init/rc-sysinit.conf to either 1 or 3, rather than the default 2, but neither option gave me an old-fashioned login screen.   

Thanks!

---

### Post by 2F4U on 2012-10-14
You could change the Grub bootloader as outlined here:

[http://askubuntu.com/questions/148717/how-do-i-boot-into-the-console-and-then-launch-the-ubuntu-desktop-from-it](http://askubuntu.com/questions/148717/how-do-i-boot-into-the-console-and-then-launch-the-ubuntu-desktop-from-it)
[http://www.techienote.com/2012/05/how-to-disable-gui-boot-in-ubuntu-12-04.html](http://www.techienote.com/2012/05/how-to-disable-gui-boot-in-ubuntu-12-04.html)

---

### Post by Leo Simon on 2012-10-14
Thanks very much for this, looks like it's sorted out now.

---

