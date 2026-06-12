---
title: "proftpd will not uninstall"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by jsaumer on 2007-06-01
Hello,

my proftpd installation went bad, the /etc/init.d/proftpd file is blank.  

I try and remove it with a apt-get remove proftpd and it comes back with a exit status 127 because of the /etc/init.d/proftpd being bad.

I try and install, same thing.

How do I completly blow it out of the water and reinstall it from scratch. I checked top, there is no instance of proftpd currently running.

---

### Post by rukuartic on 2007-06-01
Yeah. I've had problems with this too... Here's my init.d file if it'll help.

ruku

---

### Post by jsaumer on 2007-06-01
it worked :) thanks for the help!

---

