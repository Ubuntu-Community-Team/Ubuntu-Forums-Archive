---
title: "hardy-&gt;lucid: wireless ok for me, not for added users"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by rkaras on 2010-05-08
After installation, I had no problems using wireless. Next, I added a new user (with administrative access).  Now, when I log in as the new user, nm-applet doesn't appear in the panel and there is no wireless access.

I've tried adding the Notification Area (nothing appears), making sure that the new user can connect to networks, etc with no success.  System Monitor shows that nm-applet is sleeping.  When I restart and login as myself, everything is still working fine.

Computer: 
Computer: Dell Latitude D600
- Ram: 1 GB
- HD: Hitachi ATA HTS541680J9AT00
- OS: Win XP Pro & Ubuntu 10.04
- OS: win XP pro 32 & Ubuntu 10.04
- Network Controller: Broadcom BCM 4306

What additional info should I provide to assist diagnosis?

Thanks!

---

### Post by rkaras on 2010-05-10
Problem (semi) solved, and pretty simple, too: Log in as one of the added users and go to System>Preferences>Network Connections and click on the "Wireless" tab. Click on "Add" and manually enter the SSID (network name) of the wireless network you want to connect to.  Also check the "Connect automatically" box in the upper left corner of the dialog box.  Give the new connection a name (optional).  When you close the dialog, you'll be asked for the wireless connection's password.

When I finished this, the nm-applet appeared and I had my wireless connection.  BTW, when I clicked on the "available to all users" box in the dialog, it shut off the connection I'd just made.  

nm-applet appears to offer roaming access to other wireless connections, but I haven't tried that.

---

### Post by efflandt on 2010-05-10
Normally when you check the box at the bottom that says: **Available to all users** then any connection set to **Connect automatically** should make the network applet appear automatically for other users if that connection is available.

However, sometimes when configuring wireless in Network Connections I seem to have to try a couple of times before I can get all settings to stick and work.  After that it seems to work fine automatically even for other users.

Even on my desktop the usual default Auto eth0 seemed to disappear sometime after a fresh install of 10.04 LTS.  When I added that back in using DHCP, it worked.  But then when I changed it to static IP, netmask, gateway, DNS, it stopped working until I logged out of X and back in.  It has not failed me since then (my desktop is wired to a Zyxel P-330W in wireless client bridge mode).

---

