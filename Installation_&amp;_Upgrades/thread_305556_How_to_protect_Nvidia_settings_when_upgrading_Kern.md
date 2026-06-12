---
title: "How to protect Nvidia settings when upgrading Kernel"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by Ted_Smith on 2006-11-23
Hi

Every time I upgrade the Linux kernel via the auto update feature, my Nvidia and XServer settings get messed up and I have to mess about re-installing them (I use TSElliots excellent 'envy' script). As it stands, I tend to wait for several weeks or even a few months before I upgrade the kernel due to this hassle. But eventually, I upgrade it to avoid problems and secruity threats. 

I wonder though, surely there must be a way of protecting your system so that when I upgrade the kernel, it doesn't mess my XServer settings up? 

Maybe using the command line is better? (If so, what commands do I use? sudo apt-get upgrade ...what?)

Thanks a lot

Ted

---

### Post by NotJustANewbie on 2006-11-23
In your xorg.conf file (/etc/X11/xorg.conf), you will find a string "nv".

This must be changed to "nvidia" in order to get your driver working.
After a kernel update, just go to terminal (Ctrl + Alt + F2), login and type ```
sudo nano /etc/X11/xorg.conf
```

Scroll using the keyboard and find and edit the "nv" to "nvidia".
Press Ctrl + O (letter O) to save the file... then reboot your machine.

Everything should work fine!
Gd luck 8)

---

### Post by Ted_Smith on 2006-11-23
Thanks - I will try that next time I do a kernel upgrade :-)

---

