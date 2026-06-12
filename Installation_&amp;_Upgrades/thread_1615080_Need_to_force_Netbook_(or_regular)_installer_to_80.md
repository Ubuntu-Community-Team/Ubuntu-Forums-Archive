---
title: "Need to force Netbook (or regular) installer to 800x600"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by gm80 on 2010-11-06
Hi all,
 
I've built a custom net-top with a touchscreen display and I'd like to run either the Netbook Remix or regular Ubuntu as the OS ... but there's a problem:
 
The LCD panel I'm using inaccurately reports to the OS that it can handle 1024x768. In reality, all it can handle is 800x600. It can only handle 1024x768 at a very low refresh rate.
 
That means the Ubuntu install routine goes to 1024x768 by default, gives an out of range error on the display, and I can't see anything to proceed. Are there any commands I can issue during install to force a lower resolution? Any other ideas?
 
Thanks in advance.

---

### Post by sikander3786 on 2010-11-06
Try adding the **nomodeset** boot parameter. See here for details.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

