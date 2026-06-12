---
title: "Saving Grub boot Changes?"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by LOhateVE on 2007-09-04
hi im new here, (and to Linux) I had a quick question.

I finally got my vista/ubuntu dual boot to work.

I set it up with EasyBCD.

Anyways when it goes to the list, I have 2 Regular ubuntu selections in grub, both trying to boot (hd2,1)

to get Ubuntu to load I have to change then to (hd1,1) and then boot it. how do I edit it so it stays as (hd1,1) and remove the duplicate line?

---

### Post by thelocust on 2007-09-04
your looking for menu.lst in /boot/grub.

First back it up

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Now your good if you mess anything up. Then open the file as root and change it towards the bottom. Also I always print out a copy so that I can boot it manually if tings get really messed up.

---

### Post by LOhateVE on 2007-09-04
thanks a lot. :)

---

### Post by confused57 on 2007-09-04
Also, be sure to change it in the line with #groot:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

