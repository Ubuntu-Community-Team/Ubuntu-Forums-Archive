---
title: "Wordpress Permissions? - Apache works from all - Wordpress only localhost"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by suffice on 2010-11-19
Hello,

I have an apache server running.  It works on localhost and from just my IP (other computers) just fine.  I have several pages and they all work fine.  My mythweb works at my [http://myip/mythweb](http://myip/mythweb) and localhost as well. So does the transmission webclient.

I installed wordpress which works just fine at localhost/wordpress, but not from [http://myip/wordpress](http://myip/wordpress).  

I have followed several tutorials and have done all the steps.  

I have had to use a virtualhost (000-default) file in sites-enabled to get my site to run before wordpress was installed.  I dont really want it to be a separate site with a separate domain, but simply an [http://myip/wordpress](http://myip/wordpress).  different directories  in var/www ([http://myip/somedir](http://myip/somedir))  work for the site, just not the www/wordpress link one.

I think it has something to do with the permissions on the wordpress folder, but not really sure.

has anyone come across this or an help me out at all?

---

