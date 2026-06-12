---
title: "Display problem"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Shmifty on 2007-04-20
I upgraded to Feisty from Edgy last night and now I am unable to boot Feisty from any kernel because the display is not working correctly. Should I reconfigure X or try to start it manually (if so I need the codes as I don't mess with X much)?

---

### Post by taurus on 2007-04-20
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

