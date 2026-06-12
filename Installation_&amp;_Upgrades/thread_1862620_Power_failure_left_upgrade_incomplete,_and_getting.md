---
title: "Power failure left upgrade incomplete, and getting some weird issues."
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by bholzer on 2011-10-16
So I decided to upgrade my computer and my girlfriends as well. Mine went well, and so far I am enjoying 11.10. However, my girlfriend unplugged her computer and it died in the middle of the upgrade. Woops. 

When I power the laptop on, it gets stuck at various spots in the boot. It doesn't show errors, it just shows services like apache starting. If I alt+f1 to tty1, I can startx and everything seems to go well. However, when I get to gnome, things seem to be in between 11.04 and 11.1! I ran dpkg --configure -a and it ran for a while, but nothing seemed to be different after reboot. I updated and everything else I can think of, but I am stuck :(

---

### Post by zvacet on 2011-10-18
Try with 

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get -f install
```

---

