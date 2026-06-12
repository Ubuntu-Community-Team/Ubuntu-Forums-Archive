---
title: "synaptic package manager/software updater will not work."
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by tomasmekean on 2006-08-19
For some reason after I booted today it showed I had three updates available and when I started the software updater it wouldn't upgrade.  I then tried to start synaptic package manager and it wouldn't run.  I tried to search the net but didn't find an answer to my problem.

Can anyone help????  6.06 LTS Dapper Drake

Thanks,

Tomas

---

### Post by amgeex on 2006-08-19
Same problem here, Synaptic won't run AFTER installing updates... The software updater rus tho.

---

### Post by Piraat Bill on 2006-08-19
Same exact problem here, I wonder if it has to do with a recent update we downloaded.  If so, is there any way to uninstall updates?

---

### Post by IoCaster on 2006-08-19
Try this....

> sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4

From this thread ---> [http://www.ubuntuforums.org/showthread.php?t=238668](http://www.ubuntuforums.org/showthread.php?t=238668)

---

### Post by Piraat Bill on 2006-08-19
w00t! thanks!

---

