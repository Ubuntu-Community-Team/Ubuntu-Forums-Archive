---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by accodata on 2008-09-28
Hi 

I have just installed Heron on my pc, when I went to install Java, it wouldn't allow me to press ok, at the end of the agreement.

I got this message, 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

I have no idea how to fix it. Could I please get some help.

with thanks

Tracey

---

### Post by lisati on 2008-09-28
From a terminal (it's on the Applications->Accessories menu), type in ```
sudo dpkg --configure -a
``` and press 'Enter'. It will ask for your password, which won't show as you type it in (as a security precaution) and press 'Enter"

---

### Post by accodata on 2008-09-28
Thank you so much that is awesome, it works, BUT does that mean that Java needs to be installed again, or is it already installed?

with thanks

Tracey

---

### Post by lisati on 2008-09-28
> **accodata said:**
> Thank you so much that is awesome, it works, BUT does that mean that Java needs to be installed again, or is it already installed?

with thanks

Tracey

To be honest, I'm not sure - it can depend on what's being installed when the error pops up. Anyone else got any thoughts?

---

### Post by overdrank on 2008-09-28
Hi and yes you will need to install java again but when you see the ok button use the tab key to highlight and then enter. You should be good then. :)

---

### Post by WWSmith36 on 2008-09-28
This should cover everything

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get upgrade
```

Hope it helps

---

### Post by WWSmith36 on 2008-09-28
To install java

```
sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by oldos2er on 2008-09-28
> **accodata said:**
> Hi 

I have just installed Heron on my pc, when I went to install Java, it wouldn't allow me to press ok, at the end of the agreement.



 To move around in the ncurses terminal, use the Tab key or arrow keys. Use the space bar to highlight 'OK' then hit Enter.

---

