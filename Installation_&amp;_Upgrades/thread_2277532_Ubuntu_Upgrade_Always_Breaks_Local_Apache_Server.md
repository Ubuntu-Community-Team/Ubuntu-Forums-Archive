---
title: "Ubuntu Upgrade Always Breaks Local Apache Server"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2015-05-09
I am frustrated that EVERY time I upgrade to a new release of Ubuntu I have to waste a day fiddling with the Apache server config to get rid of the "You don't have permission to access / on this server" error message.  The upgrade in no way changes the permissions of the directories and files that the web site is contained in, it is just the arcana of the Apache configuration files that creates this problem.  I don't mind that I have to reinstall the LAMP stack, that is just one command.  MySql comes up fine and the only configuration information that it requires is the password of the root user, but the Apache server configuration is thrown away wasting my time!

I am trying to maintain the same directory structure on my development machine as on the production system on the public server.  So the web site is in /home/user/public_html.  I have browsed a large number of pages and forum responses regarding this and for some reason they all deal with far more complicated configurations than this or explain details in a way that obviously makes sense to the people who wrote the code, but I do not have the time to become an expert in Apache 2 configuration arcana.  I do not understand why I am required to do anything more than tell the server where the directory is.  I do not understand why when I have explicitly told the server that I want it to look at /home/user/public_html that the error message refers to the root directory.  What does the server mean when it refers to the root directory?

Why does the upgrade replace the working /etc/apache2 directory contents when this will clearly cause the site to fail?

I have been fiddling with the /etc/apache2/sites-available/000-default.conf directory trying to get the site back up and the current non-working version is as follows.  I do not understand anything that is in this file and I resent that the authors of this installation process insist that I must waste my time understanding all of this trivia.
```
<VirtualHost *:80>
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName www.example.com

    ServerAdmin webmaster@localhost
    DocumentRoot /home/jcobban/public_html
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/jcobban/public_html>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
    # error, crit, alert, emerg.
    # It is also possible to configure the loglevel for particular
    # modules, e.g.
    #LogLevel info ssl:warn

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    # For most configuration files from conf-available/, which are
    # enabled or disabled at a global level, it is possible to
    # include a line for only one particular virtual host. For example the
    # following line enables the CGI configuration for this host only
    # after it has been globally disabled with "a2disconf".
    #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

---

