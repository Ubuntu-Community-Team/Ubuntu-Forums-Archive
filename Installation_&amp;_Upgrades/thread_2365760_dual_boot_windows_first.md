---
title: "dual boot windows first"
date: 2017-07-10
forum: Installation &amp; Upgrades
---

### Post by philoneo on 2017-07-10
hello,
installed a dual boot Ubuntu 16.04 and Windows 7. Everything works fine but I would like to Windows 7 to start by default first. I was looking at /boot/grub/grub.cfg to find how to boot Windows 7 by default, but faced by the number of parameters I do not know what to do.

How to boot Windows 7 by default?

Regards
philippe

---

### Post by yancek on 2017-07-10
Boot Ubuntu and open a terminal.  If you are using gedit as a text editor enter in the terminal:  sudo gedit /etc/default/grub

If you use something other than gedit, insert that in place of gedit in the above command.  This should open that file and the top line is:

> GRUB_DEFAULT=0

You would need to count the menu line on boot to see what number to put there.  If your windows is the 3rd menuentry, you put a 2 on that line, count begins with zero.  When finished, save the file and run:  sudo update-grub.

---

### Post by philoneo on 2017-07-10
thanks <br><br>post/thread solved

---

