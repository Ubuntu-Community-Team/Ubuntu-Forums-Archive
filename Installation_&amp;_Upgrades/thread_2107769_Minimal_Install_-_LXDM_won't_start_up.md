---
title: "Minimal Install - LXDM won't start up?"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by aem0512 on 2013-01-22
I've done a minimal ubuntu install (12.04) on my old laptop. After it installed the core system I told it I wanted to manually select packages. 

Then at the terminal prompt I installed lxdm (which install lxde too) and network-manager.

(sudo apt-get install lxdm network-manager)

That all seemed to go ok, but now I can't get lxdm to start up on boot. What's the problem?

---

### Post by ibjsb4 on 2013-01-22
What packages did you install?  Did you install a display manager (lightdm)?

---

### Post by aem0512 on 2013-01-22
I thought LXDM was a lighter version of lightdm specifically designed for LXDE.

Is that wrong?

---

### Post by steeldriver on 2013-01-22
did it configure itself as the default-display-manager?

```
cat /etc/X11/default-display-manager
```

---

### Post by aem0512 on 2013-01-22
I think so. I get:

/usr/sbin/lxdm

But still won't startup.

---

### Post by aem0512 on 2013-01-22
I forgot to install xorg. After that, it all works now.

---

### Post by ibjsb4 on 2013-01-22
> **aem0512 said:**
> I thought LXDM was a lighter version of lightdm specifically designed for LXDE.

Is that wrong?

No, not wrong.  But ..

Lightdm is lighter and includes xorg.

[http://packages.ubuntu.com/precise/lxdm](http://packages.ubuntu.com/precise/lxdm)

[http://packages.ubuntu.com/precise/lightdm](http://packages.ubuntu.com/precise/lightdm)

---

