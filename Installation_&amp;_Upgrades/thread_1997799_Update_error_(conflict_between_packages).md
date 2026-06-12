---
title: "Update error (conflict between packages)"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by soralalp on 2012-06-05
When I tried to install the recent updates, update manager gave me the following error. What should I do?


The following packages have unmet dependencies:

libmx-1.0-2: Depends: libmx-common (= 1.4.6-1ubuntu1~precise1) but it is not installed
             Depends: libc6 (>= 2.14) but 2.15-0ubuntu10 is installed
             Depends: libclutter-1.0-0 (>= 1.7.6) but 1.11.3+git20120515.1f7ff75a-0ubuntu1~12.04~ricotz0 is installed
             Depends: libcogl9 (>= 1.7.4) but 1.11.1+git20120419.2ab017bb-0ubuntu1~12.04~ricotz0 is installed
             Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.26.1-1 is installed
             Depends: libglib2.0-0 (>= 2.31.8) but 2.33.1+git20120603.51e6edf0-0ubuntu1~12.04~ricotz0 is installed
             Depends: libgtk2.0-0 (>= 2.20.0) but 2.24.10-0ubuntu6 is installed
             Depends: libpango1.0-0 (>= 1.18.0) but 1.30.0-0ubuntu2 is installed
             Depends: libxrandr2 (>= 2:1.2.99.2) but 2:1.3.2-2 is installed

---

### Post by l3addy on 2012-06-06
had same problem. 
seems like 
```
sudo apt-get install -f
```
helped me.

---

