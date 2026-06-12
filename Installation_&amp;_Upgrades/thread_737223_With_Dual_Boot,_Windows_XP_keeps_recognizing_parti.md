---
title: "With Dual Boot, Windows XP keeps recognizing partition as new hardware?"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by milasihsok on 2008-03-27
Hi Everyone,

I decided to try out Ubunu 7.10 but keep Windows XP.  Ubuntu works great and I'm happy with it, but everytime I boot up XP, it seems to recognize the new Ubuntu Partition as a hard drive.  It proceeds to bring messages saying it has recognized new hardware, and eventually a message that Windows must be restarted in order to the "new" hardware.  

Sorry if this has alread been posted somewhere, but I am really new to this forum.  Any help would be appreciated.

---

### Post by protito on 2008-03-27
it happens becouse u resized the windows partition.. xp doent cares about ext2/3.. it should happens just once though

---

### Post by ajgreeny on 2008-03-27
Usually after resizing the XP partition and installing Ubuntu, there will be an automatic scandisk when you next boot XP, but it will not "find new hardware".  I can not imagine why this is happening to you unless you added some new hardware for your ubuntu install.  If so, do what XP tells you and install it in windows as well.  All should then be OK.

---

