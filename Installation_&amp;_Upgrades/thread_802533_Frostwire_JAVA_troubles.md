---
title: "Frostwire JAVA troubles"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by Ellypho on 2008-05-21
Hello everyone. I appear to have a problem installing frostwire on my machine the terminal message is posted below

Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

Any ideas?

---

### Post by Pumalite on 2008-05-21
Try:
sudo aptitude install ubuntu-restricted-extras

---

