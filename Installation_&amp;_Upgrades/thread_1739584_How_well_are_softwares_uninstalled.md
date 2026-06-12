---
title: "How well are softwares uninstalled?"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by MundoMondo on 2011-04-26
Hello!

I have been using ubuntu for a long time and am looking into migrating into Xubuntu due to the change to unity in ubuntu. I am wondering how well softwares are installed. Are there benchmarks or tests of some kind that show how many files / directories registry keys that tend to become "leftovers" when a software is uninstalled?

I tend to try alot of programs from the general repos. This means i do alot of uninstalling of uninteresting programs. Is there any reason to think there are leftovers in the system, or does it (though i doubt it) remove 100% of the uninstalled softwares files?

---

### Post by adit on 2011-04-26
From my personal experience softwares are not uninstalled completely.  There are always leftovers in my home directory even if you use the command
sudo apt-get --purge remove package-name

---

### Post by KegHead on 2011-04-26
Hi!

If you remove in synaptic..you have an opportunity to completely remove.

KegHead

---

### Post by MundoMondo on 2011-04-27
I suspect

```
sudo apt-get autoremove <insert package name> --purge
```

also does the trick. I just learned this today, though it seems it does have some issues with removing
icons from the usr/share/applications directory when uninstalling something. I quite often find icons
lingering in there from programs i have uninstalled.

---

### Post by m_duck on 2011-04-27
Using apt or synaptic you can remove the majority of a program. Those tools will not however touch any configurations etc that reside in your home directory. You would have to prune that manually.

---

