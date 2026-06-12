---
title: "problems with update manager"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by nynoah on 2007-08-28
I am having some problems with my update manager.  I have been having this for a little while.  I am wondering if I have some conflicting programs.  

I ran sudo dpkg configure a    and this is what I got.......
> noah@noah-desktop:~$ sudo dpkg --configure -a
Password:
Setting up phpgroupware (0.9.16.011-3) ...
setting up apache
setting up apache-ssl
setting up apache-perl
setting up apache2
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
dpkg: error processing phpgroupware (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of phpgroupware-dj:
 phpgroupware-dj depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-dj (--configure):
 dependency problems - leaving unconfigured
Setting up libpoppler1 (0.5.4-0ubuntu8.1) ...

Setting up poppler-utils (0.5.4-0ubuntu8.1) ...
Setting up libpoppler1-glib (0.5.4-0ubuntu8.1) ...

Setting up libpoppler1-qt (0.5.4-0ubuntu8.1) ...

Errors were encountered while processing:
 phpgroupware
 phpgroupware-dj
noah@noah-desktop:~$   

Can anyone tell me what I need to get rid of and how?


Also I can not run my update manager becuase it is telling me another process is using it.  But I have no clue what?

Thanks
Noah

---

### Post by DagonSphere on 2007-09-25
Are you using phpgroupware?  If not, I would remove it, and try again.

---

