---
title: "Upgraded from 10.10 to 11.04 had problems with compiz"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by mscout2004 on 2011-04-04
**Upgraded from 10.10 to 11.04 had problems with compiz and now I have to toolbars to work with so I cant open anything to get the compiz settings back to the defaults so I get my bars back. How do I get the settings back to default to get the menus back so I can open my programs??**

---

### Post by garvinrick4 on 2011-04-04
> **mscout2004 said:**
> **Upgraded from 10.10 to 11.04 had problems with compiz and now I have to toolbars to work with so I cant open anything to get the compiz settings back to the defaults so I get my bars back. How do I get the settings back to default to get the menus back so I can open my programs??**
Compiz settings:
```
ccsm
```

---

### Post by mscout2004 on 2011-04-04
thx that seemed to work. Are they having problems with the new desktop format and the desktop cube feature in compiz? As soon as I set that setting it blew up on me like that where I had no menus and the desktop cube didnt even work.

---

### Post by garvinrick4 on 2011-04-04
> **mscout2004 said:**
> thx that seemed to work. Are they having problems with the new desktop format and the desktop cube feature in compiz? As soon as I set that setting it blew up on me like that where I had no menus and the desktop cube didnt even work. Yes that feature is not viable.

---

### Post by stanca on 2011-04-04
```
sudo apt-get remove --purge compiz
```
worked for me.

---

### Post by afrodeity on 2011-05-03
> **stanca said:**
> ```
sudo apt-get remove --purge compiz
```
worked for me.

That's not a solution. That's a cop-out.

BTW my version of compiz is Compiz 0.9.4.0, but the Compiz site says the latest release is Compiz is 0.8.6.

---

