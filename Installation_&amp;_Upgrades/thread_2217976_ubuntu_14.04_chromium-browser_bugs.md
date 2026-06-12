---
title: "ubuntu 14.04 chromium-browser bugs"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by jhay2 on 2014-04-19
i recently upgraded my distros from 13.10 to 14.04 

upgrading works fine 

but the latest chromium-browser seems very buggy

at first run it was fine but after awhile typing at url bar or any input forms were stop working 


and from terminal i'd saw this output

[24645:24645:0419/162528:ERROR:browser_main_loop.cc(240)] Gdk: gdk_window_set_user_time called on non-toplevel

sorry for my bad english . 

is there any fix for this ?

---

### Post by bapoumba on 2014-04-19
May be this ?
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1308125](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1308125)
[https://code.google.com/p/chromium/issues/detail?id=360388](https://code.google.com/p/chromium/issues/detail?id=360388)

---

### Post by jhay2 on 2014-04-19
it seems that the bugs is only on chromium-browser 34 to 36 

so the quick fix is to remove chromium-browser

and replace it with google chrome latest version which is version 34 


and thats solved my problem ^^

---

### Post by bapoumba on 2014-04-19
Glad to see you found a working solution :)

---

