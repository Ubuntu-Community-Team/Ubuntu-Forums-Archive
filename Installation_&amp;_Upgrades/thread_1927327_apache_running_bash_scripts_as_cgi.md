---
title: "apache running bash scripts as cgi"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-02-17
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

apache can run bash scripts as cgi...  i looked up how to do this, and this is what i found.  (warning run my other apache install symlinking before doing this)

i want to move my cgi-bin directory first, and symlink it back so a non privileged user can run the website.

so alt + f2

gnome-terminal

run

then paste this block of code to move & symlink it up

```

sudo mv /usr/lib/cgi-bin/ $HOME/www/ && sudo ln -s /srv/www/cgi-bin/ /usr/lib/cgi-bin

```

then fix permissions to your user name

```

sudo chown $USER $HOME/www/cgi-bin/ && sudo chgrp $USER $HOME/www/cgi-bin/

```

chown chgrp all the goodies in cgi-bin to your user if you have any

```

sudo chown $USER $HOME/www/cgi-bin/* && sudo chgrp $USER $HOME/www/cgi-bin/*

```

then give it a script to say my system information

```

cat > $HOME/www/cgi-bin/sysinfo.sh << EOF
#!/bin/bash
echo "Content-type: text/html"
echo ""
echo "<html class="background"><head><link rel="stylesheet" href="../index.css" type="text/css" /><title>system information for $(hostname -s)"
echo "</title></head><body>"
echo "<h1 class="center">General system information for host $(hostname -s)</h1>"
echo ""
echo "<h2>Memory Info</h2>"
echo "<pre> $(free -m) </pre>"
echo "<h2>Disk Info:</h2>"
echo "<pre> $(df -h) </pre>"
echo "<h2>Logged in users</h2>"
echo "<pre> $(w) </pre>"
echo "<center>Information generated on $(date)</center>"
echo "</body></html>"
EOF
chmod +x $HOME/www/cgi-bin/sysinfo.sh

```

and the css file im using is

```

cat > $HOME/www/index.css << EOF
html

{
background: black
}

html, body, div, p

{
color: white
}

.center

{
text-align: center
}

h1

{
margin-top: 7%
}

.background

{
     background-image: url(/galaxy.jpg);
     background-size: 100%;
}
EOF

```

download my galaxy image here...

[http://img826.imageshack.us/img826/3369/galaxyx.jpg](http://img826.imageshack.us/img826/3369/galaxyx.jpg)

to $HOME/Downloads (firefox/seamonkeys default)


and then mv $HOME/Downloads/galaxyx.jpg $HOME/www/galaxy.jpg

then load [http://localhost/cgi-bin/sysinfo.sh](http://localhost/cgi-bin/sysinfo.sh) to see your systems stats via web interface cgi script.

i found it problematic to get server side includes running, to have another method of inserting my scripts to my server so i will mention here what i did to get that up and running.....  (this is like saying "my /etc/apache2/sites-available/default looks like this block of code, its worth noting that if your web server was on port 80, its probably going to show up on port 81 because of my squid configuration, simply gedit the 81 to 80 in the <VirtualHost *:81> field)


alt + f2

gksu gnome-terminal

run

enable server side includes...

```

a2enmod include

```

then feed this to the terminal

```

mv /etc/apache2/sites-available/default /etc/apache2/sites-available/default.backup
cat > /etc/apache2/sites-available/default << EOF
<VirtualHost *:81>
ServerAdmin webmaster@localhost
DocumentRoot /var/www
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/>
Options Indexes FollowSymLinks MultiViews +Includes
AllowOverride None
Order allow,deny
allow from all
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
DirectoryIndex index.shtml
</Directory>
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
</Directory>
ErrorLog /error.log
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn
CustomLog /access.log combined
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

i think its worth noting that i also had to not have a HTML file present for the web server to select the SHTML file.  thus move the index.html to index.shtml then start putting the include codes in.

---

