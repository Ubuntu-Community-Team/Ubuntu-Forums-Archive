---
title: "Apache issue after upgrading server to 16.04 LTS"
date: 2016-08-08
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2016-08-08
My two development websites cannot be accessed after my server upgrade from 14.04 LTS to 16.04 LTS.

The error I get in the browser is 
------------------------
setStart($startTime, $startMem)->mark('afterLoad') : null; // Instantiate the application. $app = JFactory::getApplication('administrator'); // Execute the application. $app->execute();
------------------------

The apache error log shows this before the upgrade
[HTML][Mon Aug 08 11:46:16.000181 2016] [:notice] [pid 4493] ModSecurity for Apache/2.7.7 (http://www.modsecurity.org/) configured.
[Mon Aug 08 11:46:16.000298 2016] [:notice] [pid 4493] ModSecurity: APR compiled version="1.5.1-dev"; loaded version="1.5.1-dev"
[Mon Aug 08 11:46:16.000319 2016] [:notice] [pid 4493] ModSecurity: PCRE compiled version="8.31 "; loaded version="8.38 2015-11-23"
[Mon Aug 08 11:46:16.000345 2016] [:warn] [pid 4493] ModSecurity: Loaded PCRE do not match with compiled!
[Mon Aug 08 11:46:16.000358 2016] [:notice] [pid 4493] ModSecurity: LUA compiled version="Lua 5.1"
[Mon Aug 08 11:46:16.000370 2016] [:notice] [pid 4493] ModSecurity: LIBXML compiled version="2.9.1"
[Mon Aug 08 11:46:17.001804 2016] [mpm_prefork:notice] [pid 4494] AH00163: Apache/2.4.7 (Ubuntu) OpenSSL/1.0.2g-fips configured -- resuming normal operations[/HTML]

While after the upgrade is shows
[HTML][Mon Aug 08 11:50:07.000672 2016] [:notice] [pid 8328] ModSecurity for Apache/2.9.0 (http://www.modsecurity.org/) configured.
[Mon Aug 08 11:50:07.000878 2016] [:notice] [pid 8328] ModSecurity: APR compiled version="1.5.1"; loaded version="1.5.2"
[Mon Aug 08 11:50:07.000893 2016] [:warn] [pid 8328] ModSecurity: Loaded APR do not match with compiled!
[Mon Aug 08 11:50:07.000911 2016] [:notice] [pid 8328] ModSecurity: PCRE compiled version="8.35 "; loaded version="8.38 2015-11-23"
[Mon Aug 08 11:50:07.000938 2016] [:warn] [pid 8328] ModSecurity: Loaded PCRE do not match with compiled!
[Mon Aug 08 11:50:07.000948 2016] [:notice] [pid 8328] ModSecurity: LUA compiled version="Lua 5.1"
[Mon Aug 08 11:50:07.000958 2016] [:notice] [pid 8328] ModSecurity: YAJL compiled version="2.1.0"
[Mon Aug 08 11:50:07.000986 2016] [:notice] [pid 8328] ModSecurity: LIBXML compiled version="2.9.2"
[Mon Aug 08 11:50:07.000996 2016] [:notice] [pid 8328] ModSecurity: Status engine is currently disabled, enable it by set SecStatusEngine to On.
[Mon Aug 08 11:50:08.003969 2016] [mpm_prefork:notice] [pid 8339] AH00163: Apache/2.4.18 (Ubuntu) OpenSSL/1.0.2g-fips configured -- resuming normal operations [/HTML]


Not sure if this causes my problem, but appreciate any pointers.

---

### Post by lister171254 on 2016-08-08
After cross posting the issue in the Joomla forum, here is the solution


> Thanks for your help. Looks like the upgrade also upgraded php to php7, without upgrading/installing the relevant php modules. I followed your suggested link [http://idroot.net/linux/install-joomla-ubuntu-16-04/](http://idroot.net/linux/install-joomla-ubuntu-16-04/) and installed the needed modules:
sudo apt-get install php7.0-mysql php7.0-curl php7.0-json php7.0-cgi php7.0 libapache2-mod-php7.0 php7.0-mcrypt

Everything works (again).


Not sure if this should be raised as an upgrade bug
L

---

