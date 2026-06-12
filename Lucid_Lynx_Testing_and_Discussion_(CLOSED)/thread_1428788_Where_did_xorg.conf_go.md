---
title: "Where did xorg.conf go?"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ViperScull on 2010-03-13
I'm using xorg-edgers, kernel 2.6.33, and everything works fine. But i have no xorg.conf

I want to make some adjustments for the Plasma TV. Do i have to create it from scratch or can it be created automatically?

---

### Post by grandtoubab on 2010-03-13
Xorg.conf is no more mandatory since Karmic, boot in recovery mode , select root shell
```
X -configure
```
```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

---

