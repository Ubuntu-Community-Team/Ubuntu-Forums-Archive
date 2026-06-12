---
title: "Install lubuntu 12.10 with VNC desktop only"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by CootCraig on 2013-02-11
What I'm trying to accomplish is a lubunto 12.10 desktop box that can boot without a monitor and puts the graphical desktop on VNC.
I have a Dell Inspiron 560 that I want to put in my company's data center and use it remotely.

I have a standard xorg install working so a way to replace xorg with a VNC server is fine.  Again, the real problem is I want to boot without a monitor and access the LXDE desktop from remote.

---

### Post by ahallubuntu on 2013-02-11
~

---

### Post by CootCraig on 2013-02-11
> **ahallubuntu said:**
> Have you tried simply installing Ubuntu desktop (or Lubuntu, whatever) and accessing it remotely on your local network?  First, try it with a monitor.  If that works, try without.

I did install the desktop and then was able to ssh x forward using xephyr, but I had some issues.
1) Slower than I liked
2) I could not get the X forwarding to work without the Xorg desktop running.

I really don't want to put a monitor on a remote machine.

---

### Post by ahallubuntu on 2013-02-11
> **CootCraig said:**
> I did install the desktop and then was able to ssh x forward using xephyr, but I had some issues.
1) Slower than I liked
2) I could not get the X forwarding to work without the Xorg desktop running.

I really don't want to put a monitor on a remote machine.

It's true, remote VNC/desktop sharing isn't going to be very fast over a network.  I've gotten used to that, however.  I don't use remote servers for anything display-intensive.  I often set the color depth back to 8 bits - lousy color but faster transfer/display refresh.  I generally use the desktop for easier remote administration via Gui (instead of say Webmin) and for what I do, it has worked well for me.

You might try this: heard good things, never tried it myself.  I assume it will work in Ubuntu:

[https://wiki.archlinux.org/index.php/FreeNX](https://wiki.archlinux.org/index.php/FreeNX)

---

