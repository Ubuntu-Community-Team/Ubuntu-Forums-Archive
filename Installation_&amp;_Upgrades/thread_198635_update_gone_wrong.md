---
title: "update gone wrong"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by osiris999 on 2006-06-17
so after i finally got compiz and automatrix installed everything was going fine till my system said there was new updates. after installing them and re booting right before the login screen comes up it goes to terminal mode. says x server is missing or not working. how can i fix this. i did sudo dpkg-reconfigure xserver-xorg and tried to reinstall it but really have no idea what im doing so it failed.

---

### Post by raptros-v76 on 2006-06-17
```
 sudo aptitude update&&sudo aptitude install xserver-xorg
```

---

