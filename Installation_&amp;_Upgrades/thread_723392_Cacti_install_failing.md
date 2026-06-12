---
title: "Cacti install failing"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by pot_roast on 2008-03-13
Ok, so I'm attempting to install Cacti, and not getting very far. 

Dapper Drake, 6.10 LTS. Very basic install, no KDE/Gnome/etc.

It looks like it's going well...

root@heap:/root# apt-get install cacti
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
   cacti (0.8.6h-3~dapper1)
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/923kB of archives.
After unpacking 3510kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  cacti
Authentication warning overridden.
Preconfiguring packages ...
Selecting previously deselected package cacti.
(Reading database ... 29996 files and directories currently installed.)
Unpacking cacti (from .../cacti_0.8.6h-3~dapper1_all.deb) ...
Setting up cacti (0.8.6h-3~dapper1) ...
dbconfig-common: writing config to /etc/dbconfig-common/cacti.conf

Creating config file /etc/dbconfig-common/cacti.conf with new version

Creating config file /etc/cacti/debian.php with new version
granting access to database cacti for cacti@localhost: success.
verifying access for cacti@localhost: success.
creating database cacti: success.
verifying database cacti exists: success.
dbconfig-common: flushing administrative password

Creating config file /etc/cacti/apache.conf with new version
 * Reloading apache 2.0 configuration...                                                                                                                                           [ ok ] 

root@heap:/root# 

Great! Done? Let's see..

[http://my.host/cacti](http://my.host/cacti) presents the short web installer. I complete it, am given a login screen, but when I attempt to log in, I get the message about "Server has dropped the connection."

At no time have I *ever* had Apache problems on this server. I've rebooted the server, bounced Apache, etc. No resolution.

Here's what I see in access.log:

66.128.59.233 - - [13/Mar/2008:12:58:48 -0500] "GET /cacti/index.php HTTP/1.1" 302 - "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en-us) AppleWebKit/523.15.1 (KHTML, like Gecko) Version/3.0.4 Safari/523.15"
66.128.59.233 - - [13/Mar/2008:12:58:49 -0500] "GET /cacti/index.php HTTP/1.1" 302 - "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en-us) AppleWebKit/523.15.1 (KHTML, like Gecko) Version/3.0.4 Safari/523.15"
66.128.59.233 - - [13/Mar/2008:12:58:49 -0500] "GET /cacti/index.php HTTP/1.1" 302 - "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en-us) AppleWebKit/523.15.1 (KHTML, like Gecko) Version/3.0.4 Safari/523.15"
66.128.59.233 - - [13/Mar/2008:12:58:49 -0500] "GET /cacti/index.php HTTP/1.1" 302 - "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en-us) AppleWebKit/523.15.1 (KHTML, like Gecko) Version/3.0.4 Safari/523.15"
66.128.59.233 - - [13/Mar/2008:12:58:49 -0500] "GET /cacti/index.php HTTP/1.1" 302 - "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en-us) AppleWebKit/523.15.1 (KHTML, like Gecko) Version/3.0.4 Safari/523.15"
^T66.128.59.233 - - [13/Mar/2008:13:06:37 -0500] "GET /cacti/docs/html/ HTTP/1.1" 200 6694 "-" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en-us) AppleWebKit/523.15.1 (KHTML, like Gecko) Version/3.0.4 Safari/523.15"
66.128.59.233 - - [13/Mar/2008:13:06:37 -0500] "GET /cacti/docs/html/manual.css HTTP/1.1" 200 3699 "http://heap.pbp.net/cacti/docs/html/" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en-us) AppleWebKit/523.15.1 (KHTML, like Gecko) Version/3.0.4 Safari/523.15"
66.128.59.233 - - [13/Mar/2008:13:06:40 -0500] "GET /cacti/docs/html/install_unix.html HTTP/1.1" 200 5146 "http://heap.pbp.net/cacti/docs/html/" "Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en-us) AppleWebKit/523.15.1 (KHTML, like Gecko) Version/3.0.4 Safari/523.15"

(FYI, this happens from Linux Firefox too, so it's not browser specific)

cacti.log logs nothing to note.

I can log into the database OK with the cacti user.
The ONLY thing that I can think of is the cacti.conf that it adds for Apache. It mentions php4. I have php5.

root@heap:/etc/cacti# cat apache.conf 
Alias /cacti /usr/share/cacti/site

<DirectoryMatch /usr/share/cacti/site>
        Options +FollowSymLinks
        AllowOverride None
        order allow,deny
        allow from all
        <IfModule mod_php4.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag short_open_tag On
                php_flag register_globals Off
                php_flag register_argc_argv On
                php_flag track_vars On
                # this setting is necessary for some locales
                php_value mbstring.func_overload 0
                php_value include_path .

                DirectoryIndex index.php
        </IfModule>
</DirectoryMatch>

root@heap:/etc/cacti# 

--
I corrected the above line to reflect php5, but no luck. 

I did run a2ensite cacti.conf and added cacti as an active site. Still no luck.

Any ideas? This certainly hasn't been the typeytypey install that the installation documents made it sound like. :-)

Oh yeah, if I go to [http://my.box/cacti/docs/html/](http://my.box/cacti/docs/html/) then I get the installation documents.. which I've read, and still have no resolution. So at the very least, Apache is doing the redirect properly.

---

### Post by dthacker on 2008-03-19
My first thought is that you really need php5.  Was it backported to Dapper?  If not can you move to a later server version?  Your're at the trailing edge of the Dapper support.

---

### Post by pot_roast on 2008-03-19
> **dthacker said:**
> My first thought is that you really need php5.  Was it backported to Dapper?  If not can you move to a later server version?  Your're at the trailing edge of the Dapper support.

I have php5. :-)

root@heap:~# dpkg -l |grep php5
ii  libapache2-mod-php5          5.1.2-1ubuntu3.10            server-side, HTML-embedded scripting languag
ii  php5-cli                     5.1.2-1ubuntu3.10            command-line interpreter for the php5 script
ii  php5-common                  5.1.2-1ubuntu3.10            Common files for packages built from the php
ii  php5-mysql                   5.1.2-1ubuntu3.10            MySQL module for php5
ii  php5-mysqli                  5.1.2-1ubuntu3.10            MySQL Improved module for php5
ii  php5-snmp                    5.1.2-1ubuntu3.10            SNMP module for php5
root@heap:~#


I really hope that I'm not at the trailing edge of anything. The download page says "Ubuntu 6.06 LTS - Supported to 2011."

Although, I have seen quite a few packages that haven't been included in the Dapper tree and are still a version or two behind. (And no backporting seems to have been done.) This concerns me, but that's another thread entirely.

---

