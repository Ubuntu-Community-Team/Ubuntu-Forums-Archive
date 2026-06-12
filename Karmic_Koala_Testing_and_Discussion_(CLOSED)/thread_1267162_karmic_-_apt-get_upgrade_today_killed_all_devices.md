---
title: "karmic - apt-get upgrade today killed all devices"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tehk on 2009-09-15
Network card, mouse, keyboard, video all broke today after I upgraded in Karmic.

I can Control-Alt-F6 and use another termincal, restart KDM after removing xorg.conf, however my mouse and keyboard don't work at all in KDE.

My network card has disappeared, and the following scripts are help back:

initscripts, lib32asound2-plugins, libglib2.0-date

All this seems to have happened after the kerneloops package failed to upgrade correctly. I removed KSplice and other dependent packages, and then it finished upgrading about 77 other packages.

I need to get my network card back! Even:

ifconfig eth0 up

doesn't seem to get my card to start correctly with an ip address.

Help!

---

### Post by eris23 on 2009-09-15
Lost mouse, gnome, wireless.  Currently chrooted from livecd.

---

### Post by unclecameron on 2009-09-15
same here, I was able to config my wired network and get to the network to look for updates after I hit ctrl-alt-F2 and got a console by doing:

edit /etc/resolv.conf --> insert nameserver 192.168.1.1

edit /etc/hosts --> insert 192.168.1.x myhost.name

ifconfig eth0 192.168.1.x netmask 255.255.255.0 up

route add default gw 192.168.1.1 eth0

I looked through the logs and didn't see anything puking. I also tried to login from another machine via ssh, but I get a TTY0 error and no prompt. Anyway, hope that helps someone else so maybe they can get whatever update might be coming to fix this. Looks like GDM/X is puking. I also eventually got another external usb mouse to work, but after gdm loads I can't open an xterm, it says I have a child process problem.

---

### Post by eris23 on 2009-09-15
After installing mountall, then updating initscripts (and one other), I got back gnome and mouse control.  Modules for wireless were there, but network manager (and dhclient, and dhclient3) failed to connect.

---

### Post by unclecameron on 2009-09-16
after waiting about 12 hours, brought the machine back into rescue mode with networking and did an apt-get udate && apt-get upgrade and now I have my desktop, mouse, keyboard and network manager after it updated about 60 packages :) whew!

---

