---
title: "Reseting xorg"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by caspermac on 2007-06-10
can anyone quickly tell me the code to run the wee programe for setting out the xorg.conf file

---

### Post by chrisccoulson on 2007-06-10
Is this what you're after?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tkjacobsen on 2007-06-10
to skip the manual part use

sudo dpkg-reconfigure -phigh xserver-xorg

---

