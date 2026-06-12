---
title: "Setup CodeIgniter in ubuntu 13.04"
date: 2013-11-11
forum: Installation &amp; Upgrades
---

### Post by therealsam on 2013-11-11
I am using a fresh CodeIgniter installation on apache2.
Using **[http://localhost:8080/codeigniter](http://localhost:8080/codeigniter)** doesn't display anything. On checking firebug it displays a 500 internal server error.
I checked the apache logs for errors and it shows me this,

[Mon Nov 11 13:11:43 2013] [error] [client 127.0.0.1] PHP Warning:  require_once(/var/www/codeigniter/system/core/CodeIgniter.php): failed to open stream: Permission denied in /var/www/codeigniter/index.php on line 202

[Mon Nov 11 13:11:43 2013] [error] [client 127.0.0.1] PHP Fatal error:  require_once(): Failed opening required '/var/www/codeigniter/system/core/CodeIgniter.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/codeigniter/index.php on line 202

The line 202 of index.php is
**require_once BASEPATH.'core/CodeIgniter.php';**

where BASEPATH is 
**define('BASEPATH', str_replace("\\", "/", $system_path));**

and system_path is,
**$system_path = 'system';**

Since this is a fresh installation I have not messed around with anything except change the main folder name from CodeIgniter_2.1.4 to codeigniter.
I have been working with CI on windows and it works perfectly there.

regards.

---

