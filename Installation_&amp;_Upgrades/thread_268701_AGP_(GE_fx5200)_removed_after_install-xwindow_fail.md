---
title: "AGP (GE fx5200) removed after install-xwindow fails"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by thevikas on 2006-09-30
Hi,

I had installed my ununtu and used it for a month. later, for some games i had to come back to my D845GBV graphics so i removed the AGP card. 
ubuntu fails to start xwindows. now, i don't know how to run the ubuntu hardware checker so it can detect and install required drivers with the new graphic hardware it detectes at startup.

the console is running just fine.

thanks,
vikas
IN

---

### Post by Iarwain ben-adar on 2006-09-30
Hi,
try this
```
sudo dpkg-reconfigure xserver-xorg
```


Iarwain

---

