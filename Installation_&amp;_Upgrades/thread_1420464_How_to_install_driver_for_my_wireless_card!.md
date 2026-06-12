---
title: "How to install driver for my wireless card!"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by lobebufe on 2010-03-03
I got the native driver for linux already but just don't how to do it. It is an external wireless usb card, it's from Ralink. thnkx

---

### Post by pingu1 on 2010-03-03
This is a good site to start with, to check if everything works:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

I once thought I had big problems with my wired network - ended up using _one_ command in the terminal (think it was "sudo eth0 up")..

---

### Post by pingu1 on 2010-03-03
You can type > lspci in the terminal to find out which wlan-card you've got...
and then search the forum ...

---

### Post by lobebufe on 2010-03-05
I don't get it, the thing is i got the wireless driver here with me. But i just don't know how to install it. [ATTACH]149077[/ATTACH]

i attached the driver, so it will be easier for you to help me. Thank you so much.

---

### Post by raymondh on 2010-03-05
tar.bz or tar.gz are compressed files that you have to decompress, then build/compile, then install.

here is the official documentation

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

here is a sample google page about 'installing a tar.bz file' (see post 3)

[http://www.linuxquestions.org/questions/linux-newbie-8/how-to-install-bz2-files-491508/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-install-bz2-files-491508/)

and from our own forum (see post 7 and 8 ... you will notice similarities with above post 3)

[http://ubuntuforums.org/showthread.php?t=292982](http://ubuntuforums.org/showthread.php?t=292982)


Raymond

---

