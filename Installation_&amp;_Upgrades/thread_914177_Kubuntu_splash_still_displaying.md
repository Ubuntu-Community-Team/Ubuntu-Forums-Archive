---
title: "Kubuntu splash still displaying"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by pwaugh on 2008-09-08
I installed KDE4, then uninstalled it after deciding I like Gnome a lot better, but now I still see "Kubuntu" on startup and shutdown.

How can I change it back to the default?

patrick

---

### Post by caljohnsmith on 2008-09-08
I think all you need to do is:
```
sudo dpkg-reconfigure kdm-kde4
```
And then choose "gdm".

---

### Post by coffeecat on 2008-09-08
If it's the usplash you're talking about, follow steps 3 and 4 of [this usplash howto]("https://help.ubuntu.com/community/USplash").

---

### Post by pwaugh on 2008-09-09
> **caljohnsmith said:**
> I think all you need to do is:
```
sudo dpkg-reconfigure kdm-kde4
```
And then choose "gdm".

Already done that, it's gdm.

---

### Post by pwaugh on 2008-09-09
> **coffeecat said:**
> If it's the usplash you're talking about, follow steps 3 and 4 of [this usplash howto]("https://help.ubuntu.com/community/USplash").

That was the ticket.  Works great, thanks.

---

