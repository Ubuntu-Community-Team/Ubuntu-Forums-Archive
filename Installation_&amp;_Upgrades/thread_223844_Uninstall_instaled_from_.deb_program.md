---
title: "Uninstall instaled from .deb program"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by igrachev on 2006-07-27
Hello i got two questions the first is

Where is the default directory where wget store the downloaded packages (i mean where i can find asd.deb if i dl it with terminal like this wget -c htpp://.../.../asd.deb

and the second is while i depakage the .deb package how shall i uninstall it ? 

Thanks.

---

### Post by aysiu on 2006-07-27
*wget* will download to wherever you are when you type the command.

So if you're in /home/igrachev when you type *wget*, the file will download to your home directory.

If you're in /home/igrachev/Desktop, it will download to your desktop.

To uninstall a .deb, use *aptitude* or Synaptic or Adept. ```
sudo aptitude remove packagename
```

---

