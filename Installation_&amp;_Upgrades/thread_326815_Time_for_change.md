---
title: "Time for change"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by addisor on 2006-12-28
Just about to order all the new bits for a partial new build, except I want to keep my old 80g hardrive as I like all the custom tweaks I've made and have no idea how i did them!!! doh. Just been reading that when changing mobo its best to re-install o/s. Shall I use this opp to swap over to 64bit syst? Is there anyway to save email/fav and more importantly the custom tweaks made?

---

### Post by taurus on 2006-12-28
If you want to keep all your settings, then you definitely want to save your $HOME directory.  Save it to a USB memstick or burn it to a CD.  Replace the mobo; install Edgy (I assume you are using Edgy right now); back copy $HOME back to the new harddrive.

Even if you decide to go with the x86_64, you still can use the same settings in $HOME...

---

### Post by addisor on 2006-12-28
just so i know i'm looking in the right place, what files or settings should i except to find in home?

---

### Post by taurus on 2006-12-28
All those hidden files/directories that start with the dot, .!  You can see them all with this command from a terminal, Applications -> Accessories -> Terminal.

```
ls -la ~
(The ~ sign stands for your $HOME directory.  If your login name is addisor, them ~ is the same as /home/addisor...)
```

---

