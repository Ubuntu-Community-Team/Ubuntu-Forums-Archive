---
title: "Installing a new machine on an NIS network"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by dallingham on 2007-10-10
Linux is extremely popular in the VLSI design field. In fact, these days, you practically have to run Linux in order to get your job done. The standard setup in most companies doing this is to have an NIS server managing accounts/passwords, and having all home directories on a network server.

NIS is common, because many of these networks also have Solaris or HPUX machines on them as well.

Red Hat has made this process very easy. During install, you can specify your NIS server, and the install handles all the details of setting up NIS. Similarly, you can specify you /home/ directory to be on a network drive during install. 

Is there an way to do the same under Ubuntu? So far, the process has proven to be rather difficult. NIS has to be installed, the /etc/passwd and /etc/group files have to be modified by hand, the /home directory has to be mounted. This is complicated by the fact that the user created during install has its account under /home. And we don't even want this user, because all users should be from the NIS server.

Any suggestions on how to make the setup easier? Is there a way to do this during install?

---

