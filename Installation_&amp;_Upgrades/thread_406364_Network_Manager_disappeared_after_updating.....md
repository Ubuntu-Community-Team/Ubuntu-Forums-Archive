---
title: "Network Manager disappeared after updating...."
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by iClouseau88 on 2007-04-10
Hi,

I just installed update of linux-restricted module 2.6.20-14-generic.  After hitting the reboot icon, the laptop screen stayed blank for a long time.  I then unplugged the powercord and retarted the machine.  After Feisty boots, I saw a yellow triangle with an exclamation mark below Network Manager icon.  It shows "No network connection".  I hit  "enable network connection" but now the NM icon disappears.  I am able to get Firefox to load though.  How can I get NM icon back?

Thanks in advance.

---

### Post by iClouseau88 on 2007-04-10
I got the NM icon back per spd106's thread dated March 5 in Networking& Wireless Forum:

Code:

sudo /etc/dbus-1/event.d/25NetworkManager restart

However, I still have the orange warning icon just below the NM icon.  It says "No network  connection" even though I still get (wired) Internet connection.  Is this a new bug in Feisty?

:confused:

---

### Post by zvacet on 2007-04-11
From my expirience NM don´t work as it supose to.I removed it first day I sow it on my panel.I belive other people will say diferent story,but this is my.

---

