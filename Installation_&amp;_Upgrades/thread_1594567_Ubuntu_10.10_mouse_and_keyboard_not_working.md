---
title: "Ubuntu 10.10 mouse and keyboard not working"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Mortesins93 on 2010-10-12
Hello,
so I tried installing Ubuntu 10.10 on my laptop hoping it would be great. I installed it without problems expect for the fact that I had a pretty hard time writing in my info as the horizontal bar on the blank space where I had to write my name, the name of the computer, etc. kept on blinking without letting me write. After rebooting, the login window came up and I could not move neither mouse (one is a wireless Trust mouse and the other is the pad on the laptop). So I tried Crtl-Alt-F1 but the keyboards, the wireless one and the one on the laptop, did not respond. After a hard shutdown, I tried it again and I managed to login but after that I got the same problems as before. What should I do? Everything works great on my Xubuntu 9.10 on the other partion. 
I hope you can tell me why because it seems like Xubuntu 9.10 is the only version of Ubuntu that works because I had the same problems with the 10.04.
Thanks in advance.

---

### Post by Charlotte18 on 2010-10-13
I had the same problem and found a solution. I posted it here:

[http://ubuntuforums.org/showthread.php?p=9967856](http://ubuntuforums.org/showthread.php?p=9967856)

---

### Post by Mortesins93 on 2010-10-24
I tried looking at your thread but I could not find the xorg.conf file. I don't think that is the problem anyways because the laptop's keyboard should always work.

---

### Post by Mortesins93 on 2010-11-04
So I got tired of this and I installed Ubuntu 9.10. Now the laptop's keyboard and touchpad work but my wireless keyboard doesn't. What should I do?

---

### Post by Mortesins93 on 2010-12-03
Where can I find drivers for my keyboard? Why does the keyboard only work on Xubuntu 9.10? Where can I find what modules I have installed by default and see if I can install the same on Ubuntu 10.10?

---

### Post by Mortesins93 on 2011-01-15
Well, using the command ```
lsmod
``` I found out that the driver is: ```
usbhid
```For now everything is working fine.

---

