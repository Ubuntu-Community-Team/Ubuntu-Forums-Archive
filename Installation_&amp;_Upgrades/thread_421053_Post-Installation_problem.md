---
title: "Post-Installation problem"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Biotech80 on 2007-04-24
Hi guys,
3 days ago i decided to install Linux for the first time. I've always used Windows before. 
I downloaded the AMD64 version of Ubuntu (My pc has an AMD64 3500+, ATI X700Pro) and successfully installed it. 
The problem is that if i select Ubuntu at start (Grub selection), after a few seconds of loading the screen turns off... it enters stand-by i mean. And i cannot do anything, like enter the terminal. 
In contrast, if i start the O.S. in "Recovery Mode" and i type "exit" in the terminal after the booting, the system loads correctly and the monitor doesn't enter stand-by mode.
Any suggestion is well accepted :)

---

### Post by dcstar on 2007-04-24
> **Biotech80 said:**
> Hi guys,
3 days ago i decided to install Linux for the first time. I've always used Windows before. 
I downloaded the AMD64 version of Ubuntu (My pc has an AMD64 3500+, ATI X700Pro) and successfully installed it. 
The problem is that if i select Ubuntu at start (Grub selection), after a few seconds of loading the screen turns off... it enters stand-by i mean. And i cannot do anything, like enter the terminal. 
In contrast, if i start the O.S. in "Recovery Mode" and i type "exit" in the terminal after the booting, the system loads correctly and the monitor doesn't enter stand-by mode.
Any suggestion is well accepted :)

CTRL-ALT-F1 when the screen shuts down should bring up a text screen that you can log into.

It could be a driver and/or xorg.conf problem, log in and do:
```

sudo dpkg-reconfigure xserver.xorg

```
And select the "VESA" driver and the defaults offered, after you have finished (assuming you are using Gnome) do:

```
sudo /etc/init.d/gdm restart
```

Should get you a basic system running.

---

### Post by Biotech80 on 2007-04-25
> **dcstar said:**
> CTRL-ALT-F1 when the screen shuts down should bring up a text screen that you can log into.


The problem is that the monitor turns off. I don't know if pressing CTRL-ALT-F1 brings up a text screen because i can't see it! :confused: 

Tnx for the reply.

---

