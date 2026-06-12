---
title: "ASUS GTX560 Ti DirectCU II card driver finding issue on Ubuntu 10.10 64-bit version."
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by KingHanco on 2011-03-29
Anyone know why Ubuntu 10.10 64-bit can't find and can't install Nvidia driver fully for this?

Problem is that Ubuntu 10.10 64-bit can't install Nvidia fully. Missing something that Ubuntu 10.10 64-bit doesn't have.

I already try these commands. But after reboot the screen take me to the typing screen instead of the Ubuntu 10.10 64-bit sign in screen.

sudo apt-get install nvidia-current

sudo nvidia-xconfig

Can anyone help me please?

---

### Post by KingHanco on 2011-03-30
Forget about all that. Here the real fix. Just this code is all you need. Add it and then run updates. Reboot. Then install the video card drivers from your Ubuntu.

```
ppa:ubuntu-x-swat/x-updates
```

---

