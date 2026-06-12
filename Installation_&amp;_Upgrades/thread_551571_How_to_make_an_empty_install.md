---
title: "How to make an empty install?"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by Nistenf on 2007-09-15
Hi
I wanna make an empty install of Ubuntu. I mean no xorg, no DE, just a command line interface. And I wanna install only what I want for myself (included xorg). Is this possible? If so, what do I have to download? The server edition? And could you tell me, some basic things to do, like for example, how to install xorg and so on?

Thanks in advance!

---

### Post by mocoloco on 2007-09-15
Get the alternate CD, and you can do a command-line only install.
If you're planning to install a window manager, like IceWM, FluxBox, etc then xorg will be installed with it since the WM would be dependent on it.  So apt-get install fluxbox would get all the xorg stuff too.

---

### Post by Pumalite on 2007-09-15
Install Server Edition, CLI only, you don't need xorg. Later is you change your mind and you want a GUI: sudo apt-get install ubuntu-desktop.

OTOH, you might want to go for the minimal install and build from there.
[http://ubuntuforums.org/showthread.php?t=9670](http://ubuntuforums.org/showthread.php?t=9670)

---

### Post by Toet on 2007-09-15
I had the same wish, and ended up using debian netinstall.

Works the same with apt-get to install packages.

I did a netinstall without any extra software install options. Works great. It takes a while to find out what packages need to be installed, but not very difficult if you're used to Ubuntu.

So after installation I get a command line. As I use XFCE now I did the next:

apt-get install xorg xfce4 gdm synaptic firefox

And then reboot, and you get in your bare xorg. Works superbly. I know everything about my system now as I installed all packages myself. So if I get an error, I know exactly what has caused it.

Good luck.

---

### Post by RedSquirrel on 2007-09-15
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Nistenf on 2007-09-16
Thanks for your answers!
I'm trying different thing in a VW, and everything works good.

---

### Post by Pumalite on 2007-09-16
Glad it worked.

---

