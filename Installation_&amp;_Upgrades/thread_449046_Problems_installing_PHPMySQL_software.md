---
title: "Problems installing PHP/MySQL software"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by Skylinux on 2007-05-19
I'm the developer of [WorkOrder TS]("http://www.workorderts.com/") a PHP/MySQL ticket tracking application. I have been contacted by a user running the latest XUbuntu who is attempting to install my software but is unable to due to an error. 

Unable to find a solution, I downloaded the latest XUbuntu and installed it into a VMWare environment. 
After the installation I used the Synaptic Package Manager to install Apache, PHP and MySQL. 
I selected the following packages and applied any required dependencies.
mysql-client
mysql-client-5.0
mysql-common
mysql-server
mysql-server-5.0
PHP5-Mysql

I can login into mysql via mysql -u root 
the installed version is: 5.0.38-Ubuntu_0ubuntu1-log
I can also restart the MySQL server without problems.

When attempting to install my software, PHP fails to connect to the MySQL server. I downloaded the latest version of phpBB2 of their website, tried to install it and received an error message that PHP is not configured for the current MySQL server version.

Any ideas why there are problems?
BTW, the user who contacted me tried to install egroupware and also received an error that egroupware is unable to create the required database.

---

### Post by Skylinux on 2007-05-19
I just checked phpinfo() and there is no mysql section. I will uninstall and reinstall apache, php and mysql to see if it will add the required mysql module.

---

### Post by Skylinux on 2007-05-19
Ok, I reinstalled and noticed a big problem with dependencies in Ubuntu's package management. On any other distro I have worked on, when I select the php5 mysql module, the dependencies will take care of installing apache, php5 and mysql plus other dependent packages. For some reason yours does not.

When I select the php5 module, I don't even get apache with it, I get the module but not apache. The PHP5 was not selected either but the php5-mysql module was.

---

### Post by Skylinux on 2007-05-19
All the software is installed again, this time the package manager does list apache, php5 and mysql server to be installed ecbause I manually selected them. 
The output of phpinfo() does not mention mysql anywhere.
php.ini contains information regarding mysql and mysqli even though phpinfo() does not.
Apache executes php scripts properly as long as they don't try to connect to a database. 
phpBB2 still fails.

---

### Post by Skylinux on 2007-05-21
To finalize this thread, my customer has been able to get PHP/MySQL/Apache to work after reinstalling XUbuntu again. Since he did get it to work, there was no reason for me to continue messing with this. Somebody might take note and try to install Apache,MySQL, PHP on a fresh XUbuntu install to reproduce the bug. 

Good luck.

---

