---
title: "Default OS in Grub"
date: 2004-12-14
forum: Installation &amp; Upgrades
---

### Post by edscripps on 2004-12-14
When I boot the Grub screen comes up and gives me the choice of Ubuntu OS or Windows OS.  Ubunto is currently the default and will start autmatically after a few seconds.  Can I change the Grub so that Windows is the default OS and would start automatically?

Thanks,
-Ed

---

### Post by gdeswardt on 2004-12-14
Yes you can by executing the following command in the terminal window

```
 sudo gedit /boot/grub/menu.lst
```

This will open config file for the grub loader. There should be a parameter called *default* with some instructions of how to set it. 

Hope this helps

---

### Post by Rancoras on 2004-12-14
Look in /boot/grub/menu.lst and see if there's an option in there to set the default.  I don't have an Ubuntu machine at my disposal right this second.  If there are no further replies, I'll check when I get to one and post back.

---

### Post by edscripps on 2004-12-14
Editing the menu.lst did the trick.  

Thanks for the help.

--Ed

---

