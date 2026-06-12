---
title: "apache2 Unclean shutdown"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by its_joy on 2008-03-19
Hello,

We have unbuntu server with apache2  and php 5. After restarting the apache service we get the following result

[Wed Mar 19 12:02:25 2008] [notice] caught SIGTERM, shutting down
[Wed Mar 19 12:02:26 2008] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Wed Mar 19 12:02:27 2008] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Wed Mar 19 12:07:26 2008] [notice] caught SIGTERM, shutting down
[Wed Mar 19 12:09:42 2008] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Wed Mar 19 12:09:42 2008] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations


Please give us the solution for this issue. 

its_joy

---

### Post by dthacker on 2008-03-19
We need more info.

What user are you starting apache as?  
What is the exact command you are using to start apache2?
What user does apache2 run as in your environment?

---

### Post by jaripetteri on 2008-06-01
Did you fix this? I have same problem here. My server went down because power lost and after that webserver is not running anymore. Any advice?

---

