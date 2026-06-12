---
title: "can I upgrade ubuntu to xubuntu?"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by fulgencio on 2008-12-01
Hi, I`m using ubuntu 7.10, on an old desktop, and want to upgrade but I'm pretty sure 8.10 is going to be too much for it. Is there a way to tell upgrade directly to xubuntu?

---

### Post by snowpine on 2008-12-01
Xubuntu is really just Ubuntu with a different desktop environment (Xfce). Try this:

```
sudo aptitude install xubuntu-desktop
```

Then, log out and at the login screen choose Sessions then Xfce. Now you're in Xubuntu!

(If you want to remove all the Gnome-related Ubuntu packages: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce))

Now you can upgrade to 8.04 and then again to 8.10.

You might also consider backing up your data and doing a fresh install of Xubuntu 8.10. There are pros and cons to upgrading vs. a fresh install; I personally don't have a strong opinion one way or the other.

Good luck!

---

### Post by fulgencio on 2008-12-02
Thanks, I upgraded and happily my computer is dealing with Ubuntu 8.04 just fine but I also installed the Xfce desktop and it work perfect :guitar: its great to have upgrades again!

---

