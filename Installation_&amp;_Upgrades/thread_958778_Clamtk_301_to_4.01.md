---
title: "Clamtk 301 to 4.01"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by Terry19 on 2008-10-25
hi, I have clamtk 3 and i want to upgrade to 4, no as u all probably know the update option that comes with the program never works. Anyway i downloaded the tar.gz clamtk 4.01 and have no idea how to update or install from there. [email]terryk_tv@hotmail.com[/email]

---

### Post by cariboo on 2008-10-25
Clamtk is only the gui interface to clamav, it won't update the anti-virus program. To keep your virus definitions up to date run in a terminal:

```
sudo freshclam
```

Clamav only scans for Windows viruses, so keeping your definitons up to date is more important than having the latest gui.

Jim

---

