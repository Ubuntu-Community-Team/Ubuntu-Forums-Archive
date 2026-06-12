---
title: "Which network management software?"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by spdiscus on 2005-10-15
Howdy. I recently installed Xubuntu (Breezy server install + apt-get install xubuntu-desktop).

I was able to manually configure my home wireless connection, but I'd like to have a GUI manager, like the one used in Gnome, so I can see all available wireless networks when I'm at the library or a coffee shop.

What can/should I install to have quick network management in XFCE?

In Ubuntu, I think you can get to it through System > Administration > Networking.
It may already be installed, and just not in the menu, like Synaptic.

---

### Post by joelito on 2005-10-15
guess that you can try to install the manager from gnome

---

### Post by spdiscus on 2005-10-15
I grabbed it in Synaptic, and it grabs about 30 other packages. None of them were huge, so I don't think it would be too bad, but I was wondering if there was a lighter option.

---

### Post by eric71 on 2005-10-21
A while back I had tried to make a completely Gnome-less Xfce based system.  I used WDM as the desktop manager but I really missed the gnome-system-tools.  The solution turned out to be Webmin, which is available in the repositories. I'm not sure if networking was part of the basic Ubuntu packages, or a module I had to install separately from their website, but it did the job nicely. ( it's listed as a "standard module" at the website, so I think it's included) I think I needed to make a root password to do it right, or maybe just open FIrefox with sudo, I don't really remember.  It was nice having an distribution/desktop idependent control center type thing for use with Xfce.

[http://www.webmin.com/index.html](http://www.webmin.com/index.html)

---

### Post by WOteB on 2005-10-21
You're working on the server? In the Linux world, its not usual to work -on- a server ;) That's usual in the MS Windows world.... ;) 

Why don't work with Webmin. You can install it on the server and can work remotly from a workstation very, very easy, comfertable and safe. Take a look at [www.webmin.com](www.webmin.com)

I have a server with Debian 3.1 Sarge stable, but can perfecty administor from my Kubuntu laptop on the server. It is possible to choose an IP-address wich only can administor the server on the LAN.

With Webmin you can remove the monitor and the keyboard from the server. It's also possible to reboot or shutdown the server, if necessary, remotely.

Putty (installed in the client) does the same thing, but via a terminal and command shell. You log in with a user account and the switch with 'su' to the root account, if necessary.

MC (Midnight Commander, installed on the server) is also a very powefull tool. When using Putty, you can run MC in a small window on your desktop and have full controll on the server.

In short:

Webmin, to administor the server via the browser and ssh.

Puty, to administor the server via a terminal client.

MC, to administor the server remotely via Putty in a small window on the desktop.

In this situation, you can move the server in a corner of the house or office, and work from the desktop comfortably and safe. I never work on the server onself, but always in this way, remotely.

Try it..... :D

---

### Post by joedekangeroe on 2005-11-13
[I]"guess that you can try to install the manager from gnome"
[/I]

What package do I need to install this. I looked for 'network-admin' in synaptic but I did not find anything like that.

---

### Post by eric71 on 2005-11-13
[QUOTE=joedekangeroe][I]"guess that you can try to install the manager from gnome"
[/I]

What package do I need to install this. I looked for 'network-admin' in synaptic but I did not find anything like that.[/QUOTE]

It's "gnome-system-tools"

It does require some gnome libraries, but really nothing very big. You'll also get user administration and a few other things.

---

