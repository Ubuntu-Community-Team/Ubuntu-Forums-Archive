---
title: "Apache2 trouble"
date: 2005-07-27
forum: Installation &amp; Upgrades
---

### Post by waveqam on 2005-07-27
Good day all, I just finished installing ubuntu 5.04, installed apache2 added a virtual site but can't get apache2 to start.

I edited /etc/apache2/apache2.conf to add ServerName WaveQam.com to get rid of the error 'Could not determine the server's fully qualified domain name' which seemed to solve that problem.

I created a virtual site called waveqam with the following info

<VirtualHost *>
        ServerName [www.waveqam.com](www.waveqam.com)
        ServerAlias waveqam.com
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/waveqam
        <Directory /var/www/waveqam/>
                Options Indexes FollowSymLinks MultiViews
                # pcw AllowOverride None
                AllowOverride All
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ErrorLog /var/log/apache2/waveqam/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/waveqam/access.log combined
        ServerSignature On

</VirtualHost>

and enabled it using the a2ensite waveqam, and left deafult also alive.

When I /etc/init.d/apache2 reload, I get the following

 * Reloading web server config...
 *tpd not running, trying to start  (Exacly like this)     

When I attempt to brows to the url [http://www.waveqam.com](http://www.waveqam.com) it is asking me for a username and password.  Why?  After the three attempts it fails and I see it is (I think) mini_httpd doing this.  When I attempt to browse to browse to the url [http://139.142.41.245](http://139.142.41.245) I get the same thing.  When I try to browse to it locally [http://10.10.53.2](http://10.10.53.2) I get Page is unable to be displayed error.

What am I doing wrong?

Darcy

Addtional Information:

After searching the fourms I found a referance to 'httpd not running, trying to start'.  I suspect that this is the real error message i should be seeing and not "*tpd not running, trying to start ".  I suspect that there is another httpd server running but I don't see it in ps- aux.  Is mini_httpd installed by default?  What is the username and password for this?  How can it be removed?

Darcy

---

### Post by heimo on 2005-07-27
As far as I know there's no listening services installed by default (at least not any that would listen non-local connections). You can use netstat to check which program is listening on port 80 - if I recall correctly, *netstat -ltp* (should list programs listening on TCP-ports).

Try stopping apache2, check that there's no apache2 or httpd processes before starting and then start again. You can check apache configs syntax with [i]apachectl configtest


[/i]

---

### Post by waveqam on 2005-08-01
Thank-your for the reply.  

I ran netstat and did not see anything listening on 80.  I suspected that httpd was not running at all.

I know it was kinda working before I added my new site, so I did a apache2ctl configtest and that passed.  Just to make sure adding my new site was not the cause of the problem, I used a2dissite waveqam to disable it and reloaded apache.  Wa-la - I now get an index page served up showing both deafault and waveqam.

In the sort term, I would like to default to waveqam (not default or index page) so I am posting both the default and waveqam configs.

In the log term I would like to beable to uses mutilple sites 

Please have a look and let me know where I goofed.

_**default**_
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

_**waveqam**_

<VirtualHost *>
        ServerName [www.waveqam.com](www.waveqam.com)
        ServerAlias waveqam.com
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/waveqam
        <Directory /var/www/waveqam/>
                Options Indexes FollowSymLinks MultiViews
                # pcw AllowOverride None
                AllowOverride All
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ErrorLog /var/log/apache2/waveqam/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/waveqam/access.log combined
        ServerSignature On

</VirtualHost>

This is my site-available directory

root@WaveQamDMZ:/etc/apache2/sites-available # ls -al
total 16
drwxr-xr-x  2 root root 4096 2005-08-01 11:58 .
drwxr-xr-x  8 root root 4096 2005-08-01 11:41 ..
-rw-r--r--  1 root root 1225 2005-07-27 00:23 default
-rw-r--r--  1 root root  955 2005-07-26 23:32 waveqam

This is my sites-enabled directory
root@WaveQamDMZ:/etc/apache2/sites-enabled # ls -al
total 8
drwxr-xr-x  2 root root 4096 2005-08-01 11:42 .
drwxr-xr-x  8 root root 4096 2005-08-01 11:41 ..
lrwxrwxrwx  1 root root   36 2005-07-26 23:40 000-default -> /etc/apache2/sites-available/default

This is my /var/www directory
root@WaveQamDMZ:/var/www # ls -al
total 16
drwxr-xr-x   4 root root 4096 2005-07-26 23:11 .
drwxr-xr-x  15 root root 4096 2005-07-26 21:21 ..
drwxr-xr-x   2 root root 4096 2005-07-26 21:21 apache2-default
drwxr-xr-x   3 root root 4096 2005-07-26 23:12 waveqam


Thanx for your help
Darcy

---

