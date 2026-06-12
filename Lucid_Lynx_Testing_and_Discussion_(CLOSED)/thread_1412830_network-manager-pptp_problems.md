---
title: "network-manager-pptp problems"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JCoster on 2010-02-21
Right- I posted a message the other day about not being able to connect to VPN.  I finally got that fixed, but now I have a new problem.

Basically, the VPN connection will never connect as it times out.  Using the same details on my dual-boot Windows 7 works fine.  

The only way I can connect is if I run:
```
sudo apt-get install --reinstall network-manager-pptp
```

..then restart the machine, and then immediately connect.  Even when I do this, the VPN connection drops out after a short while...

Anyone else experiencing the same problems?

Cheers,
JC

---

### Post by JCoster on 2010-03-06
Bump?

---

### Post by JCoster on 2010-03-09
I'll give it one more bump and then leave VPN'ing to a VirtualBox running Karmic.... 

Bump?

---

### Post by nanog on 2010-03-09
yep, pptp connects and fails on some of my installs.

---

