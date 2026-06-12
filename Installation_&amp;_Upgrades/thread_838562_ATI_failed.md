---
title: "ATI failed"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by melenor on 2008-06-23
I recently for no real aparent reason went and installed the newest ATI driver, 8.6, and after it was installed it worked perfectly expect that when ever i tried to watch a video it crashed my computer, i tried to uninstall it every way and when i used Synaptic it said this.

E: xorg-driver-fglrx: subprocess post-removal script returned error exit status 2

Then when i click on details it says this (look at screen shot)

all i want to do is reinstall the ATI driver that is in ubuntu's repository. Thanks for your help.

*couldn't think of a better title any suggestions and will change it.*

---

### Post by pytheas22 on 2008-06-23
You could try using envy:
```

sudo apt-get install envyng-gtk
```

and run it with "sudo envyng-gtk"

It will get the best video driver for you and configure other parts of the system as necessary.  I think the the drivers it pulls aren't actually from Ubuntu's repository--they're from the server of the guy in Italy who wrote envy--but if you don't have a problem with that, then I'd recommend giving envy a try.

---

### Post by melenor on 2008-06-23
but the thing is that i need to uninstall the fglrx i have now, and install the ones that i had before, but i will try it and post back.

---

