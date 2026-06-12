---
title: "Minimilistic Gnome Install"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by stormblue on 2006-08-11
Would it be possible for me to just install gnome in some way and not have all the other crap that comes with.  I don't need the full desktop.

I'd install the server and then get the packages from there, but I'm not sure what package I need for just gnome.  I'd like to have all the applets, but not have bittorent clients, e-mail clients, graphics, games.

Any suggestions?

---

### Post by Jagot on 2006-08-11
> **stormblue said:**
> Would it be possible for me to just install gnome in some way and not have all the other crap that comes with.  I don't need the full desktop.

I'd install the server and then get the packages from there, but I'm not sure what package I need for just gnome.  I'd like to have all the applets, but not have bittorent clients, e-mail clients, graphics, games.

Any suggestions?

You could do a server install then:

```
sudo aptitude update
sudo aptitude install gnome-core
```

I think there is also an even more minimalistic package called gnome, but not sure if that would work.

gnome-core is in the universe repository, so you would have to enable that first.

Read about them both here:

[http://packages.ubuntu.com/dapper/gnome/gnome](http://packages.ubuntu.com/dapper/gnome/gnome)
[http://packages.ubuntu.com/dapper/gnome/gnome-core](http://packages.ubuntu.com/dapper/gnome/gnome-core)

---

### Post by stormblue on 2006-08-11
Gnome Core is exactly what I'm looking for.  Thanks!

---

