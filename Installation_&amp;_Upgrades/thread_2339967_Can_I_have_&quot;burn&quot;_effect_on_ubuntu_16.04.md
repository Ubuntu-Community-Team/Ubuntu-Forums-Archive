---
title: "Can I have &quot;burn&quot; effect on ubuntu 16.04 LTS using &quot;compiz&quot;?"
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by magicianofthemes on 2016-10-14
Hi,

I am trying to find a way to have 'burn' effect using compiz but even after installing addon animations, I can't seem to find it.

I wanted to know if there's a way to get the burn effect?

Thanks!

---

### Post by howefield on 2016-10-14
Assuming that you have compizconfig-settings-manager installed you will also need compiz-plugins-extra.

```
sudo apt install compiz-plugins-extra
```

But there is a reason why compizconfig-settings-manager isn't installed by default, if you break your install, you get to keep all the pieces :)

---

### Post by #&amp;thj^% on 2016-10-14
I think I heard talk the (Or some of the add-ons are only available in 16.10 Yakkety)
I have not heard if they were going to be available for 16.04 (Xenial) at some point.
Regards
Ninje'd by howefield

---

### Post by magicianofthemes on 2016-10-15
> **howefield said:**
> Assuming that you have compizconfig-settings-manager installed you will also need compiz-plugins-extra.

```
sudo apt install compiz-plugins-extra
```

But there is a reason why compizconfig-settings-manager isn't installed by default, if you break your install, you get to keep all the pieces :)

Thank you very much, it worked!

---

### Post by howefield on 2016-10-15
You are welcome, but as said, be careful in there. :)

---

