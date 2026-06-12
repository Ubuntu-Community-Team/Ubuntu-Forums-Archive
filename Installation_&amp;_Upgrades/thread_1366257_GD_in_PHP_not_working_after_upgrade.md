---
title: "GD in PHP not working after upgrade"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by msknight on 2009-12-28
Hi Folks,

I had a LAMP server running Hardy server for ages. I ran through all the upgrades to Karmic. Platform is 64bit.  Obviously, I had a bit of grief and sorted most issues out expect one...

The GD library in PHP 5 is not working through Apache.

I've read posts on the subject and tried lots of things, but none of it works.  phpinfo() reports that the GD library is installed and enabled. Even so, I've tried removing and re-installing it.

I've got a feeling that a configuration file somewhere has either changed or got overwritten.

I remember that some years ago, the automatic configuration of PHP in Apache was removed and PHP has to be enabled by hand, but PHP itself is working fine.

Any ideas please?

---

### Post by msknight on 2009-12-28
In case it helps, here is a section from the phpinfo()

```
apache2handler
Apache Version 	Apache/2.2.12 (Ubuntu)
Apache API Version 	20051115
Server Administrator 	webmaster@localhost
Hostname:Port 	127.0.1.1:80
User/Group 	www-data(33)/33
Max Requests 	Per Child: 0 - Keep Alive: on - Max Per Connection: 100
Timeouts 	Connection: 300 - Keep-Alive: 15
Virtual Server 	Yes
Server Root 	/etc/apache2
Loaded Modules 	core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_dir mod_env mod_mime mod_negotiation mod_php5 mod_setenvif mod_status 
```

---

### Post by msknight on 2009-12-28
SCRATCH THE REQUEST

Long story short ... I program a "drop calculator" for the L2J system.

I let someone else help me on the programming and there have been little surprises left for me along the way ... one of which is that he reprogrammed the GD routine to display fonts that were on his system, but no one elses.

I'm unpicking the mess now ... but I've found that the GD system itself IS working ... it was just the code that was broken.

Thanks for your patience.

---

