---
title: "VirtualBox troubles"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by ekmon1582 on 2008-04-01
I have installed Ubuntu 7.10 Gutsy Gibbon on VirtualBox, with Windows XP as my operating system. For some reason, when I go to 'screen resolution' and click on 1024 X 728.. it does nothing but brings up the window if I want to 'keep resolution or go back to old one' except as said it stays the same when I change it.

---

### Post by kellemes on 2008-04-02
> **ekmon1582 said:**
> I have installed Ubuntu 7.10 Gutsy Gibbon on VirtualBox, with Windows XP as my operating system. For some reason, when I go to 'screen resolution' and click on 1024 X 728.. it does nothing but brings up the window if I want to 'keep resolution or go back to old one' except as said it stays the same when I change it.

You need to install the virtualbox guest additions to be able to get a higher resolution.
[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/]("http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/")

But don't assume getting native resolution since you're working in a virtual machine.

---

### Post by ekmon1582 on 2008-04-02
I have installed them. But when I try to get the smaller resolution that came with them, as said above, when I change to the higher one, it does nothing but acts like it has.

---

### Post by kellemes on 2008-04-02
> **ekmon1582 said:**
> I have installed them. But when I try to get the smaller resolution that came with them, as said above, when I change to the higher one, it does nothing but acts like it has.

Can you post /etc/X11/xorg.conf of Ubuntu please?

---

### Post by ekmon1582 on 2008-04-02
Now I get even get Ubuntu to start, well it does, but it's so scrambled I can't see anything... I'll wait till Hardy comes out and try that. Thanks though!

---

