---
title: "java trouble"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by asif_1088119 on 2010-01-02
hi
i have mozilla 3.0.8 in my ubuntu 9.04 & i cannot configure java in firefox.so when i check in the website of java that if i hav proper java installed or not they say i dont have any proper version installed.but i checked from synaptic that i have java 1.6.0 installed.so what to do??
moreover,i cannot browse [www.smeet.com](www.smeet.com) full functionally.

---

### Post by asif_1088119 on 2010-01-02
is there anyone to reply please??

---

### Post by jonest1 on 2010-01-02
I do not have a 9.04 system handy, but you do need to check and see if the java browser plugin is installed.

In Firefox, type about:plugins into the URL bar and you will get a listing of your plugins to which Firefox is aware.  You should see something similar to 'Java(TM) Plug-in 1.6.x...'.  Again, your exact text may be different than mine.

If it is not there, you need to install the plugin.  On Ubuntu 9.10, the java plugin package is titled sun-java6-plugin and may be the same in 9.04. You can search for it using synaptic and install away.  You will probably have to restart Firefox.

If you already have it installed, you may want to uninstall it and re-install it.  This too can be done through synaptic by right-clicking on the package name and choosing from the menu.

---

