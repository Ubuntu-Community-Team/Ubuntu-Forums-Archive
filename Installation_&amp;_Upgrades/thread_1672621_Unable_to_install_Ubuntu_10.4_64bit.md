---
title: "Unable to install Ubuntu 10.4 64bit"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by KILLERB4DGER on 2011-01-21
I'm trying to install 64bit Ubuntu 10.4, got the Ubuntu loading screen then faced with this message.
Also tried installing 10.10, again same message.


BusyBox v1.13.3v (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system


Tried booting from USB from various ports, same message. I can't even install Ubuntu using wubi. Wondering if its a hardware issue?

I have:
* Intel Core i7 930 2.8GHz
* Asus P6X58D-E X58 Motherboard
* Sapphire HD 5970 2GB GDDRS Dual DVI
* Corsair 6GB XMS3 Dominator Memory
* Samsung SH-B083L 8xBD-ROM


Cheers

---

### Post by sikander3786 on 2011-01-21
Welcome to the forums :-)

First of all, check your downloaded image for any possible defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums match, try using unetbootin to burn the USB.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

If the errors persist, you probably need to put in some boot parameters from F6 menu. There are 6 of them and you might need to try all of them, one by one.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

Keep us posted ;-)

---

### Post by KILLERB4DGER on 2011-01-25
Sry its taking so long to reply.

I have tried all three of your options, none have worked. Your last option, I don't get those screens shown in the screenshots to press F6.

Booting from unetbootin gives me the menu to install, then the screen is completely blank.

As for my downloaded iso, I checked for defects and found none.

Kinda sucks, but thanks for your reply :)

---

### Post by BACbOK on 2011-01-25
[Use the Ubuntu 10.04.1 alternate.]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt")

---

### Post by KILLERB4DGER on 2011-01-25
Have tried that before I started this thread, no luck  :(

---

### Post by sikander3786 on 2011-01-25
> Your last option, I don't get those screens shown in the screenshots to press F6.

As soon as the computer starts booting from the disc, keep on pressing any key and you'll see that menu.

---

