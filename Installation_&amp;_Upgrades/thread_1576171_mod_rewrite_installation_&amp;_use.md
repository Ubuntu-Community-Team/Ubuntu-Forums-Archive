---
title: "mod_rewrite installation &amp; use"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by mu2pilot on 2010-09-16
I'm trying to setup a new server running Ubuntu 10.xx.  When someone types my domainname.com, I want to do a mod rewrite to change it to [www.domainname.com](www.domainname.com).  I can't get it to work.  Here is my .htaccess file:

RewriteEngine on
RewriteCond %{HTTP_HOST} !^www\. [NC]
RewriteRule .? http://www.%{HTTP_HOST}%{REQUEST_URI} [R=301,L]

I've also tried this:

RewriteEngine on
RewriteCond %{HTTP_HOST} ^domainname\.com
RewriteRule ^(.*) http://www.domainname.com/$1 [L,R=301]

I'm pretty sure its not the code because it is work for me on other servers.  I've never built a Linux server from the ground up and I must be leaving something out.  I've installed mod_rewrite, as I thought that was causing the problem, but it doesn't appear to be.

Help would be appreciated.

mu2pilot

---

