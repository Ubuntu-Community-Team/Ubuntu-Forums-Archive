---
title: "Was Fast, Now Slow"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by erkrus on 2011-02-20
Over the past few months due to one reason or another I've had to reinstall Ubuntu on my laptop. The first time I installed Ubuntu and every install after it ran nice and fast. On my latest re-install it has been running a little "laggy". That is the best word I can use to describe it. Basically when I click on something there is a delay before it actually does something. It's not very apparent or there at all in normal internet browsing or gaming, however when navigating through menus and similar operations it is very noticeable. 

Any ideas what could be causing this?

Hope this is an appropriate area for this post.

Thanks in advance.

---

### Post by sikander3786 on 2011-02-20
Welcome to the forums :-)

We need to know more about your hardware specs i.e, processor, RAM and graphics card.

Which version of Ubuntu is this? Did you install the latest update from update-manager or by running this command in Terminal under Applications > Accessories sub-menu?

```
sudo apt-get update && sudo apt-get upgrade
```

Did you install the drivers for your graphics card?

---

### Post by erkrus on 2011-02-21
Processor: Intel Centrino 2 @ 2.26 GHz each

RAM: 3.9GB

Hard Drive: 500GB @ 7200RPM

Graphics Card: NVIDIA GeForce 9800M 1GB (recommended driver installed)

Ubuntu Version: 10.10 Maverick Meerkat (all updates and upgrades installed)

Gnome Version: 2.30.2

---

### Post by sikander3786 on 2011-02-21
Is compiz enabled? If yes, try reverting to metacity and see if the menus still lag with it also.

Press Alt + F2 and in the pop up window, type,

```
metacity --replace
```

---

### Post by erkrus on 2011-02-21
Metacity definitely seems faster

---

