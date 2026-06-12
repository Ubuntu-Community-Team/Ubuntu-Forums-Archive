---
title: "php5 &amp; mysql"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by tbresson on 2006-06-16
For some reason mysql_connect(); doesn't work after a clean Ubuntu install. I added myphpadmin afterwards and that works fint. Read below for a summery of all the posts done [here]("http://www.ubuntuforums.org/showthread.php?p=1156313#post1156313").

---

### Post by grexk on 2006-06-16
What is not function php or mysql?
Check your php.ini if mysql is enabled.
Check your /etc/apache2/mods-enabled for php, if not configured create a symlink from /etc/apache2/mods-available/php*"

---

### Post by tbresson on 2006-06-16
Read below!

---

### Post by tbresson on 2006-06-19
Read below!

---

### Post by tbresson on 2006-06-19
Read below!

---

### Post by tbresson on 2006-06-19
I completed a new install of Ubuntu 6.06.

After the install it said there was updates so I updated the OS as the 1st thing to do.
This generated this [error]("http://work.scarecrow.dk/synaptec-error.png"). (which I havn't seen when I installed the system on June 1st).

After restart I decided to try and instally apache, php and mysql, I choose these packages:

Apache2, php5, mysql-server and php5-mysql + php5-mysqli and all the dependencies synaptec suggested.

All the selected packages (including the ones that are a part of the default install is shown here):

[Apache2]("http://work.scarecrow.dk/apache-postinstall.png")
[PHP]("http://work.scarecrow.dk/php-postinstall.png")
[MySQL]("http://work.scarecrow.dk/mysql-postinstall.png")

All these packages are the same as my box I installed the 1st of June when the OS came out. BUT! with this install and configuration I am unable to connect to the mysql database from php. When I try I get this [error]("http://work.scarecrow.dk/phpmysql-error.png").

If I try with the install I made June 1st I have no problems.

The solution to the problem is to use "sudo dpkg-reconfigure php5-mysql", but what I'm trying to say is that it seems a part of the system is not configured correctly now, but used to be and if something is wrong somewhere people should know about it so they have a chance to correct it.

I might be wrong, and it might be me - but then plz someone explain what I've done wrong.

For your information here's some info on the php.ini and apache mods content:
php.ini contains this at the very bottom:
extension=mysqli.so
extension=mysql.so

/etc/apache2/mod-enabled contains:
php5.conf
php5.load

---

### Post by tapeshag on 2006-06-23
Hi Tbresson,

Today I tried to configure the Apache+Mysql+PHP5 at my setup. I got exactly the same error u have attached. Then I just restarted the apache and it starts working fine. I did not have to do the above mentioned step **"sudo dpkg-reconfigure php5-mysql" **. I feel that the author of php5-mysql needs to put extra logic to check if "libapache2-mod-php5" is installed and if so, restart the apache so that it picks up the new php.ini

---

### Post by tbresson on 2006-06-26
Hmm.. that didn't work for me :-(

The most annyoing thing is, that is wasn't an issue when Ubuntu 6.06 came out and suddenly it is.

I'll guest we'll just have to do a reconfigure or a restart of apache until a developer thinks it's annoying too..

Btw. I restarted like this : sudo /etc/init.d/apache2 restart

---

### Post by jimwillsher on 2006-06-26
I've done two clean installs of Dapper, via the Server CD, onto my two servers. Both were done as LAMP installs, and both worked flawlessly. I didn't have to reconfigure anything. So, the LAMP side of things works well. Perhaps something is preconfigured in the LAMP setup?

(The LAMP set, btw, is brilliant).

Jim

---

### Post by tbresson on 2006-06-26
I've done 2 server installs (lamp) also - and I had no problems there.

This problem only occurs when installing a "normal" install and then choosing the packages my/yourself.

---

### Post by epicadop on 2006-06-26
Hi !
I have a testing server for applications in LAMP, i formatted and install ubuntu four times, the 5.10 and the 6.06. I think i was doing something wrong, but i concluded that there is a "flaw" or bug in the LAMP instalation of Ubuntu that have to be fixed. I have no error in the PHP page, just only when processing the php pages and find a php/mysql script (*"mysql_connect()" for ex;*) just hang up, stops in the line without and error.
I have to go back to Mandrake 10.2 LE.
I tried the "reconfiguration" and didn't work for me.
Any help, it will be appreciated, Thanks !

Edgar

---

### Post by tapeshag on 2006-06-27
If you are facing some issues, with php5 and mysql , I can help if I can connect to your machine on SSH

[QUOTE=epicadop]Hi !
I have a testing server for applications in LAMP, i formatted and install ubuntu four times, the 5.10 and the 6.06. I think i was doing something wrong, but i concluded that there is a "flaw" or bug in the LAMP instalation of Ubuntu that have to be fixed. I have no error in the PHP page, just only when processing the php pages and find a php/mysql script (*"mysql_connect()" for ex;*) just hang up, stops in the line without and error.
I have to go back to Mandrake 10.2 LE.
I tried the "reconfiguration" and didn't work for me.
Any help, it will be appreciated, Thanks !

Edgar[/QUOTE]

---

### Post by epicadop on 2006-06-28
Sorry to the late reply, but i have to go back to Mandrake 10.2. LE

But i have another server with the same problem. This server have Plesk 8.01 for Ubuntu, and can't process mysql and pear scripts in a php page.

Of course i can give you access to the server, please contact me at (i use gaim):

[email]edgar_picado@hotmail.com[/email] in gaim.

thanks !

---

### Post by epicadop on 2006-06-28
U know !!!
I have a test computer. I installed Ubuntu 5.10 and download the updates. Installed the LAMP and tried to connect in php with the mysql, and can't.

OK, i installed the 6.0.6 Desktop, and download-install the update with the LAMP, and have the same problem.

Then, I install the 6.0.6 server, download-install the desktop, and have the same problem.

Then, i tried to reconfigure all the packages that i know, and the same, nothing.

I finally installed Mandrake 10.2 LE again, and everything works smooth !!!

U can say, wel.... stay on MDK,    but sorry, i like Ubuntu, not only installation, desktop and package management, but philosophy too....

Well.... i am stuck...

---

### Post by tapeshag on 2006-06-29
I have added you in MSN. Mine is 'tapeshag@hotmail.com'

---

### Post by tbresson on 2006-06-29
It's kinda of weird you can't get it to work with a clean install.

On purpose I've not corrected the error on my box. But when I was testing the script today, I didn't have any problems; mysql_connect worked.

There have been updates on the box, but I don't know what has happend.

I'll try a reinstall soon and see if it works.

---

### Post by tbresson on 2006-06-30
I did a clean install. Downloaded and installed the updates, rebooted, installed the packages, and made a php-mysql connection test fil.

The error was clear:
Fatal error: Call to undefined function mysql_connect() in /var/www/index.php on line 2

With a simple sudo /etc/init.d/apache2 restart
Everything was working ok !

---

### Post by dom on 2006-07-20
Thanks for this thread guys,

Helped with my Joomla experiment on Xubuntu DD (6.06), the install finally works. [[http://ubuntuforums.org/showthread.php?p=1279952#post1279952]](http://ubuntuforums.org/showthread.php?p=1279952#post1279952])

I reconfigured phph-mysql and re-started apache as per the earlier posts.

---

### Post by az on 2006-07-20
> **tapeshag said:**
> Hi Tbresson,

Today I tried to configure the Apache+Mysql+PHP5 at my setup. I got exactly the same error u have attached. Then I just restarted the apache and it starts working fine. I did not have to do the above mentioned step **"sudo dpkg-reconfigure php5-mysql" **. I feel that the author of php5-mysql needs to put extra logic to check if "libapache2-mod-php5" is installed and if so, restart the apache so that it picks up the new php.ini

I think it's meant to be that way, since you have not set a root password yet.  The reason it seems to work for a LAMP server fresh install is because you reboot after the install, no?  That restartes apache2.

Does mysql-server listen for *remote* connections out-of-the-box?  I seem to think that it does not.  But I'm not sure.  Perhaps that is the problem described?

---

### Post by tbresson on 2006-07-28
azz: It's probably true what you're saying. I just don't remember having problems before. Then again, I might simply have installed Ubuntu so many times by now that I could have set the mysql password for the root logon before testing if an mysql connection could be made from php.

Anywayz; I kind of posted this because I thought someone else might  experience this problem.. and someone was.. tnx for letting us now dom! :)

---

### Post by makadam on 2006-07-31
Thanks for this thread. It helped me to resolve my problem with Apache2, PHP5 and MySQL5 installation.

---

