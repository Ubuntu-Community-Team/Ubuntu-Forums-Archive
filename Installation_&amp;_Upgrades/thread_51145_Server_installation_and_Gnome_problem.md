---
title: "Server installation and Gnome problem"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by sfwasabi on 2005-07-22
I'm trying to replace my Windows 2000 server with a linux server. I'm pretty technically saavy, but new to Linux.

I made a new installation choosing "server" which doesn't install X or Gnome.

I want to have a gui, because I am new to Linux.

So, I want to add a working installation of Gnome Desktop to the server installation.

I'm getting pretty far, but something is eluding me.

Here is where I'm at so far.

After installation,  and after I log in and get a command prompt, I've been doing the following:

1) sudo apt-get install x-window-system-core
2) sudo apt-get install xscreensaver
3) sudo apt-get install gdm
4) sudo apt-get update
5) sudo reboot

After I do this, the server reboots and gives me a GUI login. I put in my login and password, and the desktop begins loading. It loads the Window Manager, then it starts loading Nautilus, and then it stops there. It doesn't freeze. I can still use my mouse. When I click on the splash screen, it disappears. I left it overnight and the next morning the screensaver had kicked in. When I clicked the mouse, it woke up. There just was no desktop icons and no menu bar, just the ubuntu desktop background.

I suspect that there are a couple more packages that I need to install. Can anyone tell me which packages I need to install just to get the Gnome Desktop Manager working?

Is there a list of the default installed packages anywhere? Or a list of the normally installed packages versus the server installed packages?

Thanks!

---

### Post by scoon on 2005-07-22
Hey there, 

You DO NOT need to reboot.  Try: 
sudo /etc/init.d/gdm start

I believe there is a meta package called gnome which will install the "works" for you.  You can find that by:
apt-cache search gnome 

All though, it may be easier for you to just do a Desktop install and then add the server components as needed.  Instead of the other way around. 

regards, 

scoon

---

