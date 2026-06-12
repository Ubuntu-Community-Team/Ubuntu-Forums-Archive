---
title: "open office gone?"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by not_yet on 2006-06-01
after dapper upgrade open office seems to be gone:confused:

---

### Post by ash211 on 2006-06-01
If you upgraded by changing the /etc/apt/sources.list file from breezy to dapper, it may not have correctly updated the entire desktop correctly.  Run ```
sudo apt-get update
``` and then either ```
sudo apt-get install ubuntu-desktop
``` or ```
sudo apt-get install kubuntu-desktop
``` depending on whether you're using Ubuntu or Kubuntu.

If that doesn't work and you just want to have open office back again, run ```
sudo apt-get install openoffice.org
```

---

