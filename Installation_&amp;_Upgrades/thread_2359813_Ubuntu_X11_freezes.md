---
title: "Ubuntu X11 freezes"
date: 2017-04-28
forum: Installation &amp; Upgrades
---

### Post by mordox on 2017-04-28
I recently upgraded my laptop from 16.10 to 17.04 . After the upgrade my X11 screen freezes after I log in. If I immediately switch to tty1 I'm able work with console commands. I tried looking into dmesg but didn't find anything. How can I troubleshoot this?  FYI, the laptop is having radeon hardware. Its HP dm4 1041tx.

---

### Post by mörgæs on 2017-04-28
As always we should first try to narrow down if the problem is 17.04 itself or the upgrade process, so... 
How does it work in a live boot of 17.04?

---

### Post by ubfan1 on 2017-04-28
Anything in /var/log/Xorg.0.log (or any older copies with ".old" or a higher number)?  Try killing the X server from a terminal, and restarting it, to see what errors are produced on the screen.  If you have an /etc/X11/xorg.conf file, try renaming it, and restart the X server without the file.

---

### Post by mordox on 2017-04-29
I tried running a live cd. It is not able to start the graphical mode. Mouse and keyboard don't work.

---

### Post by mörgæs on 2017-05-01
What are the results from the advice in post 3?

---

### Post by mordox on 2017-05-01
Tried restarting lightdm didn't help. I see a kernel error on tty does that help in anyway?

[ATTACH=CONFIG]274894[/ATTACH]

---

### Post by mörgæs on 2017-05-03
Did you try without xorg.conf (if the file was present)?

---

### Post by mordox on 2017-05-06
There was no xorg.conf file

---

