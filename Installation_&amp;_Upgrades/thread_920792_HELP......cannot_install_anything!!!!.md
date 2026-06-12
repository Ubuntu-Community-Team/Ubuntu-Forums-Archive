---
title: "HELP......cannot install anything!!!!"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by orIONX on 2008-09-15
I'd tried installing second life from the .deb available at getdeb.com
for some reason the install broke and now i cannot install anything or even upgrade.......please help
the following is the output i get when i try upgrading

orion@X:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.

---

### Post by Partyboi2 on 2008-09-15
Open a terminal and try[FONT=monospace]
[/FONT]```
sudo dpkg --remove --force-remove-reinstreq secondlife-install
```

---

### Post by orIONX on 2008-09-16
thankyou very much...... it works!!!

---

