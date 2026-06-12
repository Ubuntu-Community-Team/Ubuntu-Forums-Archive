---
title: "Help, Adept is stuck ?!?!"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by mips on 2006-06-05
Was using adept to install a whole bunch of stuff. It downloaded the stuff but got stuck on the java install where it prompts you to accept the license conditions. I had to kill the process. I rebooted but i still cannot run adept and get following error although i have none of the listed processes running.

```
Read Only mode: Database Locked - Adept Manager
You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.
```

---

### Post by mips on 2006-06-05
Problem fixed, had to do a:
**# sudo dpkg --configure -a**

---

