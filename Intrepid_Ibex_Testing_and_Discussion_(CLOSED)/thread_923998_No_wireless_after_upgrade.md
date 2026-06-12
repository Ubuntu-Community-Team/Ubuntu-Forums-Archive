---
title: "No wireless after upgrade?"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SnowPunk98 on 2008-09-19
I have a Latitude D830 and did an upgrade from Hardy, I have an Intel 4965AGN wireless card and can't seem to get any connection. if I do an ifconfig I have a wlan0 and if I do lspci I can see the wireless card.

When I first booted into Intrepid I did not have the network monitor in the top panel, when I added it I only had lo.

---

### Post by SnowPunk98 on 2008-09-23
Anyone know?

---

### Post by mikedep333 on 2008-09-23
I did a fresh install of Intrepid alpha6. Network-manager was buggy (listed each connection twice [ironic in light of your problem]) (and it gave me a hassle trying to connect.) It seems to work ok overall though.

I have an intel 3945ABG, which uses the same basic driver.

---

### Post by wenuswilson on 2008-10-16
Bump!

I have this exact problem as well. My computer see that my wireless exists but it makes no effort to find any wireless connections. I upgraded a couple days ago into Ibex. and I really don't want to have to do a fresh install to get this to work. 

/Bump!

---

### Post by Jove on 2008-10-16
We've been having this issue at work most of today. I think we've found a fix which involves editing /etc/network/interfaces and removing all lines except those which start with "auto" (so leave "auto eth0" "auto eth1" "auto wlan0" etc.) AND edit /etc/NetworkManager/nm-system-settings.conf and change it to read:

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

then reboot. You should then have an nm-applet which detects and allows connection to wireless (and wired) ethernet. Good luck!

---

### Post by wenuswilson on 2008-10-16
> **Jove said:**
> We've been having this issue at work most of today. I think we've found a fix which involves editing /etc/network/interfaces and removing all lines except those which start with "auto" (so leave "auto eth0" "auto eth1" "auto wlan0" etc.) AND edit /etc/NetworkManager/nm-system-settings.conf and change it to read:

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

then reboot. You should then have an nm-applet which detects and allows connection to wireless (and wired) ethernet. Good luck!

In my /etc/network/interface file there was no "auto eth0, auto wlan0" so I added them and removed everything else. I rebooted and still no Wireless Networks. 
(For the pessimistics out there, where I currently am there are at least 5 separate wireless networks that I could find when Hardy was on my system.)

Thank you for the advice though.

---

### Post by Jove on 2008-10-16
Did you edit /etc/NetworkManager/nm-system-settings.conf ?

---

### Post by wenuswilson on 2008-10-16
> **Jove said:**
> Did you edit /etc/NetworkManager/nm-system-settings.conf ?

my entire nm-system-settings.conf file --

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

as recommended by your earlier post. should there be more in it than what i have?

---

### Post by Jove on 2008-10-16
Actually, there was one further thing we had to do. Have a look in /var/log/syslog for messages about missing firmware. If you find them, copy the firmware file referred to from an earlier kernel into /lib/firmware/<kernel-release>

---

### Post by BXCracer on 2008-10-16
> **Jove said:**
> Actually, there was one further thing we had to do. Have a look in /var/log/syslog for messages about missing firmware. If you find them, copy the firmware file referred to from an earlier kernel into /lib/firmware/<kernel-release>

Yup, that solved my problem with rt61 firmware missing.

---

### Post by wenuswilson on 2008-10-16
AWESOME! Thank you for that, I just copy and pasted all of my firmware files from an old kernel, it seemed to work out just fine.

---

