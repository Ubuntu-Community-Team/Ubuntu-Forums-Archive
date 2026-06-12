---
title: "No write permissions on the install directory"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by kareed on 2010-09-04
I'm pretty new to Linux but I know my way around. I've gotten Google Earth downloaded and am trying to install it.  Everything is fine until I try to install it into /usr/local (or somewhere in there).  The Google Earth Setup keeps telling me that I do not have write permissions on this directory.  

Question: How do I change the write permissions for this folder? Or should I install the program somewhere else? The last program I installed (xMind) installed into /usr/local.

I am the only user (administrator).

Thanks for your help.

PS. I'm using Lucid Lynx 10.04.1

Also, I installed it to the default (/home/me/googleearth) and when I try to launch it it says "untrusted application launcher"

---

### Post by rtimai on 2010-09-04
Kareed, may I suggest that you try here. You have my sympathy, but you are likely to get more experienced advice from the support site dedicated to the product.

[http://earth.google.com/support/](http://earth.google.com/support/)

Ubuntu does provide a way to run installation tasks AS root (administrator,) but you should investigate the Google support site first. Good luck, and I hope you get to enjoy Google Earth.

---

### Post by oldos2er on 2010-09-04
> **kareed said:**
> I'm pretty new to Linux but I know my way around. I've gotten Google Earth downloaded and am trying to install it.

If you're installing the *.bin file, you need to run it with sudo. ```
sudo ./GoogleEarthLinux.bin
```

---

