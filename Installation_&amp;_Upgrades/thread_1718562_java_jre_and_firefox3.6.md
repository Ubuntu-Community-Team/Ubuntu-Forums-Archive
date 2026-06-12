---
title: "java jre and firefox3.6"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by rbramley on 2011-03-31
I am trying to get firefox to see java jre 1.6.024 and in particular the libnpjp2.so file.
I have followed the instructions on the java website and linked this file from /usr/lib/mozilla/plugins but firefox cannot pick it up. Does anyone know why this could be?

I did some stuff previously with nswrapper to get something to work but I do not really understand what it does.

---

### Post by TBABill on 2011-03-31
Java is in the repos and it's version 1.6. Why not just go into Synaptic, mark the Java Plugin for installation and let Apt/Synaptic pull in the dependencies and take care of the rest? Takes just seconds to do. 
 
One caveat to installing java: a default install of Ubuntu comes with openJDK and the icedtea plugin. Mark those for complete removal and then install Sun java for a smooth transition. I do this on every new install of Ubuntu that I do because the icedtea plugin doesn't work well with some sites.

---

