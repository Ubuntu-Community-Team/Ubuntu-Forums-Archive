---
title: "Network Manager broken / Firefox Work offline"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2008-10-08
I've noticed that although Network manager says I'm not connected (and that the device is unmanaged, namely my builtin mobo's LAN), I am still able to get on the net and ping other sites.

What is really annoying is that everytime I open Firefox it starts in "work offline" mode.

Any ideas on how to fix this? Just happened with today's updates.

---

### Post by iClouseau88 on 2008-10-08
Refer to my post earlier today:


> Following the thread by kadafi69 (not related to Colonel Khadafy?), I added a comment sign # to iface eth0 inet dhcp in my /etc/network/interfaces file and saved it. This solves 2 problems:

1. Messed up network manager
2. Firefox not starting up consistently because of automatic "File-work offline"
 

---

### Post by Enigmatic on 2008-10-08
Alright, I now have this in my interfaces file. I've restarted networking, but there seems to be no effect. Do I need to restart X also?

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp
#mtu 9000

---

### Post by caryb on 2008-10-08
I have the exact problem, I have commented out all bar the loopback as well but it does not fix the problem


Cary

Update after 2nd reboot it works fine with the interfaces file commented out!


Cary

---

### Post by anywebloco on 2008-10-09
I had this problem too and there are bug reports around it.

firefox (apparently) takes it's online/offline status from DCOP messages and so, if network-manager is not working (even if you're connected via some other route), firefox will think it's offline.

What worked for me is this: I have an rt61/rt2561 wireless card (in my desktop PC) and this does *not* work OOTB for me with network-manager, despite that fact that it "should".

So to get my internet connection working I install the latest csv versios of the rt61 driver from serialmonkey and overwrote /etc/network/interfaces so that the system connects at boot.

So at this stage, my wireless connection worked, but network-manager didn't. Consequently, firefox still thought it was offline.

So I uninstalled network-manager & network-manager-kde.

Works perfectly, as long as you don't mind not having network-manager.

In Hardy, you could just disable network-manager (rather than remove it). Unfortunately I can't seem to figure out how to disable it in Intrepid.

So in short:
1) remove network-manager & network-manager-kde (or gnome)
2) overwrite /etc/network/interfaces with details of yuor connection

---

