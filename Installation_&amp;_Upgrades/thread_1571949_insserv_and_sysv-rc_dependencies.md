---
title: "insserv and sysv-rc dependencies"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by utopyr on 2010-09-10
I upgraded a server installation from 8.04 to 10.4, but get this one nagging message when I update now:
```
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  insserv: Breaks: sysv-rc (< 2.87dsf-3) but 2.86.ds1-14.1ubuntu45 is installed
E: Unmet dependencies. Try using -f.

```

Using -f doesn't take care of it. I've tried ```
dpkg --purge remove sysv-rc
``` but nothing, autoremove, and so on, but this persists. Any suggestions?

---

