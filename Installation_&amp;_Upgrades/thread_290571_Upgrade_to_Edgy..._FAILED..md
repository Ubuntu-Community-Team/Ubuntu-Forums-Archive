---
title: "Upgrade to Edgy... FAILED."
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by eighthate on 2006-11-01
Hey, I just upgraded to edgy eft, after rebooting the computer it gave me an error message concerning X. I reconfigured it but it refused to save the configuration file cause of an already existing one.. I<m sure this is my problem but how can i solve it? thanks

---

### Post by taurus on 2006-11-01
Did you remember to run it with sudo, i.e.,

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by eighthate on 2006-11-01
yeah i tried and it said after all my configuration:
xserver-xorg postinst warning, overwriting possibly customized configuration file..


i tried a lot of things to repair but none worked..

---

