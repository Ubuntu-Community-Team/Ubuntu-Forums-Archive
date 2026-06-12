---
title: "Install UBUNTU on usb HD"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by pepposus on 2005-03-22
I installed Ubuntu, and the installation finished without error.
Now rebooting the computer i have this error
pivot_root: No such fileor directory
/sbin/init: 429: cannot open de/console: no such file
What can i do?  :-k 
Thanky you in advance...
Gianni

---

### Post by nutubu on 2005-04-06
If you want to boot from a USB drive, the thread below will give you the solution. Or at least, it will give you some hints to fix your problem. The default initrd.img file is missing some modules to boot your specific system or the delay before booting is not long enough for all necessary modules to load. It is just a matter of finding which one(s) and add these in the file /etc/mkinitrd/modules and/or increasing the DELAY parameter while following the procedure given in this thread.

[http://ubuntuforums.org/showthread.php?t=20522](http://ubuntuforums.org/showthread.php?t=20522)

---

