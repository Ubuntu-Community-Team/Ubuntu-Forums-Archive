---
title: "wired network not work"
date: 2006-04-04
forum: Installation &amp; Upgrades
---

### Post by whoboo on 2006-04-04
Has anyone succeeded in getting wired network to function on Compaq Presario  2190US ?  If so, how ?  TIA

---

### Post by jamesr on 2006-04-04
I use several compaq desktops without any problems but I do not recognise 2190US model. Is it a laptop? or desktop?. With the desktops, the compaq web site will give the  equivalent of the on-board NIC .

---

### Post by whoboo on 2006-04-04
It's a laptop, a variant of Presario 2100, apparently.  It was a smooth installation.  I think there's a hardware detect problem.

---

### Post by jamesr on 2006-04-04
Post the outputs of```
sudo ifconfig -a
```
or  if wireless
```
sudo iwconfig -a
```

---

