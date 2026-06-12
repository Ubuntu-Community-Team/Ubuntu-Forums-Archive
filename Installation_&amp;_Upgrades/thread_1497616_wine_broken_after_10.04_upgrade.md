---
title: "wine broken after 10.04 upgrade"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by dillinger417 on 2010-05-30
wine client error:0: version mismatch 387/398.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?


Trying to use wine ( or winecfg etc) after update to 10.04 gets me this message.   I have tried uninstalling and I still get the message even before I reinstall.  What is strange is that even after uninstall it gives same message not, 'command not found' or a suggestion to install wine.  There is no wineserver running prior and $PATH = "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

wine --version = wine-1.1.42


Help!

tia

---

### Post by dillinger417 on 2010-05-30
ok so i guess there were old packages leftover

tried 'sudo apt-get remove wine' then 
tried 'sudo apt-get autoremove' and
tried 'sudo apt-get install wine' and that worked... until i tried 'sudo apt-get install wine-gecko' so apparently that package is obsolete... what is the new replacement if any???

also now 'wine --version' = wine-1.1.25-174-gb0f53e1

tia

---

