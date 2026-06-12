---
title: "apache and domain"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by jamstir on 2012-02-20
Hi people, has anyone tried or got a domain set up and working on the net using apache 2.2 from ubuntu.. from right here in fact..  
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)



BECAUSE I SEEM TO HAVE HIT A WALL!!

        NameVirtualHost *:80
        
        <VirtualHost *:80>
                     ServerName [www.domain.tld](www.domain.tld)
            ServerAlias domain.tld *.domain.tld
            DocumentRoot /www/domain
                 </VirtualHost>
        
        <VirtualHost *:80>
        ServerName [www.otherdomain.tld](www.otherdomain.tld)
            DocumentRoot /www/otherdomain
                 </VirtualHost>


Everywhere i look on the net its the same,,  as the one above.. apart from mine downbelow, that looks like this.


<VirtualHost *:80>
    ServerAdmin  [email]webmaster@globalsource.tk[/email]

    DocumentRoot /var/www/globalsource.tk/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/globalsource.tk/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all

I have reg.. a domain name and seem to be missing something in getting the website to go anywhere apart from loopback in my machine using localhost.  the fact that i dont have these 2 pieces of info  ...
ServerName.
            ServerAlias

Should i just add them in, and is there anyway or do i have to port forward in anyway?
I have read the manual for Apache and understand it very well, if my Apache looked anything like the one they talk about in the manual i would have had this working at lunch time to day instead of it now being 7;20 pm at night and about to hit the drink for the reminder of the year. hahaha

Anyone shed some light on the topic please.. thanks..

---

