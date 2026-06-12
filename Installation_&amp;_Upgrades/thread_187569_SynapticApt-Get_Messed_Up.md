---
title: "Synaptic/Apt-Get Messed Up"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by rykel on 2006-06-03
Dear friend,

My system was accidentally shut off while Synaptic was doing a system upgrade, and now I cannot upgrade the OS.

The error message I get is:

[INDENT]sudo apt-get upgrade (OR sudo apt-get upgrade)
Reading package lists... Done
Building dependency tree... Done
E: The package fax4100lpr needs to be reinstalled, but I can't find an archive for it.
[/INDENT]

Any idea what I can do to repair the machine? Thank you!!

---

### Post by jjcv on 2006-06-03
You are caught between a rock and a hard place.

At this stage I think your best option is to reinstall from scratch.

---

### Post by catlett on 2006-06-03
Try reloading the cache and then using aptitude instead of apt-get ```
 sudo aptitude update
``````
sudo aptitude dist-upgrade
```

---

### Post by rcarring on 2006-06-04
sudo apt-get install fax4100lpr

sudo apt-get update

sudo apt-get dist-upgrade

---

### Post by rykel on 2006-06-13
Thanks for all the help... my friend went ahead and reinstalled Ubuntu Dapper Drake... so I never got the chance to see which solution worked.

Oh well.    ;)

---

### Post by JaymZZZ on 2006-08-04
worked for me

---

