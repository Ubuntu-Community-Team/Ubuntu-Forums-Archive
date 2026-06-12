---
title: "black screen"
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by foxy123 on 2010-02-06
tried to install alpha 2 but got a black screen after the first menu (install or try without installing etc.). has anyone else got this problem?

---

### Post by VMC on 2010-02-06
> **foxy123 said:**
> tried to install alpha 2 but got a black screen after the first menu (install or try without installing etc.). has anyone else got this problem?

I'm not sure, sounds like the plymouth problem I was having. Check out my [topic]("http://ubuntuforums.org/showthread.php?t=1396912") and see if you have similar results.

---

### Post by foxy123 on 2010-02-06
> **VMC said:**
> I'm not sure, sounds like the plymouth problem I was having. Check out my [topic]("http://ubuntuforums.org/showthread.php?t=1396912") and see if you have similar results.

looks like that, unfortunately I cannot remove Plymouth from the live cd :(

---

### Post by VMC on 2010-02-06
> **foxy123 said:**
> looks like that, unfortunately I cannot remove Plymouth from the live cd :(

Since you have an Intel video chip try using "nomodeset" on the tail end of the boot string. F6, then add it, without quotes. It may boot but then later freeze.

---

### Post by gjoellee on 2010-02-06
> **foxy123 said:**
> looks like that, unfortunately I cannot remove Plymouth from the live cd :(
Why CD? Boot up in recovery mode, enter command prompt and use:

```
apt-get remove plymouth
```

when done use the command:

```
reboot
```

this time boot normally. You may see an error about plymouth in the boot, but just ignore it.

---

### Post by ace214 on 2010-02-07
I had this- my laptop played the GDM sound but the screen was black until I pressed keys, which just produced jumbled characters.

It's very round-a-bout, but I am able to get to my desktop by entering recovery mode, then choosing drop to root shell with networking prompt, and then entering "startx." Hopefully, some update will fix this soon...

---

