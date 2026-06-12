---
title: "change resolution before boot"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by lilmill on 2008-03-07
I have hooked my ubuntu machine up to another monitor that is smaller. Now when I boot the computer after and choose ubuntu from grub it starts to boot and I hear the startup chime but the monitor goes to sleep. I'm guessing it cannot display the set resolution. During install it was using a bigger monitor. The monitor seems to work fine if I choose xp from grub. Ps i'm a total noob with linux so please some detailed help

---

### Post by confused57 on 2008-03-07
> **lilmill said:**
> I have hooked my ubuntu machine up to another monitor that is smaller. Now when I boot the computer after and choose ubuntu from grub it starts to boot and I hear the startup chime but the monitor goes to sleep. I'm guessing it cannot display the set resolution. During install it was using a bigger monitor. The monitor seems to work fine if I choose xp from grub. Ps i'm a total noob with linux so please some detailed help
You could try booting into recovery mode & run:
```
dpkg-reconfigure xserver-xorg
```

---

