---
title: "Apache Version Discrepancy"
date: 2014-10-23
forum: Installation &amp; Upgrades
---

### Post by short-timer on 2014-10-23
Using 12.04 LTS; checking Apache version against a reported vulnerability that was fixed in [2.2.22-1ubuntu1.7]("https://launchpad.net/ubuntu/+source/apache2/2.2.22-1ubuntu1.7"), the response from 'apachectl -v' (same as 'httpd -v') is

    Server version: Apache/2.2.21 (Unix)

But 'dpkg -l | grep apach` yields:

ii  apache2                                       2.2.22-1ubuntu1.7                               Apache HTTP Server metapackage
ii  apache2-mpm-prefork                           2.2.22-1ubuntu1.7                               Apache HTTP Server - traditional non-threaded model
ii  apache2-utils                                 2.2.22-1ubuntu1.7                               utility programs for webservers
ii  apache2.2-bin                                 2.2.22-1ubuntu1.7                               Apache HTTP Server common binary files
ii  apache2.2-common                              2.2.22-1ubuntu1.7                               Apache HTTP Server common files

Why does the daemon report --.21?

-R

---

### Post by bashiergui on 2014-10-25
Not really sure why, but when listing software versions using <name> -v or --version, it doesn't report precise results.

The dpkg method yields precise versions installed on your system.

---

### Post by short-timer on 2014-10-31
Aha! After upgrading to Ubuntu 14.04, the new Apache makes the distinction stark. It now deploys **apache2** instead of **httpd**. Now `apache2 -v' displays "Apache/2.4.7" which jibes with the **dpkg** output. 

But... now I note the the rc#.d/ directories still contain symlinks to the old **apachectl** script that runs **httpd** as well as the **apache2** script that runs **/usr/sbin/apache2**.. I don't know why **httpd** and **apache2** aren't both running because of that, but **httpd** does not appear as a running daemon. I suppose next step is using 'update-rc.d' to eliminate the old startup script from the rc#.d/ directories...

---

### Post by Doug S on 2014-10-31
I suspect that you had something messed up and non-standard in your 12.04 server. It has, at least partially, sorted itself out when you upgraded to 14.04.
There never was an httpd daemon in 12.04. Here is what I get on my 12.04 server:```
doug@doug-64:~$ [COLOR=#ff0000]apachectl -v[/COLOR]
Server version: Apache/2.2.22 ([COLOR=#ff0000]Ubuntu[/COLOR])
Server built:   Jul 22 2014 14:35:25
doug@doug-64:~$ [COLOR=#ff0000]httpd -v[/COLOR]
No command 'httpd' found, did you mean:
 Command 'xttpd' from package 'xtide' (universe)
httpd: command not found
doug@doug-64:~$ [COLOR=#ff0000]apache2 -v[/COLOR]
Server version: Apache/2.2.22 (Ubuntu)
Server built:   Jul 22 2014 14:35:25
``` The key what you were getting being wrong is this:```
Server version: Apache/2.2.21 ([COLOR=#ff0000]Unix[/COLOR])
```> **short-timer said:**
> Aha! After upgrading to Ubuntu 14.04, the new Apache makes the distinction stark. It now deploys **apache2** instead of **httpd**.It didn't use httpd for 12.04 either.

---

