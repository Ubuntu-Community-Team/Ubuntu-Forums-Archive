---
title: "Error after upgraded from 7.10 to 8.04"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by alya84 on 2008-05-08
Hello all, i got this error when in the middle of upgrading my ubuntu 7.10 to 8.04.


gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on file-roller; however:
  Package file-roller is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 file-roller
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

now, whatever i do it in terminal will end with that lines and my programs start to crash when i try to open it. Anyone here could help me with these error?

---

### Post by iaculallad on 2008-05-08
If you backed-up your important files prior to your upgrade to 8.04, I suggest that you do a clean install. That would solve the problem.

---

### Post by alya84 on 2008-05-08
is there any other option before clean install? actually..i did clean install with 7.10 then upgrade to 8.04 right after finished 7.10 clean install...im afraid it will happen again if i make clean install..

---

### Post by iaculallad on 2008-05-08
Why would you want to do a installation of 7.10 then upgrade it with 8.04? Many had complained about errors from upgrading to 8.04 from 7.10, let's learn from them. Just give 8.04 a clean install.

---

