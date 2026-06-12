---
title: "get stuck after upgrading to ubuntu 10.10"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by nguyenxh on 2010-10-26
Hi,

I recently has upgraded from ubuntu 10.04 to 10.10 then it gets stuck at the screen:

Ubuntu 10.10 ubuntu tty1 and asks to login,

I entered my login and password then it shows: welcome to ubuntu!...

account@ubuntu:~$:..

how could I go to the desktop screen?

Thanks in advance!

---

### Post by Mark Phelps on 2010-10-27
Simplest way, since you're already at a command line, would be to enter "startx", or if that doesn't work, "sudo startx".  That should bring up a desktop.  After that, do a normal shutdown and upon reboot, you should go to a desktop.

Had this same thing happen to me this last weekend and this sequence fixed it.

---

