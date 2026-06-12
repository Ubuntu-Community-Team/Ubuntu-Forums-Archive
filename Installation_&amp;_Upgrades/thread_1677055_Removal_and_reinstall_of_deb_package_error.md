---
title: "Removal and reinstall of deb package error"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by RebeccaB37 on 2011-01-28
Hello all

Using the Package Installer I installed a .deb from opticks.org. The software didn't work (not listed in menu and wouldn't boot from terminal). I tried reinstall without success so I now wish to remove the package completely.

Unfortunately I get the following error

sudo dpkg -r opticks
(Reading database ... 349373 files and directories currently installed.)
Removing opticks ...
rmdir: failed to remove `/opt/Opticks/Extensions/AutoInstall': No such file or directory
dpkg: error processing opticks (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 opticks

Synaptic recognises the package but will not allow the full removal (quits with same error). I have also tried to reinstall the package using a fresh download from the site but this ends with the same error.

Does anyone have any ideas what to try next?

Thanks for reading,
Rebecca

Ubuntu Lynx 10.04 64bit
Dell Inspiron 1525

---

### Post by sikander3786 on 2011-01-28
It is complaining for a non-existing directory. I wonder if creating that directory would play with dpkg and solve the issue.

```
sudo mkdir -p /opt/Opticks/Extensions/AutoInstall
```

```
sudo dpkg -r opticks
```

---

### Post by RebeccaB37 on 2011-01-28
total genius, I love it when the answer is simple! thank you :)

---

