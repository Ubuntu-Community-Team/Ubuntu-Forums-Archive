---
title: "how to install typo3"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by cazique on 2007-09-04
Not finding a installation guide for typo3 on ubuntu, although finding a very good guide in german for debian-systems, i thought i'll translate this guide (with the authors permission) to english. The german site can be found at: **[SIZE="3"][COLOR="Red"][http://www.tim-bormann.de/index.php?section=157](http://www.tim-bormann.de/index.php?section=157)[/COLOR][/SIZE]**

It's possible to get your typo3 by apt-get but on my computer it didn't work properly and that version isn't up-to-date. So here's an very good alternative to install tyop3 4.1.2 on your ubuntu 7.04:

**Update your apt-lists and get the newest versions:**
```
sudo apt-get update
sudo apt-get upgrade
```

**Then you have to install apache2 with php5 and mysql (also know as lamp, linux-apache-mysql-php):**

```
sudo apt-get -y install apache2 libapache2-mod-php5 php5-cli php5-common php5-cgi mysql-common mysql-server mysql-server-5.0 phpmyadmin
```

Now, so far you have the main tools on which typo3 relies on. Let's start setting up a database for typo3. 

**Change the default password in mysql**

```
sudo mysqladmin -u root -p password 'your-new-password'
```

**Then create a database for typo3:**

```
sudo mysqladmin -pyour-new-password create Typo3
```

As you know you shouldn't access the database always with root so we create a new user:

**Start mqsql:**
```
mysql -u root -p
```

**and set up the new user:**
```
mysql> grant all privileges on Typo3.* to New-username@localhost identified by 'typo3';
```

**Quit mysql safely:**
```
mysql> flush privileges; 
mysql> quit
```

So now you successfully configured mysql for typo3. :KS 
We have to restart apache2 in order to see the changes.

**Restart apache2 with: **
```
sudo /etc/init.d/apache2 restart
```

Let's get on with the typo3 installation. Typo3 is based on php so we have to copy all the files to the apache2 web-directory. 

**Change to this directory:**
```
cd /var/www/
```

**Get the typo3 source-package. **(Don't worry, you don't have to compile anything! :) )
```
wget http://kent.dl.sourceforge.net/sourceforge/typo3/typo3_src-4.1.2.tar.gz
```

**Unpack the packages:**
```
tar xzf typo3_src-4.1.2.tar.gz
```

You probably wanna start typo3 with the dummy-package because it guides you very nicely through the setup and configuration of typo3. 

**Get the dummy-package and unpack it:**
```
wget http://heanet.dl.sourceforge.net/sourceforge/typo3/dummy-4.1.2.tar.gz
tar xzf dummy-4.1.2.tar.gz
```

**Create and move the dummy-files to folder called cms i.e.:**
```
mv dummy-4.1.2 cms
cd ./cms
```

**Don't forget to set the ownership-rights correctly:**
```
chown -R -v www-data /var/www/typo3_src-4.1.2
chown -R -v www-data /var/www/cms
```

:KS Your done! :KS Typo3 should be now installed and working! You can now go on with the configuration of typo3! 

**Start the typo3 installer pointing firefox to:**
[http://localhost/cms/typo3/install.php](http://localhost/cms/typo3/install.php)

Probably a pop-up appears telling you more or less important things. If not, this is the password for the next page: 
**joh316**
Make sure to change it as soon as possible!
[SIZE="5"]
1.)[/SIZE]  At the upcoming login-screen enter the username and password you used for creating the mysql useraccount!
[SIZE="5"]
2.)[/SIZE] Select an existiing EMPTY database: **Typo3**
Create new database (recommended): <empty>

[SIZE="5"]3.)[/SIZE] Import the database sql-file: **<Import database>**

It's important to change the default-password, so set it new by:
***Continue to configure Typo3 ***

Furthermore you should change the admin password. Open in your browser:
[http://localhost/cms/typo3/index.php](http://localhost/cms/typo3/index.php)
Username: **admin**
Paswort: **password**

( :KS I would make a bookmark to this page!! :KS )

In the left tab go to:
> Tools > User Admin > Edit (pencil-symbol next to admin) > your-new-password
hit < return >

Hopefully i could help you installing typo3 on ubuntu and for further steps go to:
**[SIZE="4"][COLOR="Red"][http://typo3.org/documentation/](http://typo3.org/documentation/) [/COLOR][/SIZE]**

Cheerzzzz

---

### Post by mscott on 2007-11-10
hi Cazique,
Thank you for this hard to find information.  Over the past 24 hours, I've installed Ubuntu 7.10 Server with LAMP options.  I've also downloaded the latest Typo3 v4.1.3, source and dummy tgz files.  My attempts to get Typo3 off the ground fail at your step of Starting the TYPO installer with [[http://localhost/cms/typo3/install.php]](http://localhost/cms/typo3/install.php]) - 404 Page not found.  In fact, there is no install.php anywhere.  I tried to load the index.php, but got a Database error page "The current username, password or host was not accepted when the connection to the database was attempted to be established!"

Any thoughts?  Much appreciated!
Mike

---

### Post by rockprincess on 2008-01-19
any ideas why the quickstart 3.8.1 package won't work under ubuntu?

i always get "403 Forbidden....access denied" when trying to access the quickstart install tool

the dummy package works fine though....

any idea how i can import the quickstart package into the dummy package, since it won't start under localhost although it is in /var/www/ ?!

please help me!

many thanks in advance

---

