---
title: "Boots to Black Screen after updating grub and booting to text mode"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by rufus muturi on 2013-05-16
Hello, guys.
I booted into text mode from instructions on this page, [http://goo.gl/ZT9oa](http://goo.gl/ZT9oa). It worked fine but now I can't boot back into the graphical mode.

I also recently removed the 3D packages for Ubuntu 12.04 because of an unmet dependency. I was able to use it in 2D mode for a while. I installed compiz-config-settings-manager and updated the intel video drivers and the grub. Once I restarted my computer, I could view the purple splash screen, then....nothing, just a black screen and I could not boot into the desktop. 

So, here's what I did: removed 3D packages (worked fine up to this point), then updated intel graphics and video drivers and installed ccsm, updated grub, rebooted into text mode. Yeah, quite a bit of work.

I need help in getting back to my GUI login and desktop urgently. Please help me out. :(

---

### Post by d0006 on 2013-05-16
What happens if you enter
```
startx
``` from the command line?

You can install KDE and see what happens. Do a web search for install KDE and you will find instructions.

---

