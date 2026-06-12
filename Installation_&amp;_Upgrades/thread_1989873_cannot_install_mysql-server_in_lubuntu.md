---
title: "cannot install mysql-server in lubuntu"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by lortech on 2012-05-28
I am trying to install zoneminder and it was getting this error when trying to install mysql-server

server-5.1_5.1.62-0ubuntu0.11.04.1_i386.deb: subprocess new pre-installation script returned error exit status 1

I tryed uninstalling and reinstalling mysql server and got the same error. Did a Google search and came up empty. What do I need to get beyond this so I can get zone-minder installed?


Thanks :)

---

### Post by mastablasta on 2012-05-29
try to use tasksel to install mysql server.

---

### Post by d_in_Conduct on 2012-05-29
I had almost the same problem installing MySQL on 12.04.  This morning I opened up synaptic and did a complete removal of all mysql selections.  After all were removed I went back and only checked the mysql-server and mysql-client entries that had numbers after them and accepted the dependencies it wanted to load.  Yours will probably be something like mysql-server-5.1.  I also checked the -core entries for both of those.  The installation(s) went fine.

---

