---
title: "mkfs.vfat : No such file or directory"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by aberkov on 2008-08-20
Hullo.

I'm trying to create a USB-boot Ubuntu. I've been following the procedure outlined here: [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

However, when I hit the *$ sudo mkfs.vfat -F 16 -n liveusb /dev/sdb1* I've hit the wall, as the system responds:
[B]
mkfs.vfat 2.11 (12 Mar 2005)
n: no such file or directory[/B]

What am I doing wrong / what do I do now?

Thanks in advance for advice!

Guess I should add: I'm trying to do this from a machine with a fresh 8.04 install, no addons, extra software etc.

---

### Post by prshah on 2008-08-20
> **aberkov said:**
> 
n: no such file or directory
What am I doing wrong 

I think you've dropped the hyphen ("-") from the "..-n liveusb.." part of the command. The command you've put here (probably pasted) is correct, but in the Terminal when you're putting (probably typing) the command, you may have inadvertently left out the hyphen "-" before the "n".

---

### Post by aberkov on 2008-08-20
Of course I'm using this forum as a replacement for command syntax proofreading... *shame*

Thanks!

---

### Post by prshah on 2008-08-20
OK! Please mark the thread solved; click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

