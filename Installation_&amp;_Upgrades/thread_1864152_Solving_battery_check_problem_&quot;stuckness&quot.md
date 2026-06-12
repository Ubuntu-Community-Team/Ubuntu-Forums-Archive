---
title: "Solving battery check problem &quot;stuckness&quot;"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by durammx on 2011-10-18
Hello!

I solved the problem by loading the rescue and then:

```
Go to root

[COLOR=Red]Remove all nvidia drivers:[/COLOR]
 apt-get remove nvidia*

Then startx
```Now you can install the 280 nvidia driver correctly thru jockey-gtk

reboot and enjoy.

---

