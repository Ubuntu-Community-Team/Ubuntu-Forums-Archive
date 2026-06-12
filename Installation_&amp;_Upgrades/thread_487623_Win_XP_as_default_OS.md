---
title: "Win XP as default OS"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by dennis grollo on 2007-06-29
I have 7.04 installed on the wife's computer in dual boot. The Problem is Grub picks Ubuntu as the default OS, my wife does not want to mess with the down arrow to select Windows XP -sigh! I have looked around and cannot find how to change the default OS in grub from Ubuntu to XP, help will be greatly appreciated.

Thanks Dennis Grollo

---

### Post by vexorian on 2007-06-29
```
sudo gedit /boot/grub/menu.lst
```

This opens grub's config file.

In the config file you have to find a line that says
```

default 0

```

Now, count the position of windows XP in the menu, if it is the third item, change it to default 2, if it is the second item change it to default 1, if it is the nth item change it to default n-1

You can add a timeout, if I am mistaking the timeout is already set to 30 you can find
```

timeout 30

```
And change it to timeout 10 

I have it to timeout 2 since when I boot I am ready to select ubuntu but my brother is not annoyed by it since it chooses windows XP

---

### Post by dennis grollo on 2007-06-29
Thanks worked like a charm. Wife is happy - the universe is spinning properly once again.

---

