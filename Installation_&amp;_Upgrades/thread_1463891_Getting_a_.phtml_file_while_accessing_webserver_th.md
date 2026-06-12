---
title: "Getting a .phtml file while accessing webserver through firefox"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by DC80 on 2010-04-27
Hi all, 

I'd like to ask a question about the apache webserver. I'm very sorry to post this topic here. It seems likely that this post is better off in server platforms and i didn't know where to post it. 

Anyway, i have a problem with my apache webserver. Well, not so much however it is behaving strangely. When i installed the apache webserver and accessed the webroot (/var/www) through my webbrowser it said: It works!. Then i added a folder with an .php file to the root folder and get an error: access denied when i accessed it through my webbrowser. 

I'v tried to modify /var/www with chmod but this didn't work, however i do get a .phtml file offered as a download.

Also i have looked for a configuration file (httpd.conf) to alter the "DirectoryIndex" string. I did find the apache2.conf instead but it has no "DirectoryIndex" directive. 

I did google this problem but there is no straight answer to this. Could someone help me please?

DC80

---

### Post by DC80 on 2010-04-28
Edit: the problem seems to be solved. I do not know how i did it. I shut my computer down last night and this evening up. After doing some things i stopped and started apache as root. And now it seems to be working.

---

### Post by madtom1999 on 2010-05-01
I'm getting the same problem
php files offered for download 
a2enmod php5 says its already enabled...

---

### Post by madtom1999 on 2010-05-02
php is sort of working.
Most of my work is in netbeans projects and I needed to re-create the projects and now php works in them
php in non-netbeans projects still doesnt - no .htaccess that I can find so I dont know quite why...

---

### Post by dineshamle on 2011-01-12
> **DC80 said:**
> Hi all, 

I'd like to ask a question about the apache webserver. I'm very sorry to post this topic here. It seems likely that this post is better off in server platforms and i didn't know where to post it. 

Anyway, i have a problem with my apache webserver. Well, not so much however it is behaving strangely. When i installed the apache webserver and accessed the webroot (/var/www) through my webbrowser it said: It works!. Then i added a folder with an .php file to the root folder and get an error: access denied when i accessed it through my webbrowser. 

I'v tried to modify /var/www with chmod but this didn't work, however i do get a .phtml file offered as a download.

Also i have looked for a configuration file (httpd.conf) to alter the "DirectoryIndex" string. I did find the apache2.conf instead but it has no "DirectoryIndex" directive. 

I did google this problem but there is no straight answer to this. Could someone help me please?

DC80

for download thing: try installing php again using apt-get install php5 (for ubuntu) ... if it says no changes, remove php completely using apt-get remove php5 and install it again 

then try 

apt-get install libapache2-mod-php5

and now restart apache2

/etc/init.d/apache2 restart

and clear ur browser cache and try hitting ur local development site. I guess this should work

---

### Post by arestivo on 2011-08-28
Had the same problem as the OP with a clean apache+php install. Restarting apache was enough to get everything going.

---

