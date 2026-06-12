---
title: "apache read error on ubuntu 10.04"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by luftadler on 2010-05-04
Hi all, 

I've just install Ubuntu 10.04 on my machine and I have a problem with apache, when i try to browse localhost I get this error 

> Forbidden

You don't have permission to access / on this server.
Apache/2.2.14 (Ubuntu) Server at localhost Port 80

I now that is an old problem, but i didn't find a working solution on web.


Regards,
Cristian

---

### Post by luftadler on 2010-05-04
Here is a part from apache log file

> [Tue May 04 12:08:18 2010] [error] [client 127.0.0.1] (13)Permission denied: cannot read directory for multi: /home/user/public_html/
[Tue May 04 12:08:18 2010] [error] [client 127.0.0.1] (13)Permission denied: cannot read directory for multi: /home/user/public_html/

Cristian

---

### Post by luftadler on 2010-05-07
Resolved, it was permission error of public_html directory.

---

