---
title: "no internet access"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by rkruse on 2005-11-03
I have just installed ubuntu 5.10 server.  The machine is connected to a LAN. There is an internet connection via cable modem.
I am no Linux expert, so I haven't been able to connect to the internet.
I ping an address outside our local network and I get a "Network is unreachable" message.
I have been searching through the forums and guides without success. Most of the discussions are about desktops equipments and/or GUI based systems.

Any hints?

---

### Post by Hinko on 2005-11-03
What kind of connection do you have? (what have you entered in windows to establish your connection?)

---

### Post by John.Michael.Kane on 2005-11-03
make sure your networkcard is activated. then in the terminal type sudo pppoeconf and follow the directions.

---

### Post by rkruse on 2005-11-04
I did it. I have been able to get internet access.
As I thought it was a relatively simple thing: I used the route command to set up the default route to other networks.

Thanks any way!

---

### Post by Randux on 2006-02-01
I have a cable modem and I get can to my backbone provider's homepage but I can't get to my ISP.  If this is what happened to you, can you please explain how to resolve it?

Thanks,
Rand

---

