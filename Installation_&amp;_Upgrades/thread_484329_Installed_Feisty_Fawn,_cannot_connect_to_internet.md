---
title: "Installed Feisty Fawn, cannot connect to internet"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by mattdawg8 on 2007-06-25
I installed Feisty Fawn in a dual Boot with XP, and when I ran it from the Live CD, I had internet, I used GAIM,  everything worked. So, I installed it, and now, Ubuntu will not detect my network. i have tried manually typing all of the necessary numbers, names, etc. but that didn't work. I have no idea what to do. Please help!

---

### Post by stchman on 2007-06-25
> **mattdawg8 said:**
> I installed Feisty Fawn in a dual Boot with XP, and when I ran it from the Live CD, I had internet, I used GAIM,  everything worked. So, I installed it, and now, Ubuntu will not detect my network. i have tried manually typing all of the necessary numbers, names, etc. but that didn't work. I have no idea what to do. Please help!

Select DHCP from your Networking under Administration.

---

### Post by Pumalite on 2007-06-25
What kind of connection do you have?. If DSL; they are sometimes hard to configure. I prefer DHCP. For that you need a router.( You also gain a hardware firewall). DSL>Router>DHCP. All Linux recognize that connection automatically and you don't have to configure anything. On the other hand, make sure your installation is recognizing your card and controller. Look at 'System'.

---

### Post by mattdawg8 on 2007-06-25
I'm using a Wireless connection, its  a Texas Intruments 802.11g Wireless Network Adapter. Sorry for not mentioning that. or does DHCP work with wireless?

---

### Post by Pumalite on 2007-06-25
DHCP work with wireless, but you have to set it that way. Consult your manual.

---

### Post by mattdawg8 on 2007-06-25
Is there a way for me to find a manual online? Because I definitely don't know of any physical copy that I own.

---

### Post by Pumalite on 2007-06-25
Can't help you there. Maybe someone that does will jump in. I'll tell you this: I have a D-Lynk wireless. You connect to it through the browser. In 'Advance' tab you have on the left 'DHCP'. I set it to enable.

---

### Post by stchman on 2007-06-26
> **mattdawg8 said:**
> I'm using a Wireless connection, its  a Texas Intruments 802.11g Wireless Network Adapter. Sorry for not mentioning that. or does DHCP work with wireless?

What make of WAP (Wireless Access Point) or wireless router do you own?  You may have to add the MAC address to the MAC filter for wireless.

There might be wireless encryption (WEP, WPA) enabled.

Let us know.

---

