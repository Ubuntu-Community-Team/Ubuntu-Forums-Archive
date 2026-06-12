---
title: "Ignroing File ... Invalid Filename Ext."
date: 2017-04-03
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2017-04-03
Get this message at the end of updating. Seen it on several computers after installing Xubuntu v16.04. It shows;

> Processing Triggers for dbus ....
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/'
as it has an invalid filename extension.


Any ideas why this is showing up? And why is there "auto-upgrades" anyway? Sounds like a security risk!

Rick

:popcorn:

---

### Post by Dennis N on 2017-04-04
I renamed it to **x20auto-upgrades-ucf-dist** and system perhaps will not try to use it, but if problem persists, looks ok to just delete. 

More here:
[http://askubuntu.com/questions/850793/apt-update-message-etc-apt-apt-conf-d-20auto-upgrades-ucf-dist-invalid-file](http://askubuntu.com/questions/850793/apt-update-message-etc-apt-apt-conf-d-20auto-upgrades-ucf-dist-invalid-file)

Edit:
Looking at the two files again, one of the settings in that file conflicts with the correct setting in 20auto-upgrades, so to prevent this I am deleting 20auto-upgrades.ucf-dist. Done.

---

### Post by Rick St. George on 2017-04-04
I concur ... Remove it with;

```

sudo rm /etc/apt/apt.conf.d/20auto-upgrades.ucf-dist

```

Thanks - Case Closed.

---

