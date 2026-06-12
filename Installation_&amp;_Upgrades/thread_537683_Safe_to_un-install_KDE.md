---
title: "Safe to un-install KDE?"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by rberry88 on 2007-08-29
I started with Gnome and liked it very much, but had an itching to try KDE. OK, I tried it and now want to stick with just Gnome. Is there any detriment to un-installing KDE? Or should I just leave it be, I find it added alot to my system that I won't ever use and it just feels bloated. 

If it is safe to un-install KDE, what is the best way to go about it?

:popcorn:

---

### Post by wieman01 on 2007-08-29
It should be safe, yes. I did the same thing once the other way around (uninstalled Gnome) with no incidents.

---

### Post by SeanHodges on 2007-08-29
You should find

```
sudo aptitude remove kubuntu-desktop
```

in a terminal should do the trick. It will also request to remove a whole bunch of KDE-specific applications, check through them quickly first, if it removes one you actually want to keep you'll need to install it againafterwards (although the configuration should still be intact).

---

### Post by wieman01 on 2007-08-29
Uninstalling KDE won't removing your personal settings from the home folder. So you could reinstall KDE easily at a later stage while keeping your profile.

---

### Post by ajgreeny on 2007-08-29
Unfortunately, I think that sudo aptitude remove kubuntu-desktop will only remove everything if you installed it with aptitude in the first place.  If you used apt-get or synaptic I don't think all the KDE applications will be removed, just the metapackage, leaving most of the programs untouched.

Have a look at [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) which tells you how to get a pure gnome system back.

---

### Post by rberry88 on 2007-08-29
> **ajgreeny said:**
> Unfortunately, I think that sudo aptitude remove kubuntu-desktop will only remove everything if you installed it with aptitude in the first place.  If you used apt-get or synaptic I don't think all the KDE applications will be removed, just the metapackage, leaving most of the programs untouched.

Have a look at [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) which tells you how to get a pure gnome system back.

Thanks all for the fast and informative answers, I used the method and psychocats.net and it worked like a charm.:guitar:

---

