---
title: "Ubuntu Gutsy 7.10 hangs after updates have been downloaded and needs reset!"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by siretfel on 2008-01-18
Hi all,

I have a problem with the update process in my ubuntu 7.10. The last two times ubuntu have notified me to update, after the updates, about two to five minutes my notebook hangs and i have to FORCE shutdown with the power button. 

Everything is stuck. The mouse doesn't work, keyboard all the same, and music is stuck. NOTHING works, not even caps lock button in keyboard.

Anyway, i don't know how to fix this and it pisses me off since i moved from windows to ubuntu EXACTLY for such reasons. 

Hope someone has some answers

Thanks you guys.

---

### Post by zvacet on 2008-01-18
Boot in recovery mode and type

```
dpkg --configure -a
```

or

```
apt-get -f install
```

---

### Post by siretfel on 2008-01-18
> **zvacet said:**
> Boot in recovery mode and type

```
dpkg --configure -a
```

or

```
apt-get -f install
```

Thanks for your reply. Can you please tell me what does these commands do?

---

### Post by zvacet on 2008-01-18
>  Reconfigure an unpacked package. If -a  or  --pending  is  given
              instead  of  package, all unpacked but unconfigured packages are
              configured.


>  Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution.

You can read more in **man dpkg** and man **apt-get**

---

