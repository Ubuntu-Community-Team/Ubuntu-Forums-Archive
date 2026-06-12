---
title: "Change karmic sources.list to lucid... Now update?"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ventil on 2010-03-12
Hi,
I run Ubuntu Karmic Koala. Basically I have my own minimal version from Ubuntu minimal CD + openbox + lightweight apps.
I changed every line in sources.list from karmic to lucid like this:

```
deb http://si.archive.ubuntu.com/ubuntu/ **karmic** main
to
deb http://si.archive.ubuntu.com/ubuntu/ **lucid** main
```

Now I noticed that I have a lot of updates in Synaptic. I was wondering if:

I could/should update now? I really want to!
If I update... Do I have Lucid Lynx then or just something mixed like "Lucid Koala"? :p
Will my system even work?

---

### Post by Ardrias on 2010-03-12
If you *really* want to upgrade to an alpha, and cant wait, I'd suggest using "update-manager -d" instead of manually making changes.

---

### Post by Ventil on 2010-03-12
I have my own minimal version from Ubuntu minimal CD + openbox + lightweight apps. Not the default Ubuntu. 
I think that with "update-manager -d" I get way too much much stuff. I think that I get default Lucid Lynx with default apps. I don't want that. I just want to update my system.

---

### Post by slakkie on 2010-03-12
Hi,

please have a look at [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

---

### Post by slakkie on 2010-03-12
> **Ventil said:**
> I have my own minimal version from Ubuntu minimal CD + openbox + lightweight apps. Not the default Ubuntu. 
I think that with "update-manager -d" I get way too much much stuff. I think that I get default Lucid Lynx with default apps. I don't want that. I just want to update my system.

update-manager will respect whatever you had installed, you don't have to worry about that. You could also use do-release-upgrade which is the cli version of update-manager.

---

### Post by Ventil on 2010-03-12
OK thankx slakkie.

---

