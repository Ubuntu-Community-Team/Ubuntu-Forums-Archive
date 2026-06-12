---
title: "Ubuntu 7.04 BETA &amp; Toshiba Satellite"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by holz on 2007-03-31
Hi all

I am trying to install the BETA version on my Satellite(P105) but I get an error telling that no screen found.
Anyone?

---

### Post by Majorix on 2007-03-31
You have to type in

```
sudo dpkg-reconfigure xserver-xorg
```

And fill in the correct values for monitor refresh rates. You might have to look at the product description for your laptop in order to learn what these values are.

---

### Post by holz on 2007-03-31
Where & when? I am unable to get the installation going at all. Once I get the 2 page long error description, the command prompt is stalled, all I can do is CTRL+ALT+DEL

---

