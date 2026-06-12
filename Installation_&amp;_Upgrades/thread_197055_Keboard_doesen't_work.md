---
title: "Keboard doesen't work"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Eagleorn on 2006-06-15
**Hi everybody!**

I'm pretty new to this Linux stuff, and I have some problems installing Ubuntu 6.06.

I have an Intel Pentium D processor, and therefore I downloaded the AMD64 desktop image (that would work, right?)

The CD boots nicely and I choose "start and install". The liveCD starts up and everything seems to be ok, but my keyboard does not work. I have a Logitech keyboard connected via ps/2. It works perfectly well in Windows, and I had no problem in Ubuntu 5.10 either. My mouse, Logitech MX1000 (wireless), connected via usb, works fine though.

I also downloaded the alternate image and tried to install in text mode, but my keyboard dosen't work there either. I have run the "check cd for defects option", but it dosen't display any errors

Any idea what is wrong?

---

### Post by BitTorrentBuddha on 2006-06-15
EDIT: I was completely wrong, please ignore anything you read before I edited this.

---

### Post by Eagleorn on 2006-06-15
After trying several times with different keyboards and boot options, I finally came up with a solution, a pretty easy one.

When i took a closer look at all messages printed by the kernel while booting up the installation system I found this:

**i8042.c: Can't read CTR while initializing i8042**

This thread suggests to boot with i8042.noacpi
[http://www.ussg.iu.edu/hypermail/linux/kernel/0409.2/0901.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0409.2/0901.html)

But i found it easier to just disable USB mouse and USB keyboard support in BIOS, that solved my problem! 
USB mouse support tries to emulate a ps/2 mouse, wich dosen't work very well in this case.

If you master any of yhe scandinavian languages (e.g sweish, danish or Norwegian) you may benefit from this article at [goolge groups]("http://groups.google.se/group/dk.edb.system.unix/browse_thread/thread/8edfc77a929b70aa/8534f8d8decd88b8?lnk=st&q=can't+read+ctr+while+initializing&rnum=1&hl=sv#8534f8d8decd88b8")

---

