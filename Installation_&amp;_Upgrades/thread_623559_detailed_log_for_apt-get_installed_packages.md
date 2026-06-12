---
title: "detailed log for apt-get installed packages  ?"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by keepsimple on 2007-11-26
Hi, 

I know that /var/log/dpkg.log   logs the apt-get install  in the package level.  Is there a log in the file level?

i.e.  how can I find out what exactly are the files installed by an "apt-get install <pkg>"  command ?  

Thanks in advance. 

Han

---

### Post by keepsimple on 2007-11-26
I think I got it.  Looks like  the log is under:

/var/lib/dpkg/info 

cheers.

---

