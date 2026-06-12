---
title: "Help!!!"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by edbrown on 2010-02-04
Hello everyone, sorry to post this but I have just installed ubuntu from the ubuntu website for my laptop. Its great. Whatever i read or do though i cannot connect wirless to my bt home hub. please help. im not very technical

many thanks

---

### Post by Grenage on 2010-02-04
Assuming you can connect to the hub using a wire, are you able to check for drivers under System/administration/Hardware Drivers?

Do you know what wifi card the laptop has?

---

### Post by edbrown on 2010-02-04
hi it says no proprietary drivers are in use on this system. how do i find out about wireless card. sorry to be a pain!

---

### Post by Grenage on 2010-02-04
It's no pain :)

Type this into a terminal:

```
lspci
```

---

### Post by edbrown on 2010-02-04
i found this :

Broadcom Corporation bcm4318 [airforce one 54g] 802.11g
Wirless lan controller (rev 02)
VIA technologies, inc. VT6102 [Rhine-II](rev 78)

???????????

---

### Post by Grenage on 2010-02-04
I think most Broadcom cards are supported.  While connected by cable to the router, type this from the command line:

```
sudo apt-get update
```

Then go into hardware drivers, any improvement?

Ok, apparently not!  Check [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx").

---

### Post by edbrown on 2010-02-04
it is doing something, i hope it works. I wanted to put this on my netbook also, is it better than xp for netbook (remix)

---

### Post by edbrown on 2010-02-04
what a legend you are, it works.... thank you

---

### Post by Grenage on 2010-02-04
Glad it works, but all credit should go to the authors of that guide :)

> is it better than xp for netbook

I've never used Windows on a netbook, but Ubuntu netbook remix is supposed to be good!

---

### Post by edbrown on 2010-02-04
hi there i cannot get netbook to get wirless using the method described for my laptop. please help

---

### Post by qwerty2009 on 2010-02-04
Hi, you could try installing the backport drivers (you need to be connected to a wired connection) open synaptic package manager and search for "linux-backports-modules-wireless-karmic-generic" without quotes

---

### Post by Grenage on 2010-02-05
Is it not working for the original laptop, or is this a second one?

---

