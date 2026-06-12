---
title: "Installed 14.04, no wifi"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by remn on 2014-05-26
My wireless adapter is the Dell Wireless 1510 Wireless-n (I think it's made by Broadcom).

I installed 14.04 and it doesn't seem to be recognizing my wireless card. It recognized the card on an earlier installation, but I had to re-install because I had changed the name on the home folder and it wasn't showing my files. I don't know if that has anything to do with why the wifi wouldn't be working this time when it worked on the first install.

---

### Post by kc1di on 2014-05-26
could you post the outputs of the following terminial commands:

```
lspci
sudo lsmod
rfkill list all
```

we will try to help with that information.

---

