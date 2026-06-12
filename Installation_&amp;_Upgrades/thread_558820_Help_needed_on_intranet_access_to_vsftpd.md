---
title: "Help needed on intranet access to vsftpd"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by rodkar on 2007-09-24
Hi,

I am new to Linux. I have setup a Ubuntu 7.04 desktop with LAMP on an old laptop. I can access the Apache server and MySQL server from computers inside my network at home. Before I made any changes to the vsftps.conf file, I could login as anonymous from other computers. I want to login as a user to upload files for the web server so I had made the following changes:

anonymous_enable=NO
local_enable=YES
write_enable=YES

After I restarted the server, I could no longer login via ftp. Everytime I try, it says Connection Refused.

Please advise.

Thanks.

Roderick

---

