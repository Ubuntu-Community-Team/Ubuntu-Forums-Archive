---
title: "Unable to boot - HP Pavilion dv6"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by gtosco on 2010-04-07
Hi everybody,

I've just installed Ubuntu 9.10 64 bits on my new HP Pavilion dv6, but it seems to boot almost randomly. I think it might be an issue related to the ATI graphics card, but I don't know how to solve it. Could you help me?

Thank you very much in advance!

---

### Post by duanedesign on 2010-04-07
Did you try and install the proprietary flgrx driver? It might be it doesn't play well with your  card.

You should be able to drop to tty1 console when the screen turns black by hitting CTRL+ALT+F1. Then try renaming your xorg.conf.

```
sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
```

then restart

```
sudo reboot
```

If you did install the fglrx driver and that is the source of your issue (you will know because renaming the xorg.conf let you boot) you should uninstall it and go with the open source radeon driver.

---

