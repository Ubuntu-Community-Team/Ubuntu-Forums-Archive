---
title: "Upgrade from 11.10 to 12.04 failed , N00b Needs Help :)"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by audioaddictz on 2012-04-28
ok i ran the update manger last night and checked for updates 

when it had finished checking it told me there was an upgrade to 12.04 lts available

so i clicked the upgrade button , ticked the agrement box , and it started doing its thing

downloading various packages and such ... then my wifi droped offline and the process haltered telling me that my internet connection had failed

so i clicked ok , got my wifi back on 

opened the update manager and ... no option to upgrade is there now 

any one know how i get this to come back , or if there is a terminal command to restart / resume the upgrade process 

thanks in advance for any help

---

### Post by yo_bhan on 2012-04-28
alt+f2 and type
```
sudo update-manager -d
```

---

### Post by audioaddictz on 2012-04-28
> **yo_bhan said:**
> alt+f2 and type
```
sudo update-manager -d
```


that has not worked it seems , it brings up the update manager but there is still no option 
to upgrade to 12.04 anymore

---

