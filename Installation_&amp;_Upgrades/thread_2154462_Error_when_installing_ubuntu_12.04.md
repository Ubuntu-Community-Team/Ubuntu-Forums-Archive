---
title: "Error when installing ubuntu 12.04"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by hondaprelude on 2013-06-14
I am trying to install Ubuntu 12.04 but every time I try to install it I get an error the error says.  Error informing the kernel about modifications to partition /dev/sda1 - device or resource busy. This means Linux won't know about any changes you made to /dev/sda1 until you reboot- so you shouldn't mount it or use it in anyway before rebooting. The pop up window has an ignore button and cancel button but I cant get out of the window I have to restart the computer. Has anyone seen this issue before?

---

### Post by byStanderone on 2013-06-15
...haven't encountered this issue, tho am wondering...what architecture of 12.04 you are installing, 32 or 64?

---

### Post by Mark Phelps on 2013-06-15
Are you trying to install to a PC that has Windows installed -- and is hibernated?  In that case, it would most likely be using sda1 and won't let you access it.

Otherwise, do you have some other OS running using sda1 that is hibernated or in sleep state?

Or, is sda1 a partition that was in use and you simply powered down without gracefully shutting down?

---

