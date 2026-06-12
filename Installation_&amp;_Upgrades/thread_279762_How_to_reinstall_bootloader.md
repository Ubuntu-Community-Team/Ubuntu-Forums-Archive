---
title: "How to reinstall bootloader?"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by meatball117 on 2006-10-18
Hey, I was an idiot and reinstalled windows xp on my master hdd, and it removed the bootloader that was originally put there for ubuntu, (which is on my slave drive). Is there a (relatively small download) way to get this bootloader back on there? 

Thanks in advance!

---

### Post by adwait on 2006-10-18
Fire up Ubuntu from the LiveCD installer and use
```
sudo grub-install /dev/hda
```

---

