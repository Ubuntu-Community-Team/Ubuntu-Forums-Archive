---
title: "Kernel Install"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by ibuclaw on 2008-04-26
Hi all, I've gone off on an expedition and have compiled the new linux 2.6.25 kernel for myself.

I've done all the right steps (I hope)
```

make mrproper
make menuconfig
# setup some settings saved config file
make all
make deb-pkg
cd ../
dpkg -i linux-2.6.25-1.deb

```

Now, as far as I can tell that has done everything but make a new line in my boot menu.lst file.

This is where I'd like a little push in the right direction (just to be sure)
Shall I create an identical copy of the ubuntu line, but change vmlinuz-2.6.24 for 2.6.25??
Or is a bespoke line needed?


Regards
Iain

---

