---
title: "XSane failed to open"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by dennisofnewport on 2012-04-26
Xsane

can any one help me change the argument in xsane

when I run xsane i get the following message

failed to open device brothers3:bus3;dev1' invalid argument

when I run lsusb I see brothers listed as bus1 device 2

can I change this agrument in xsane????

thanks

---

### Post by col48 on 2012-04-26
Does this help?

[HTML]
http://askubuntu.com/questions/32646/how-to-change-the-bus-dev-in-order-to-allow-xsane-to-work[/HTML]

I imagine that if you
```
cd /dev/bus/usb/001
``` you see an entry 002 which you can identify with the scanner (my equivalent has the owner lp - line printer - and it is an MFP)

The chmod suggested adds write access for you to the entry.  I don't understand why this might change the device bus address but perhaps you do!  If the error was 'access denied' then this solution would be more reasonable to me, pedant that I am!

This is on the same lines and a bit more readable:
[HTML]http://www.scribd.com/doc/44744453/XSANE-permissions
[/HTML]
Alternatively...
[HTML]http://ubuntuforums.org/showthread.php?t=1285100
[/HTML]gives an explanation of why your situation might have happened and perhaps a different way through.

Hope you find a solution.

---

### Post by dennisofnewport on 2012-05-01
thanks for the info I tried them and still a little confused. I want to change xsane to reckon the correct bus an dev. How do I get into xsane.

---

### Post by dennisofnewport on 2012-05-01
thanks I still do not know how to mark this thread a solved but it is.

---

