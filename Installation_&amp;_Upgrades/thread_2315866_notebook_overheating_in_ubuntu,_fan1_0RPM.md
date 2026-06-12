---
title: "notebook overheating in ubuntu, fan1 0RPM"
date: 2016-03-03
forum: Installation &amp; Upgrades
---

### Post by mark273 on 2016-03-03
I have installed ubuntu alongisde with windows 8.1 but my notebook is really loud and temperatures as super high while i 'm just browsing webpages on the internet.

Now basically when i do not do anything it's :
temp 1: 68-71                  min:54                max : All of them 85
physical id: 68-71          min:54
core 0: 67                     min:52
core 1: 68-69                min:51
core 2: 70                    min:53
core 3: 64                    min:52
temp1 : 60                  min:52

Laptop is really warm and especially loud, i do not have the same problem in windows even though termeratures are not optimal. In windows its around 56-58 all of them + notebook is not laud.
My specs:
lenovo ideaPad z50-70
GTX 980 4gb
intel i7 haschwell 4720 Hq
ubuntu 14 / windows 8.1

tlp-stat -t shows :
CPU temp               =    69 [°C]
Fan speed (fan1)       =     0 [/min]

I noticed in Psensor and also in another application that fan1 is at RPM:0 could this be the problem? I'll be thankful for all the help.



EDIT:
My friend got the same notebook , the same dual boot , and he has got temperatures around 45 at everything 
tlp-stat -t shows :
CPU temp               = 48 [°C]
Fan speed (fan1)       = ( unavaible )

---

