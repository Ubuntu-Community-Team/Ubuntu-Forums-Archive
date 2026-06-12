---
title: "Wireless issue"
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by phoogkamer on 2009-03-05
Could there be an issue with wireless encryption with the latest updates on Jaunty?
I cannot connect to my wireless modem with WPA/TKIP encryption. Modem settings are ok and XP on the same laptop CAN connect. Jaunty asks me for WEP encryption after trying for some time. Could this be somethint with wpasupplicant?

Tux

---

### Post by ildfroe on 2009-03-05
I also cannot connect to a wireless network with encryption (WEP). When I disable wireless security in the router, there's no problem connecting.

---

### Post by phoogkamer on 2009-03-05
Just to be clear. My wireless connection has WPA/TKIP encryption, but when connecting with jaunty it asks for WEP encryption in stead of WPA/TKIP.

Ok, I have not tryed that yet, but that would suggest an issue with the encryption portion of the NetworkMangager.

Tux

---

### Post by ildfroe on 2009-03-05
I have it working now. I have enabled ssid in the router, and wireless security (WEP) is also enabled. So maybe it's just hidden networks that doesn't work?

---

### Post by caryb on 2009-03-05
I can confirm this I had to remove the hidden attributes from my 3Com access points to connect.


Cary

---

### Post by jbernardo on 2009-03-05
There is a open bug in launchpad ([#336915]("https://bugs.launchpad.net/bugs/336915")), together with a workaround. Maybe it will work for you?
Thanks.

---

### Post by phoogkamer on 2009-03-05
Ah, I have a hidden wlan. So I'll try this workaround when I get back home.

Tux

---

### Post by excogitation on 2009-03-15
Hearing you talk about using WEP encrypted wireless networks I was wondering if you know that WEP isn't secure by any means.

---

