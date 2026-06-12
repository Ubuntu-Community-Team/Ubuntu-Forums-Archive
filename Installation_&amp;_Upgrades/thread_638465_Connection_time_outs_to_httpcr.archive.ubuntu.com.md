---
title: "Connection time outs to http://cr.archive.ubuntu.com/"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by sheds on 2007-12-12
Hey there. I recently tried to perform an upgrade using apt to my 7.10 installation. But i keep getting time outs when trying to reach [http://cr.archive.ubuntu.com/](http://cr.archive.ubuntu.com/). I can obviously comment them out in /etc/apt/sources.list, but i want those upgrades. And need them actually, the nvidia installer is complaining about some libraries and they are found there.

Is there some kind of problem with the site??? More than half of the entries in my sources.list file are related and need to be fetched from there, so i am kinda lost here.

Thanks in advance for the help.

---

### Post by yabbadabbadont on 2007-12-12
Edit your sources.list and remove the "cr." so that it is using "http://archive.ubuntu.com" and then run "sudo apt-get update".  That will switch it to the primary mirror.

---

