---
title: "Erros were encountered..."
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by cjmoretti on 2012-11-19
I have Ubuntu 12.04.1 LTS version (GNU / Linux 3.2.0-32-generic x86_64)
Today I update: Aptitude update in error
Aptitude get upgrade error:
Errors were encountered while processing:
* linux-image-3.2.0-33-generic
* linux-image-server
* linux-server

What can I do?

---

### Post by efflandt on 2012-11-19
"No space left on device" means that you are running out of drive space on something.  Do you have a separate /boot partition that is not big enough for all the kernels on it?

Does **df** show any partition using 95% or more of its space?

---

