---
title: "How to install MATLAB"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by mahmoodn on 2011-01-12
Hi,
I want to install matlab 2009b on amd64 machine, however at the beginning of installation, I get some errors about awk.cmd:
```
root@server:/opt/Matlab2009b# sh /mnt/install -t
awk: cmd. line:2:       BEGIN { found = 0; extra = 9; min = 24; default = 24 }
awk: cmd. line:2:                                               ^ syntax error
awk: cmd. line:6:                   if (nrows < min) nrows = default
awk: cmd. line:6:                                            ^ syntax error
awk: cmd. line:12:      END { if (found == 0) print (default - extra) }
awk: cmd. line:12:                                   ^ syntax error
awk: cmd. line:12:      END { if (found == 0) print (default - extra) }
awk: cmd. line:12:                                                    ^ syntax error
awk: cmd. line:2: (FILENAME=- FNR=1) fatal: division by zero attempted in `%'
[: 582: -le: argument expected

```
What does that mean? I don't have X.

---

