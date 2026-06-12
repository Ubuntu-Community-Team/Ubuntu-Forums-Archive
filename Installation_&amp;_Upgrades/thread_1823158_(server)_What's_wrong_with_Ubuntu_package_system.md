---
title: "(server) What's wrong with Ubuntu package system?"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by sonnet on 2011-08-11
No meant to be rude, but I honestly would like someone to enlighten me about what happened to me and why it is the way it is.
I downloaded a Ubuntu server image (64bit latest version).
Installed the command line system without any additional server packages.
The I simply ran like in this guide :
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
sudo apt-get update

then 

sudo apt-get upgrade

At last I installed the graphical environment:
sudo apt-get install gdm xorg xfce4 synaptic

Everything went smooth, but the problem is that it pulled out also all the **_whole_** Gnome environment including ubuntu one, unity evolution and so on.
Also i might be wrong but when I entered the command and asked to confirm, I didn't see ubuntu-one packages or metacity or nautilus or many others gnome libraries.
When I rebooted
Now can someone explain why that happened and if it's possible to install only xfce4 environment (starting from a command line system as base) without any additional and unnecessary library?

---

### Post by ajgreeny on 2011-08-11
I see no reason why all of gnome was also pulled in with xfce4, unless something else was also already installed that you are not mentioning.

To get rid of the other things that you don't need, see [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) for a long but effective command to give you pure xfce and nothing else.  I am not sure if it will remove gdm, leaving you needing to start the GUI with "startx" but if you find that is annoying, just add the display manager of your choice (gdm, xdm, kdm, lxdm, etc etc)

---

### Post by sonnet on 2011-08-11
Thanks for the link.
I'm sure I installed the way i wrote it.
I was hugely surprised too.

---

