---
title: "aptitude, see installed packages"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by Pasdar on 2010-01-24
The last upgrade I did installed a package which has ruined my kubuntu. Since I don't know the exact package name, I don't know which one to uninstall. How can I see a list of installed packages (in terminal)? Preferrably I could see them by date installed, so I can uninstall the last packages. I think it has to do with the package called Intel aes or something...

---

### Post by Pasdar on 2010-01-24
I figured it out.

cat /var/log/aptitude
show the log for installed/removed/upgraded packages. You can send it to a file to check it out by: cat /var/log/aptitude > /path/to/file

then check that file.

---

### Post by oldos2er on 2010-01-24
Run **aptitude** in a konsole, click Package, Cycle Package Information, and it should offer to show you a list of installed packages.

---

