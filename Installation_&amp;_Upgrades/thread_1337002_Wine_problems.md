---
title: "Wine problems"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by Mr Nemo on 2009-11-25
I'm having a problem installing wine. I was messing around with it and probably did something. It says that the packages are broken when I try to install it.

---

### Post by rabidityfactor on 2009-11-25
try ```
sudo dpkg --configure -a
``` and then installing

---

### Post by Mr Nemo on 2009-11-25
> **rabidityfactor said:**
> try ```
sudo dpkg --configure -a
``` and then installing

Holy hell, I've been having so much trouble with this. Thank you so much rabidityfactor. Could you please explain to me exactly what that command did?

---

### Post by Rserit on 2009-11-25
[SIZE=5]I was having the same problem. Thanks bro[/SIZE]

---

### Post by rabidityfactor on 2009-11-26
> **Mr Nemo said:**
> Holy hell, I've been having so much trouble with this. Thank you so much rabidityfactor. Could you please explain to me exactly what that command did?
I'm glad I could help. Well.. It basically reconfigures all the packages. Some errors might have occured in the configuration of packages due to installation interrupts etc. This command corrects them.
This is what *I* think it does. I could be wrong.

---

