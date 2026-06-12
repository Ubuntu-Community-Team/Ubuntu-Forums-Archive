---
title: "Blackscreen Blues"
date: 2006-03-25
forum: Installation &amp; Upgrades
---

### Post by Titus A Duxass on 2006-03-25
Hi,
I have done a server install and then tried the following:

Howto Ubuntulite install 
How installation for Low memory systems
How to or xcfe

Always return to the same probem, a black on boot up.

sudo apt-get install gdm x-window-system-core xterm icewm menu mozilla-firefox abiword synaptic

gives me the same problem.

Installation is based on 5.10, hardware is not unusual with a 1.5GHz proc and a Nvidia 4 based graphics card.

Anyone any idea what I am missing?

---

### Post by tseliot on 2006-03-25
Try this (just to be sure):
sudo apt-get install xserver-xorg


Try this:
sudo nano /etc/X11/xorg.conf

And set the driver from "nv" to "vesa" in the Section "Device".

CTRL+O to save
CTRL+X to exit

Then type:
sudo /etc/init.d/gdm restart

---

### Post by Titus A Duxass on 2006-03-25
Thanks, but no joy.
I even tried apt-getting the ubuntu-desktop to make sure that everything was covered.  No luck still a black screen.

Looks like a reinstall (server-expert) is called for and start again.

---

### Post by Titus A Duxass on 2006-03-29
No matter how many times I try it I cannot get this to work.

I can do it in Debian and the only difference is one package, in debian you install x-window-system in ubuntu you install x-window-system-core.

In ubuntu trying to install x-window-system gives error messages.

I have tried the HowTo for minimum, xubuntulite.

Can anyone give me any pointers as to where my problem is?

---

