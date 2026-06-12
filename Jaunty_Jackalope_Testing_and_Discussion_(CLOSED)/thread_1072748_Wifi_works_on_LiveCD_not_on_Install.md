---
title: "Wifi works on LiveCD not on Install"
date: 2009-02-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by syko21 on 2009-02-17
I have an Intel 4965agn card that works perfectly on the livecd but fails to work when connected to my specific access point after install.

My access point is a wrt300n with WPA2 AES encryption broadcasting SSID on mixed mode 802.11BGN. It connects but websites fail to load and no console commands can access the internet. However my local network works fine, I can remote desktop into my Vista machine and see shared folders fine.

My neighbor has an unprotected router that I tested and everything works fine when using that connection. I don't know what type of network my neighbor uses.

So far I have tried changing my SSID, my neighbor's has no spaces and mine did, removing encryption, changing to BG mode, recompiling with a newer compat-wireless module, using network-manager and wicd, and switching kernels to the LiveCD default. None of these options worked.

Anyone have any ideas on how to troubleshoot this?

---

### Post by syko21 on 2009-02-18
bump

---

### Post by Gramps on 2009-02-18
Your connecting to your local network using WiFi correct? If so then I would think that the problem is between you router and cable/dsl modem. Can your neighbor access the internet using you access point?

---

### Post by emelce on 2009-02-18
Intel PRO/Wireless 3945ABG doesn't work anymore after today's updates. I've been using Ubuntu 9.04 for a long time (relatively;) and never had any problems...

---

### Post by caryb on 2009-02-18
I have found the intel wireless do work but not at the networkmanager level if you run the config from the /etc/network/interfaces file it still works for me.


Cary

---

### Post by syko21 on 2009-02-18
My network is otherwise fine, all other machines (ipod, cell phone, vista, xp) can connect and use the internet. Its just my laptop and after install, livecd works perfectly.

---

### Post by syko21 on 2009-02-18
[https://bugs.launchpad.net/ubuntu/+bug/330755](https://bugs.launchpad.net/ubuntu/+bug/330755)

I filed a bug report if anyone else is experiencing similar problems

---

