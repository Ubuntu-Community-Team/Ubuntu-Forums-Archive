---
title: "adding wifi no net connection xubuntu belkin"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by blackest_knight on 2006-07-16
ok i am using a belkin 54g wireless card 
i used the synaptic package manager to install ndiswrapper-utils
copied the bcmwl5.inf and sys files to the desktop

sudo ndiswrapper -i ~/D (tab) /bcmwl5.inf

Checked the installation by 
sudo ndiswrapper -l

Installed ndis drivers:
bcmwl5        driver present, hardware present

then for ndiswrapper to be loaded automatically on boot:

sudo ndiswrapper -m

i tried modprobe ndiswrapper but still nothing it also calls the card eth0
not wlan0

any idea's i also have a ra0 type card but havent a clue how to make that run either

---

### Post by blackest_knight on 2006-07-16
I don't know what did it but the rt2500 card just started working 
I did lose wireless network on my better laptop for a while too very strange. 

anyway jobs done p166 with 48meg ram installed and working wirelessly with xubuntu and another windows pc joins the linux ranks :D

its not fast but still seems better than with win98 on it

---

### Post by orb9220 on 2006-07-16
Now if there was a way to bump up that memory then you would have alot nicer experience.

But not bad being what it is.

Good Luck

---

