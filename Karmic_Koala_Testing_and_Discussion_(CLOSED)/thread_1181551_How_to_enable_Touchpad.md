---
title: "How to enable Touchpad?"
date: 2009-06-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2009-06-08
Just updated to Karmic and well, the touchpad is disabled. How do I enable it? Also, can you give me a step by step detail as to how?

---

### Post by binbash on 2009-06-08
I think this is a kernel issue.I have the same issue and downgrading to
2.6.29-02062903-generic kernel fixes mine

---

### Post by tjeremiah on 2009-06-08
maybe I should be more specific. The scroll only works but I cant tap to open a item.

---

### Post by taavikko on 2009-06-08
> **tjeremiah said:**
> maybe I should be more specific. The scroll only works but I cant tap to open a item.

[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391)

---

### Post by tjeremiah on 2009-06-08
how do I access PPA?

---

### Post by taavikko on 2009-06-08
> **tjeremiah said:**
> how do I access PPA?

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

Refer to: "Installing software from a PPA"

---

### Post by tjeremiah on 2009-06-08
recent update fixed problem :)

---

### Post by durand on 2009-06-08
Did it? Because I can't right click with the touchpad :(

---

### Post by tjeremiah on 2009-06-08
> **durand said:**
> Did it? Because I can't right click with the touchpad :(

never had that problem but earlier I did an update and now the touchpad can now tap once again.

---

### Post by durand on 2009-06-08
I can tap but I can't right click by going in the corner of the touchpad. It's not a big feature but it was useful.

---

### Post by tjeremiah on 2009-06-15
problem is back after recent update.. :(

---

### Post by durand on 2009-06-15
Just enable the touchpad again with [gsynaptics]("apt://gsynaptics"). Install it and then go to System > Preferences > Touchpad.
The same setting is actually in System > Preferences > Mouse but gsynaptics has other features.

---

### Post by tjeremiah on 2009-06-15
> **durand said:**
> Just enable the touchpad again with [gsynaptics]("apt://gsynaptics"). Install it and then go to System > Preferences > Touchpad.
The same setting is actually in System > Preferences > Mouse but gsynaptics has other features.

Thank you so much !!1:D:D:D

---

### Post by freeman2000 on 2009-06-15
> **tjeremiah said:**
> problem is back after recent update.. :(


Yeah, the problem is back on my laptop also.  The prior link to William Grant's PPA solution didn't work for me, as it stated that I have a newer package already installed.  So I had to go to Sarvatt's PPA to get a remedy.  Here's the link and some useful info from Sarvatt.


[https://edge.launchpad.net/~sarvatt/...-archive-extra](https://edge.launchpad.net/~sarvatt/...-archive-extra)

[ sarvatt's notes -  "BTW, be sure to get rid of gsynaptics and install gpointing-device-settings instead if you're using newer drivers, 2/3 finger scroll options are built into it and SHMConfig isn't needed anymore to change settings. with the latest 1.1.99 you can even turn off the annoying tap and drag thing via synclient that was permenantly enabled on synaptics before." ]     Thanks, sarvatt.  Good luck.

---

