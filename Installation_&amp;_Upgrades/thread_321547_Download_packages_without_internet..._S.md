---
title: "Download packages without internet... :S"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by Ezabel on 2006-12-19
Hi,
I've gone home for the christmas holiday and it so happens that my parents have this ancient modem to connect to the internet. To be able to install this modem on my Ubuntu laptop I need to download a couple of packages (gcc and libc6-dev), but since the modem is not yet working I am kinda stuck...](*,) 
Does anyone happen to know if you can install packages without an internet connection? Can I get them from the installation cd? Or can I download them on another comp and transfer them by usb and tell Ubuntu to install from there? 
Thanks for your help :)!!

---

### Post by pay on 2006-12-19
> **Ezabel said:**
> Or can I download them on another comp and transfer them by usb and tell Ubuntu to install from there? Yes. Just install the package with ```
sudo dpkg -i packagename.deb
```

---

### Post by Ezabel on 2006-12-19
That worked very well, thanks a lot! Am now connected from my laptop :)!

---

