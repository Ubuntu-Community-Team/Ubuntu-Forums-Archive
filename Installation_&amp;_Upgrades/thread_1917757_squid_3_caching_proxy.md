---
title: "squid 3 caching proxy"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-01-30
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

for those industrial strength folks using routing servers this is appropriate and relevant to squid
[http://www.quagga.net/docs/docs-info.php](http://www.quagga.net/docs/docs-info.php)
if a cisco router needs a database to run OSPF, why not just have the database its self do some routing.
i have not set this up but these 2 topics are side by side.

this copy/paste tutorial is for squid forward, and reverse proxy...  it will push your local web site to the net, and will make local users of the server get cached versions of web pages.  it uses a local http server on an alternate port as an example from the local squid.  in practice your going to want your actual http server further buried within the network because of security reasons.

alt + f2

gnome-terminal

run

```

sudo apt-get install squid3 squid-cgi

```

go god mode in the terminal

```

sudo su

```

move your squid.conf to a safe place before you beat it up....

```

mv /etc/squid3/squid.conf /etc/squid3/squid.conf.backup

```

to turn on a reverse proxy (accelerate YOUR web page on your local machine)

```

cat > /etc/squid3/squid.conf << EOF
http_port 80 accel defaultsite=127.0.0.1
cache_peer 127.0.0.1 parent 81 0 no-query originserver name=myAccel
acl our_sites dstdomain 127.0.0.1
http_access allow our_sites
cache_peer_access myAccel allow our_sites
cache_peer_access myAccel deny all
EOF

```

now re populate the squid conf from the backup

```

cat >> /etc/squid3/squid.conf /etc/squid3/squid.conf.backup

```

once you have done that then drop this block of code to remove version information in your error pages.  (dont let people look up attacks for your exact version, make them guess....)  drop this block of code in god mode....

```

cat >> /etc/squid3/squid.conf << EOF
httpd_suppress_version_string On
EOF
exit

```
and press enter to exit god mode

to make your error pages black background with white text....

again go god mode in the terminal

```

sudo su

```

```

mv /etc/squid3/errorpage.css /etc/squid3/errorpage.css.backup
cat > /etc/squid3/errorpage.css << EOF
/* Page basics */
* {font-family: verdana, sans-serif;}
html body {margin: 0;
padding: 0;
background: black;
font-size: 12px;
color: white;}

/* Page displayed title area */
#titles {margin-left: 15px;
padding: 10px;
padding-left: 100px;
background: url('http://www.squid-cache.org/Artwork/SN.png') no-repeat left;}
/* initial title */
#titles h1 {color: white;}
#titles h2 {color: white;}
/* special event: FTP success page titles */
#titles ftpsuccess {background-color: black;
width:100%;}
/* Page displayed body content area */
#content {padding: 10px;
background: black;}
pre {font-family:sans-serif;}
/* special event: FTP / Gopher directory listing */
#dirmsg {font-family: courier;
color: white;
font-size: 10pt;}
#dirlisting {margin-left: 2%;
margin-right: 2%;}
#dirlisting tr.entry td.icon,td.filename,td.size,td.date {border-bottom: groove;}
#dirlisting td.size {width: 50px;
text-align: right;
padding-right: 5px;}
/* horizontal lines */
hr {margin: 0;}
/* page displayed footer area */
#footer {font-size: 9px;
padding-left: 10px;}
EOF
exit

```

then finally to tell your squid logs "hush" since you know the servers caching and working good...

in terminal again go god mode
```

sudo su

```

```

cat >> /etc/squid3/squid.conf << EOF
cache_access_log /dev/null
cache_store_log none
cache_log /dev/null
EOF
exit

```

now since you have done your essential fixes for squid, restart it

```

sudo service squid3 restart

```

and make your squid your systems default proxy....

do

alt + f2

gnome-network-properties 

run

set to manual proxy configuration

check use the same protocol for all protocols

http proxy 127.0.0.1 port 3128

and then click apply system wide, give your root password twice and bam ur surfing in style on all your browsers


(WARNING reverse proxy stuff is broken for the moment....)

now to change your apache port to listen to 81 so squid forwards it correctly...

backup your previous ports directive
```

sudo mv /etc/apache2/ports.conf /etc/apache2/ports.conf.backup

```

go god mode and then replace the ports with this block of code

```

sudo su

```

```

cat > /etc/apache2/ports.conf << EOF
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz
NameVirtualHost *:81
Listen 81
<IfModule mod_ssl.c>
# If you add NameVirtualHost *:443 here, you will also have to change
# the VirtualHost statement in /etc/apache2/sites-available/default-ssl
# to <VirtualHost *:443>
# Server Name Indication for SSL named virtual hosts is currently not
# supported by MSIE on Windows XP.
Listen 443
</IfModule>
<IfModule mod_gnutls.c>
Listen 443
</IfModule>
EOF
exit

```

now to fix your sites enabled...

backup the original

```

sudo mv /etc/apache2/sites-available/default /etc/apache2/sites-available/default.backup

```

go god mode again

```

sudo su

```

paste this code to move the port over

```

cat > /etc/apache2/sites-available/default << EOF
<VirtualHost *:81>
ServerAdmin webmaster@localhost
DocumentRoot /var/www
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/>
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
</Directory>
ErrorLog ${APACHE_LOG_DIR}/error.log
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn
CustomLog ${APACHE_LOG_DIR}/access.log combined
Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>
</VirtualHost>
EOF
exit

```

finally restart your apache to get it up again under port 81

sudo service apache2 restart

---

