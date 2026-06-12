---
title: "How to Reinstall X Server?"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by moclippa on 2006-05-30
I think my X Server got corrupted... any suggestions on how to reinstall it?

---

### Post by mlind on 2006-05-30
You just probably need working configuration, not the whole Xserver?

backup your /etc/X11/xorg.conf
and do 

```

sudo dpkg-reconfigure xserver-xorg

```

If you use forum's search functionality, you'll find a lot of other threads with
the solution.

If you really need to reinstall whole Xserver, try
sudo apt-get install --reinstall xserver-xorg

---

### Post by moclippa on 2006-05-30
Thanks... yeah it seems to be a glx problem with Nvidia drivers more then an xsererver problem... but I figured it wouldn't hurt to try. :) Thanks for the help

---

### Post by tsairox on 2007-12-29
Hi,

Another very easy way to reinstall the X server is to:

1.Restart the PC with the live ubuntu disk. 
2.Choose safe graphics mode.  
3.Open a terminal
4.cd to /etc/X11
5.cp xorg.conf to /media/usbdrive
6.open gftp
7.upload the xorg.conf file to a server
8.restart PC without the live disk
9. ctrl-alt-f1
10. login
11. cd /etc/X11
12. sudo rm xorg.conf
13. then wget [www.yourserver/xorg.conf](www.yourserver/xorg.conf)
14. startx

You will be able to start X without a hitch because the live cd in safe graphics mode automatically determined your X settings.  This is much easier than the sudo dpkg-reconfigure xserver-xorg method!

Enjoy!

---

