---
title: "Problem in Installing Drupal on Ubuntu"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by theou huios on 2011-01-27
Hello

I was trying to install Drupal on Ubuntu. Everything went fine . But when it came to the installation page which opens up in local host this is the error 


> Installation tasks
[LIST=1]
[*]Choose profile(done)
[*]Choose language(done)
[*]Verify requirements(active)
[*]Set up database
[*]Install profile
[*]Configure site
[*]Finished
[/LIST]
      
                             OK
Web serverApache/2.2.16 (Ubuntu)OK
PHP5.3.3-1ubuntu9.3OK
[B]PHP register globalsDisabledError
PHP extensionsDisabledDrupal requires you to enable the PHP extensions in the following list (see the [system requirements page]("http://drupal.org/requirements") for more information):[/B]
[LIST]
[*]**gd**
[/LIST]

OK
Database supportEnabledOK
PHP memory limit128MOK
File systemWritable (*public* download method)OK
Unicode libraryPHP Mbstring ExtensionOK
Settings fileThe *./sites/default/settings.php* file exists.Then I tried installing PHP5 . And this is what I get. I did install PHP5. I am not able to understand whats wrong it this.

> theou@ubuntu:/var/www$ sudo apt-get install php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I refreshed the page and tried to see whether that error is gone, but nope. It still says the same. Any Suggestions?

---

### Post by perspectoff on 2011-01-27
GD is a graphics library. PHP can use the GD graphics library (versus Imagemagick) and it is asking that the php5-gd libraries be installed.

Try this (from a command-line interface Terminal):
 sudo apt-get install php5-gd

or perhaps install the php5-gd package via Synaptic Package Manager or KPackageKit.

PS -- I have lots of instructions for setting up Drupal6 on Ubuntu at:
[http://ubuntuguide.org/wiki/Drupal6_tips](http://ubuntuguide.org/wiki/Drupal6_tips)

or Kubuntu at:
[http://kubuntuguide.org/Drupal6_tips](http://kubuntuguide.org/Drupal6_tips)

---

### Post by theou huios on 2011-01-27
Solved it

But came up with a new problem.

When it asks about database name, I gave the name drupal. Which is exactly as in this [link]("http://www.jonathanmoeller.com/screed/?p=1732") . But the error which is coming up is

> In order for Drupal to work, and to continue with the installation  process, you must resolve all issues reported below. For more help with  configuring your database server, see the [installation handbook]("http://drupal.org/getting-started/install"). If you are unsure what any of this means you should probably contact your hosting provider.Failed to connect to your database server. The server reports the following message: *SQLSTATE[28000] [1045] Access denied for user 'theou'@'localhost' (using password: YES)*.

[LIST]
[*]Is the database server running?
[*]Does the database exist, and have you entered the correct database name?
[*]Have you entered the correct username and password?
[*]Have you entered the correct database hostname?
[/LIST]


Any mistake which I did?

---

### Post by perspectoff on 2011-01-27
> **theou huios said:**
> Solved it

But came up with a new problem.

When it asks about database name, I gave the name drupal. Which is exactly as in this [link]("http://www.jonathanmoeller.com/screed/?p=1732") . But the error which is coming up is



Any mistake which I did?

You do have MySQL (or PostgreSQL) installed, right?

Drupal does require an entire LAMP stack (meaning Apache2, MySQL or PostgreSQL, and PHP5). If you never installed all of them, the easiest way is:

 sudo tasksel install lamp-server

There's a lot of haphazard instructions out there. I looked at the link you posted -- those are incredibly complex and needlessly difficult instructions. They represent a method of installation from several years ago.

Clearly you haven't tried the Ubuntu/Debian package installation, which is far, far easier and automates many of those steps:

 sudo apt-get install drupal6

When you are asked which user will install the database, you want to use the root superuser and the password that was created when you installed MySQL (during the tasksel install lamp-server step, for example). If you don't remember it, you are SOL. You'll have to re-install MySQL.

The constellation of errors you posted all have something to do with MySQL configuration (or lack of it).

---

### Post by theou huios on 2011-01-27
Yup, I did installed it.

---

### Post by perspectoff on 2011-01-27
Ok, then I recommend you start over.

Erase the database (the name of the database does not matter, and drupal is as good as any).

mysql -u root -p
mysql> DROP DATABASE drupal;
mysql> quit

This series of command logs you in as the root superuser (of course you must remember your original MySQL installation password for the root user) and empties the drupal database (assuming one was created in the first place).

Now you can start over.

From the command line, reinstall drupal6:
 sudo dpkg-reconfigure drupal6

It will lead you through the questions that are a little easier to digest than manually setting up a database, granting permissions and whatnot (a process that is fraught with opportunities for error). 

If the package was never installed in the first place, just try:
 sudo apt-get install drupal6

See if that isn't easier. The questions will be:

    Configure database for drupal6 with dbconfig-common? Yes 
    Database type to be used by Drupal6: mysql 
    Password of your database's administrative user: mysqlrootpassword 
    MySQL application password for drupal6: mysqldrupal6password 

where mysqlrootpassword is the MySQL password for the original root superuser, and mysqldrupal6password is a new password you will create for use only with this Drupal database (can be anything).

As usual, you might want to wait for other suggestions to see which one makes more sense to you.

---

### Post by theou huios on 2011-01-27
Thanks for the help. I understood what mistake I did :P It's working now,

---

### Post by theou huios on 2011-01-27
:(:(  Looks like I again made a mistake.

After logging out, I tried to login again and for some strange reason, couldn't do it. So again I used the same method which perspectoff said. Dropped the database, create again n new one with a new user and granted all privileges. And then tried to log in 

Error        The website encountered an unexpected error. Please try again later.

> **Error message**

 *PDOException*: SQLSTATE[42S02]: Base table  or view not found: 1146 Table 'drupal.semaphore' doesn't exist: SELECT  expire, value FROM {semaphore} WHERE name = :name; Array (     [:name] => variable_init )  in *lock_may_be_available()* (line *165* of */var/www/includes/lock.inc*).
           

 

Looks like I am trying new things to screw it up :P:P 

By the way can anyone explain me how to see the database fields. I read in a forum that I can access mysql n then make changes. How do I go into mysqladmin> from mysql> ? Not being from CS back ground is making this tough to handle :)

---

