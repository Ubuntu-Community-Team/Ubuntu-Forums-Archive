---
title: "Apache2/Drupal problem after upgrade  [SOLVED]"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by JoelParke on 2013-10-17
I am seeing a strange Apache2 problem after upgrading.
I still see all of my sites, HOWEVER I can no longer access any of the sub-urls.
For example:
blabblahsite.com/user/login  IS NOT LONGER ACCESSIBLE, and web shows:
***Not Found***
***The requested URL /user/login was not found on this server.***
***Apache Server at blabblahsite.com Port 80***

/var/log/other_vhosts_access.log shows:
"GET /user/login HTTP/1.1" 404 479 "http://blabblahsite.com/" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/28.0.1500.72 Safari/537.36"
-- but no errors reported anywhere that I can find.
ALSO - since I can't login - no reports, etc.

Any Thoughts or what might be causing this issue?  You help is much appreciated!

---

### Post by JoelParke on 2013-10-17
I discovered that the Clean URL's were not working.  They had been enabled prior to the upgrade.
I tested using [http://blabblahsite.com/?q=user/login](http://blabblahsite.com/?q=user/login) WHICH then allows me to login.  
Of course, all the subsequent URL's are wrong until I turned off the Clean URL's setting.
I will report back SOON ... after I determine what is broken in the Clean URL's.

---

### Post by JoelParke on 2013-10-17
I hunted and discovered that with the upgrade, the apache2.conf file changed to limit access by default:
See:
# Sets the default security model of the Apache2 HTTPD server. It does
# not allow access to the root filesystem outside of /usr/share and /var/www.
# The former is used by web applications packaged in Debian,
# the latter may be used for local directories served by the web server. If
# your system is serving content from a sub-directory in /srv you must allow
# access here, or in any related virtual host.
<Directory />
	Options FollowSymLinks
	AllowOverride None
	Require all denied
</Directory>


<Directory /usr/share>
	AllowOverride None
	Require all granted
</Directory>


<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride All
	Require all granted
</Directory>


SO I needed to modify AllowOverride None to AllowOverride All:
<Directory /var/www/>
        Options Indexes FollowSymLinks
**        AllowOverride All **
        Require all granted
</Directory>

Now all is working as expected.  I hope this helps someone else.

---

### Post by mörgæs on 2013-10-18
Thanks for an attempt at marking the thread 'solved'. The best way is using 'thread tools', though.

---

