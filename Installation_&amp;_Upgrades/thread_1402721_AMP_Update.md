---
title: "AMP Update?"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by italianoman421 on 2010-02-09
My computer runs Karmic and has quit booting when it is plugged in. I was told it was the AMP needing updated. How do I do that? I do the updates from the update manager, does this mean I missed the AMP update or is it done differently than through the update manager. 

Thanks

---

### Post by julianb on 2010-02-09
You might want to be more specific. Apache-MySQL-PHP are often used together and can be referred to as AMP (or more commonly LAMP when used with linux).

A failure in any of the "AMP" components generally can't cause your computer to fail to boot.

Apache-MySQL-PHP are updated the same ways that other Ubuntu software is updated. If you are not sure whether they are up-to-date, you may enter these two lines using Terminal

```
sudo apt-get update
```
(enter password and wait until it's finished
```
sudo apt-get upgrade
```

---

