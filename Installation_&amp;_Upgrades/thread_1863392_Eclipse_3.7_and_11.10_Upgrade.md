---
title: "Eclipse 3.7 and 11.10 Upgrade"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by avrono on 2011-10-17
All, 

I had a very nice working version of Eclipse 3.7 with WDT. I then upgraded to Ubuntu 11.10 and Eclipse seems to have lost some dependencies and non of the web tools (like JSP editor and launching tomcat) would work. 

I tried re-installing the WDT from the repository, and kept getting a dependency error. I then nuked the install and re-installed Eclipse from the 11.10 repository -- same issue.

Finally, the only way to solve the problem was to download the Eclipse Tarball and do a manual install. I have not investigated this issue fully, but seems as if something is broken in the 11.10 Eclipse package. Furthermore a previously working Eclipse in 11.04 might break when you upgrade ...

Any ideas what is going wrong for future reference ?

_av

---

### Post by lovinglinux on 2011-10-17
No idea, but I use Eclipse tarball instead of the one from the repositories. Works fine for me and I don't need to install all the plugins again after a clean install (I never do distro upgrades). 

I recently moved to Aptana, which is based on Eclipse and it is working fine on 11.10.

---

### Post by s-valley on 2011-10-24
I too have problem with eclipse after the upgrade. 

[http://ubuntuforums.org/showthread.php?t=1859995](http://ubuntuforums.org/showthread.php?t=1859995)

I have problem with my mail also.  evolution is broken after the upgrade.  11.10 may be the killer of ubuntu desto.  A friend of mine moved to fedora after 11.10 broke his mail.

---

