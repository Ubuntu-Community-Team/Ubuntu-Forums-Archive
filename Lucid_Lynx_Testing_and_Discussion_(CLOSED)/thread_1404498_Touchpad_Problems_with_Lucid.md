---
title: "Touchpad Problems with Lucid"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JCoster on 2010-02-11
I just installed alpha 2 on a partition of my Vaio fw31zj and I now two issues with my mousepad:
1) tapping the pad no longer works as a click.
2) The scrolling area does not work.

I swear that in Karmic this was configurable through "System > Preferences > Mouse" but the options aren't there anymore?

Cheers,
JC

---

### Post by phillw on 2010-02-11
Hi,

It's System --> Preferences --> Mouse --> Touchpad on my system

Touchpad is a tab on the top right of the tabs that open with 'Mouse'

**Enable Mouse Clicks with Touchpad**

and

**Scrolling --> Edge Scrolling**

Are the two settings on mine - but, TBH - it set them itself - That's the 1st time I've been in that area !!

Regards,

Phill.

---

### Post by JCoster on 2010-02-11
Ahh right- I didn't have the 'Touchpad' tab.

Basically, I just had to run:
```
sudo apt-get install xserver-xorg-input-synaptics
```

Restarted, and it edge-scrolling and tab to click were enabled by default.

Cheers for your help and making me realise something was missing!
JC

---

