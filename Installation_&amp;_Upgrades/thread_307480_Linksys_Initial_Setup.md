---
title: "Linksys Initial Setup"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by Epperly on 2006-11-26
Hi, I just got a new Wireless-G router because my old Wireless-B pretty much died, I got a WRT54G.
And since the setup CD is made for Windows(exe), I was wondering how can I set it up without the CD? I don't have Windows at all.

Also, sorry if this thread is supposed to be under Wireless but Installation and Upgrades sounded more fitting.
Thanks!

---

### Post by angryfirelord on 2006-11-26
Usually with routers you don't need to install anything special. The cds that come with routers are just tools for Windows for managing Wireless connections (since Windows lacks good tools). If you can't connect to it, then it's more of a configuration problem with the card itself. Look under System-->Administration-->Network Tools to configure it (somehow ;) ).

---

### Post by Epperly on 2006-11-26
dude but the CDs are for Windows...
I thought you had to do **** in the 192.168.1.1 linksys setup.. no?

---

### Post by angryfirelord on 2006-11-27
I have a D-Link DI-524 that only had a Windows/OS X cd and I didn't even need it. The firmware on the router is what makes it run, not the cd. What issues are you having with your network?

---

### Post by Epperly on 2006-11-27
I don't know how to set it up, hah... my DNS servers change and my eth0 in the default gateway or whatever like goes away I have to reclick it..

---

### Post by angryfirelord on 2006-11-27
Eth0 is usually the name of an ethernet port, but sometimes wireless is referred to that. First, plug in the router and wait for it to initialize. Plug in the cable modem into the uplink port or something similar. On my modem, the PC Activity light starts to blink, which is normal. Under System-->Administration-->Networking, made sure that the proper network interface is turned on and running. If it's not, activate it and make sure it uses DHCP.

Now Ubuntu did this automatically, but that's how I set up my wireless network.

I hope that I solved your problem somewhat. Let me know if I didn't.

---

