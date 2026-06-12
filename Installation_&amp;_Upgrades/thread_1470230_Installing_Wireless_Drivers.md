---
title: "Installing Wireless Drivers"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by misterpickle on 2010-05-02
I am new to Linux and actually just finished my install about 30 minutes ago. Ubuntu 10.04 isn't recognizing my wireless adapter, so I need to install the drivers. I know where the drivers are, I just don't know how to install them on a Linux system.

[Here]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4318") is the driver page. I don't know how to download the .inf file (necessary?) but I have ndiswrapper, bcmwl5.sys, and sp33008.exe all in the downloads folder.

Apparently just double clicking the files does nothing, so what do I do now?

---

### Post by Bronto on 2010-05-02
You should have a "*Broadcom B43 wireless driver*" in **System** -> **Administration** -> **Hardware Drivers**. If it's there all you have to do is activate it and reboot.

---

### Post by davidmohammed on 2010-05-02
before you do that - are you installing 10.04?

can you type ```
lspci | grep -i net
``` into a terminal and dump your contents here.

---

### Post by misterpickle on 2010-05-02
Works great! Thanks.

---

