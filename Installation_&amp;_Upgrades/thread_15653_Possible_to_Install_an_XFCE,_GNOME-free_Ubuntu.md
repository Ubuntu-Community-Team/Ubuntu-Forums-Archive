---
title: "Possible to Install an XFCE, GNOME-free Ubuntu?"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by spaceballl on 2005-02-15
Hi all,

i'm fairly new to the world of linux, but I am learning quickly. I love Ubuntu. I installed and decided I wanted to move to the more lightweight XFCE. However, on my older 450 mhz P3, once i figured out all of the dependency issues, installed a bunch of stuff w/ synaptic, etc etc, I'm finding XFCE to not really be that much faster than GNOME, which is very contrary to my XFCE only install with Fedora a few months ago. Is it possible to just do an XFCE installo w/ Ubuntu? Maybe using repositories with a custom install? Obviously only GNOME is included on the CD...
-kevin

---

### Post by Xian on 2005-02-15
[QUOTE=spaceballl]Is it possible to just do an XFCE installo w/ Ubuntu?[/QUOTE]
If you want an xfce only environment I would suggest looking at [Xfld Linux](http://www.xfld.org/Xfld/en/xfld.html).
According to their forums the HD installer works nicely.

---

### Post by az on 2005-02-15
"I'm finding XFCE to not really be that much faster than GNOME, which is very contrary to my XFCE only install with Fedora a few months ago. Is it possible to just do an XFCE installo w/ Ubuntu?"

Everything is slow on Fedora, so I do not know why XFCE seemed faster for you there.  No, XFCE will not run faster if you do not have gnome installed.  I could never see why people said that XFCE was so much faster than gnome.  Things like windows and text render slower when they are antialiased (which is why Gtk 1.2 is faster than GTK2) and XFCE uses the same font rendering libraries as Gnome.  Slower older computers take an even bigger hit.

If you want to try it anyway, you can install Ubuntu with the custom option (at the cdrom's boot prompt)
After the base system is installed, type
sudo apt-get install x-window-system-core xfce xfce4 xterm mozilla-firefox menu

Other package you may want:
abiword gdm xmms mc 

Icewm is much faster than xfce.

---

### Post by Pluk on 2005-02-15
do a custom install, that way you get a minimal install.

Afterwards you can install things like xserver and xfce4.

For xfce4.2 you can add this to your /etc/apt/sources.list :

deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

then install: apt-get install -t testing xfld-desktop

---

### Post by spaceballl on 2005-02-16
Yeah the only thing with that... is that I had to install a lot of random stuff last time that didn't come with the ubuntu CD... I feel like doing apt-get is going to give me a lot of dependency errors and end up w/ a minimum install that is broken...

---

