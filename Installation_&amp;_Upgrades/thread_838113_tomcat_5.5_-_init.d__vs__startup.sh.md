---
title: "tomcat 5.5 - init.d  vs  startup.sh"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by hk47xx on 2008-06-23
Hi all, I've been having problems, with certains web application.

The thing is: if I start tomcat using "/etc/init.d/tomcat5.5 start",
the webapp start to throw severals exceptions like
"NoClassDefFoundError" among others, BUT if I start tomcat
with "/usr/share/tomcat5.5/bin/startup.sh", none of the mentioned problems raises.

So, I guess my questions are: 
[LIST]
[*]What am I missing?
[*]    If this a bug?
[*]    Or, It's just a 'user' error
[/LIST]

Any hints are very welcome!

If needed more information, just ask

[LIST]
[*]Ubuntu 8.04
[*]2.6.24-19-generic
[*]Tomcat 5.5 from official repositories
[*]java version "1.5.0_15"
[/LIST]

---

