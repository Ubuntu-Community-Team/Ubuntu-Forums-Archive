---
title: "mouse configuration"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by mauijohn on 2005-09-24
Will try again with a slightly different question

Third install of ubuntu

Installation does not recognize mouse.

Windows, RH, etc. have no problem

What file do I edit and how to be able to use the mouse.

Logitech trackman

---

### Post by Xian on 2005-09-24
I would check over at the LQ [Hardware Compatibility List](http://www.linuxquestions.org/hcl/showproduct.php?product=2474&sort=8&cat=all&page=1).

---

### Post by mauijohn on 2005-09-24
I'm new to all this 
but
I think the problem is that I'm trying this on an old computer

ubuntu is expecting the mouse on ps2 and it's on tty

any suggestions?

---

### Post by mauijohn on 2005-09-24
Think I found it!

You'll want to change the lines that say something like:

Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"

to use a serial port.

Option "Device" "/dev/ttyS0"
Option "Protocol" "Auto"

---

