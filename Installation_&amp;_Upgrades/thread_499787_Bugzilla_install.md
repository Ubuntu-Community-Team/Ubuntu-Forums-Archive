---
title: "Bugzilla install"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by Ultife on 2007-07-13
I have found the Bugzilla install and setup rather tedious on a new Ubuntu Lamp 7.04 Feisty Fawn server (cmd line only).
These are the steps I came up with to successfully complete an install.
Please post any comments/explanations/optimizations.
[B]
Pre-requisites:[/B]
[LIST]
[*]Apache
[*]Phpmyadmin (may use mysql server cmd, but why the extra hassle?)
[*]Mysql
[/LIST] 

First setup the user in phpmyadmin from a web browser:
To do this from Home go to *privileges>add a new user*
[LIST]
[*]specify the name as Bugzilla
[*] local (specifies @localhost)
[*]password: *secret *(*this seems to be the default password in some of the Bugzilla setup scripts and dbcommon)
[*]Create DB with same name and grant all access to that DB
[/LIST] 

From the machine where you wish to house Bugzilla
[LIST]
[*]sudo apt-get install bugzilla
[*]Set the email to anything you like you can always change it later.
[*]Set the administrator's real name.
[*]YES (use dbcommon) for db creation, it is not recommended to use the manual way unless you know what is happening
[*]Admin password : *EMPTY *if your Mysql admin password has not been changed from the default install
[*]Application password: *secret  *(*this is a weak password and will need to be changed after the install)
[*] Install the package maintainer's version (* this may happen during the install)
[/LIST]
Try in your web browser: _*[http://SERVER_IP/bugzilla/](http://SERVER_IP/bugzilla/)*_

If unsuccessful try again from the apt-get install, or try apt-get remove bugzilla and then try again.
If all else fails re-install Ubuntu.
Note: Altering or deleting any files after an unsuccessful install is not recommended.
All manipulations should be done from the apt-get method with sudo privileges.

Hope this helps some people. Next I will be migrating an existing Bugzilla database from a previous version of Mysql and Bugzilla, please let me know if there is anything I should know.
Thank you.

---

### Post by Ultife on 2007-07-15
**_Database migration:_**
Here's what I had to do in order to get things going.
Resource: [http://wiki.mozilla.org/Bugzilla:2.0.x_upgrade](http://wiki.mozilla.org/Bugzilla:2.0.x_upgrade)
[B]
 Database backup[/B]
    * To find a file in case you lost it! find / -name 'File_name.sql' 

Putty to target computer
*mysqldump -u user_name -p your_password bugs > bugzilla.sql*
Copy the backup from nobbles to lamp
*scp bugzilla.sql target:*
It is recommended that you backup the fresh copy of the bugzilla database on target before you attempt to restore.
*sudo mysql -u root bugzilla > bugzillaOriginal.sql*
To restore the database try and use phpmyadmin import function otherwise use the cmd line.
*sudo mysql -u root bugzilla < bugzilla.sql*

Once the database has been migrated, copy all of the old cgi scripts and miscellaneous files from the previous version:
1.Copy all current files in /usr/share/bugzilla/web/ to your home directory (actual file path may be different for you)
2.Change permissions to your user and group on all files in web
3.Create a directory of same name in your home dir on the target computer
4.SCP all contents through winscp or scp
5.Move the files to the target bugzilla directory
6.Change all files owner and group to www-data (from apache2 apache2 web user)

Finally to enable all scripts fix the bug in bugzilla if it still exists:
 Replace:  
 'urlbase'  => './cgi-bin/bugzilla/',  
 for  
 'urlbase'  => '/cgi-bin/bugzilla/',  
 in this files  
 /etc/bugzilla/params

---

### Post by WhosRodney on 2007-09-24
Thanks for the help!  Got me up and running fast!

---

