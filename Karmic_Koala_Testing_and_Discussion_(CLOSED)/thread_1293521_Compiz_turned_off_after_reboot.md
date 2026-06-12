---
title: "Compiz turned off after reboot"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 4ekuct25 on 2009-10-17
Hi :)

Compiz working well, but after each computer reboot it turned from "extra" to "none" at Appearance->Visual Effects.

kernel: 2.6.31-14-generic
videocard: GeForce 6600GT
video driver: 185.18.36-0ubuntu7
compiz version: 1:0.8.4-0ubuntu1

---

### Post by barisurum on 2009-10-17
I have the same problem: 

ATI X1950XT
rt kernel 2.6.31-9
OSS radeon driver
compiz 0.8.4-0ubuntu1

---

### Post by kc600 on 2009-10-17
Same here. Looked in Launchpad, found this: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/432871](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/432871) So i tried re-installing compiz, but the situation stays the same.

Filed a new bug about it: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/453912](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/453912)

---

### Post by nanog on 2009-10-21
I've got this one one of my boxes. Although its only a minor nuisance it really should be fixed. Absolutely nothing comes up in gdm logs or xorg logs. If I select metacity the box starts up fine and there are no errors in compiz --replace. 

This is a weird one.

---

### Post by nanog on 2009-10-21
Fixed for me by:

```
sudo apt-get remove --purge compiz compizconfig-backend-gconf compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper libcompizconfig0
```


```

rm -rf ~/.config/compiz; rm -rf ~/.compiz

```


```
sudo apt-get install compiz compizconfig-backend-gconf compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper libcompizconfig0
```

---

### Post by nanog on 2009-10-21
If this is fixed for you its a failed update and the bug should probably be marked as invalid.

---

### Post by 4ekuct25 on 2009-10-27
it does not work for me

---

