---
title: "Where's the AMP (Apache, MySQL, PHP)??"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by meantone on 2007-07-24
Hi,

Installed LAMP via Feisty Fawn Server and added the GUI GNome, but now that I'm attempting to install Drupal I don't see the AMP part?

Any ideas?

Thanks!

---

### Post by Koybe on 2007-07-25
I've nerver installed it trough the automatic installation. 

Apache web files are in /var/www
Apache config files are in /etc/apache2

Mysql commands are the same as on each system

Php is just linked with Apache and Mysql and should not need further configuration.

You can test it easily, create a info.php file in /var/www

It should contain > <? phpinfo(); ?>

Then try accessing it trough Firefox at [http://localhost/info.php](http://localhost/info.php)

If you need more informations please be more precise.

---

### Post by meantone on 2007-07-25
Thanks for the reply Koybe.  

I first installed Ubuntu 7.04 Feisty Fawn server with the LAMP components option.  Then being a Windoze guy I used the following commands to install the graphical desktop:

sudo apt-get update
sudo apt-get install ubuntu-desktop

When I did that the system prompted me for screen resolution and then booted into the GUI. 

I then followed the Drupal installation ([https://help.ubuntu.com/community/Drupal?highlight=%28drupal%29](https://help.ubuntu.com/community/Drupal?highlight=%28drupal%29)) which directed me to create sub directories off  /var/www/.  That's when I discovered that I didn't have a /var/www/ directory and it didn't seem that I had Apache, MySQL or PHP installed.

So I guess a couple of things could have happend:
1. The AMP components didn't get installed even though I selected them?
2. The GUI is somehow covering up access to the server layer?

Once again, I'm a windoze guy, so all this is still a bit like voodoo to me.

Thanks!

---

### Post by fluteflute on 2007-07-25
Try the following:
sudo apt-get install apache2
sudo apt-get install libapache2-mod-auth-mysql
sudo apt-get install libapache2-mod-php5
sudo apt-get install mysql-client-5.0
sudo apt-get install mysql-server-5.0
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin

---

### Post by meantone on 2007-07-25
Thanks, fluteflute.  I don't have my laptop with me know, but I'll try this later.

I'm surprised I have to do this since I thought the server install would have done it.  Is that not always the case or is this a required step I missed?

---

### Post by doodaa on 2007-07-25
Permissions issue? I know root owns /var/www.... not sure what other privs may be there by default. In NT terms the NTFS permissions may not be sufficient for your user account to see/traverse those directories.

---

