---
title: "how remove Oracle Virtualbox 5.1.10"
date: 2016-12-09
forum: Installation &amp; Upgrades
---

### Post by tonjaa on 2016-12-09
i try download  Oracle Virtualbox 5.1.10  an install on ubuntu 16.10 
and i need to know how to remove it.

---

### Post by howefield on 2016-12-09
Did you install Virtualbox from the Ubuntu repositories or download the .deb package from the Oracle website ?

Opening a terminal and using the following command should do it..

```
sudo apt purge virtualbox-5.1
```

You may also be able to remove it using the Ubuntu Software application.

if not, post back.

---

### Post by ajgreeny on 2016-12-09
You can definitely remove any .deb package using synaptic, even if you installed it with **dpkg -i** command.
Synaptic is the first additional package I add to any of my installations of the *ubuntu family.

---

### Post by tonjaa on 2016-12-09
:) thank you very much now i can remove it .

---

