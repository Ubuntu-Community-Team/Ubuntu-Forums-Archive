---
title: "Can't boot anymore"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by crasherball on 2007-04-15
hi,
i got a lil huge problem in ubuntu feisty :p

i did an update about a week ago

since rebooting, ubuntu is not booting anymore

when i try recoverymode i get this:

```
check root = bootarg cat /proc/cmdline
or missing modules, devices:
cat /proc/modules ls /dev
ALERT! /dev/evms/hdb2 does
not exist. Dropping into shell!
```

can anybody tell me what that means? or who i can fix this? i rilly tried as much i could and with all i knew, but this is just to high for my noob-skills :p

---

### Post by bulldog on 2007-04-15
If you can get to the console and login try```
sudo aptitude update && sudo aptitude upgrade
```
It's possible you have a not working kernel update installed.

---

