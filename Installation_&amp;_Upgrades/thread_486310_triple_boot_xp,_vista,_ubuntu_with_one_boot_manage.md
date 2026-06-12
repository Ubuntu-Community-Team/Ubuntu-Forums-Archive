---
title: "triple boot xp, vista, ubuntu with one boot manager"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by suqmaster on 2007-06-27
hmm hello, im new to linux and these forums so I don't really know what to put. I installed xp first, vista second, then today I installed ubuntu. When my system boots up again, it uses the GRUB boot manager interface, which goes by really quickly and defaults to ubuntu. If I want to choose my xp, I have to choose the vista booter under GRUB and then choose to boot xp under the vista boot manager.
  So, is there anyway to disable grub and put it under the Vista boot manager?

---

### Post by Gremlinzzz on 2007-06-27
you can change the start time of grub.    gksudo gedit /boot/grub/menu.lst

---

### Post by Gremlinzzz on 2007-06-27
go to
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
and change the 10 to the time you need and save

---

### Post by suqmaster on 2007-06-27
thx for the replies, but I was mainly wondering if theres anyway to get only one boot manager all together, meaning either GRUB boots all 3 OS's or the windows boot manager boots all 3. That way, I can set a default OS (which I want to be xp) so that I don't need to keep restarting ubuntu (currently default).

---

### Post by louieb on 2007-06-28
The short answer is **yes**. Lots of threads here on modify the GRUB config file to add XP and make it the default OS.   Even a few on using XP's ntldr program. 
MY favorite Dual boot how to site is  the [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")
If you want some help with you particular setup, post back with a copy of your /boot/grub/menu.lst and a list of your partition table using **sudo fdisk -l. **(There are lots of threads that tell you how to post that information too).

---

