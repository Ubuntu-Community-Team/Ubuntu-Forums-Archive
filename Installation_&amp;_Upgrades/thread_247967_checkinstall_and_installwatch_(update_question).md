---
title: "checkinstall and installwatch (update question)"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2006-08-31
I just run apt-get -s upgrade and found that I had to remove installwatch in order to update checkinstall. installwatch was a dependency of checkinstall prior to this update. 

do you think this is a bug / error in packaging, or just usual business?

---

### Post by Jengist on 2006-08-31
I noticed the same thing when I upgraded but I checked the dependency tab in Synaptic and it says checkinstall replaces installwatch altogether and that now they will actually conflict with each other. So, nothing funny going on I guess.

---

### Post by emperor on 2006-09-05
[COLOR=#000000]"Installwatch is now part of (included in) the [CheckInstall]("http://asic-linux.com.mx/%7Eizto/checkinstall") distribution".

[http://asic-linux.com.mx/~izto/checkinstall/installwatch.html](http://asic-linux.com.mx/~izto/checkinstall/installwatch.html)
[/COLOR]

---

