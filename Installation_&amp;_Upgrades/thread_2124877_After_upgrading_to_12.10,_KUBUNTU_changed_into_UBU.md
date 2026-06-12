---
title: "After upgrading to 12.10, KUBUNTU changed into UBUNTU"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by andy17 on 2013-03-12
Hi everybody,

I've just updated to KUBUNTU 12.10 and... surprise!!! Now I got Ubuntu   :confused::confused::confused:

```
lsb_release -idrc

```

```
Distributor ID: Ubuntu
Description:    Ubuntu 12.10
Release:        12.10
Codename:       quantal

```


how could that happen?
what can I do to sort this out?

After GRUB, I got two options on LOGIN menu:

```
KDE plamsa
GTK (GNOME)
```


thanks a lot!
Andy

---

### Post by TK999 on 2013-03-13
As for the first part of your message (lsb_release -idrc), that is perfectly normal. It is because Kubuntu is based on Ubuntu ; the two share the underlying architecture and differ only in their default desktop environment and applications. To log into KDE, which is the Kubuntu desktop environment, select the KDE Plasma option when logging in. To get rid of the vanilla Ubuntu Unity environment, run the following command from a terminal:
```

sudo apt-get remove unity

```

---

