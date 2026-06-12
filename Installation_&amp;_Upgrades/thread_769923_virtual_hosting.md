---
title: "virtual hosting"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by jk111 on 2008-04-27
Hello all,

I have set up apache on ubuntu server edition.  I have everything running but I am having a very hard time setting up virtual hosting.  I am using ssh to get into the server and change all the configuration files.

First, in /etc/apache2/sites-available, I have my own (new) file that i called example.exampledomain.com.conf

That file looks like this:

<VirtualHost example.exampledomain.com>
ServerAdmin [email]example@example.com[/email]
#We want to be able to access the web site using [www.dev.example.com](www.dev.example.com) or dev.example.com
ServerAlias [www.example.exampledomain.com](www.example.exampledomain.com)
DocumentRoot /home/myusername/public_html/example.exampledomain.com
#if using awstats
ScriptAlias /awstats/ /usr/lib/cgi-bin/
#we want specific log file for this server
CustomLog /var/log/apache2/example.com-access.log combined
</VirtualHost>

I have tried everything but still no luck.  I have also tried the a2ensite but it says that site is already enabled.  When I browse to my site, I get the normal, it works message instead of the index.html file I placed in my document root.

What am I doing wrong?

Thanks,

jk111

P.S. I also have a link to example.exampledomain.com.conf in /etc/apache2/sites-enabled

---

### Post by jk111 on 2008-04-27
Sorry, wrong category for this post.

---

