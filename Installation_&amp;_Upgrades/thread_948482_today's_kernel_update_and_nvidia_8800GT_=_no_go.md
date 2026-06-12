---
title: "today's kernel update and nvidia 8800GT = no go"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by gdp77 on 2008-10-15
After the update my Ubuntu boots only at 800x600 (I had installed the nvidia proprietary drivers through envyNG)

Tried uninstalling and reinstalling the nvidia drivers and the problem remains.

Also system--->administration---> hardware drivers, says that "no proprietary drivers are in use" and gives me no option box to install them. 

Any way to fix the problem? I don't think I am the only one that faces this problem

---

### Post by gdp77 on 2008-10-15
update : 

I managed to resolve the situation by ```

sudo dpkg-reconfigure xserver-xorg
```

I can now work at 1280x1024 but with open source drivers. If I try to install proprietary drivers through system--->administration--->hardware drivers (now the option box is there), the previus problem (post #1) returns.

Are the nvidia drivers incompatible with new kernel?

---

### Post by markbuntu on 2008-10-15
No, they are not. But the problem is that the kernel did not recognize the nvidia kernel modules Envy had installed so it did not install them. You would have seen messages about this if you watched the terminal window when the kernel was installed.

You need to use envy to remove the driver it installed and then reinstall the driver.

---

