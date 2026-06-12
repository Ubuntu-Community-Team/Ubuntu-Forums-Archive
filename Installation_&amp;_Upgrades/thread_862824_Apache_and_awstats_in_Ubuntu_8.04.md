---
title: "Apache and awstats in Ubuntu 8.04"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by rompstar420 on 2008-07-17
I am running Ubuntu 8.04 with all the latest updates, on AMD 64-bit.

I have apache installed, whatever is the version that comes with my Ubuntu, and I wanted to install awstats, and I successfully installed it and the web site works  can access the statistics and see everything.

But none of the graphics and icons want to load and I am starting to pull my hair out in trying to figure out why, here is from the bottom of my

 /etc/apache2/apache2.conf file:

Alias /awstatsclasses "/usr/local/awstats/wwwroot/classes/"
Alias /awstatscss "/usr/local/awstats/wwwroot/css/"
Alias /awstatsicons "/usr/local/awstats/wwwroot/ikons/"
ScriptAlias /awstats/ "/usr/local/awstats/wwwroot/cgi-bin/"

<Directory "/usr/local/awstats/wwwroot">
Options FollowSymLinks
#Options None
AllowOverride None
Order allow,deny
Allow from all
</Directory>

I get this error when I try to view any graphics file via the browser directly:

Forbidden

You don't have permission to access /usr/local/awstats/wwwroot/ikons/other/vh.png on this server.

Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.2 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Server at localhost Port 80


Any ideas ?

Starting to bug me.:confused:

I did name my directors ikons (not icons) instead and the directory does exists...

---

### Post by afewtips.com on 2008-08-15
Check this post - 
[http://www.debianhelp.co.uk/awstats.htm](http://www.debianhelp.co.uk/awstats.htm)

It mentions something about the icons:
Your entry for /awstats-icon/ in the Aliases section should look like:

Alias /awstats-icon/ /usr/share/awstats/icon/
<Directory /usr/share/awstats/icon>
Options None
AllowOverride None
Order allow,deny
Allow from all
</Directory>

Hope this helps. Good Luck.

---

