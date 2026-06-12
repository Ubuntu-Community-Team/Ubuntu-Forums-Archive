---
title: "need to install lamp stack"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by jimeast on 2013-01-19
on the ubuntu site I followed the following instructions:
To install the default LAMP stack in Ubuntu 10.04 and above
First install tasksel...

$ sudo apt-get install tasksel
... and then the LAMP stack:

$ sudo tasksel install lamp-server

It looked like it installed. I don't know what to do now. On Windows you just find the xampp folder and put stuff you want to test in htdocs folder and there's a control panel for starting and stopping services. Maybe I'm looking in the wrong places but I don't see a xampp folder let alond a htdocs folder and I have no idea how to start and stop Apachee, PHP or MySQL. Hopefully someone here has been through this and knows what I need to do next.

---

### Post by mörgæs on 2013-01-20
Localhost points to /var/www . 

You might need to open file and directory permissions.

---

### Post by Lars Noodén on 2013-01-20
To add to what mörgæs wrote, if you are the only user of your machine then it is enough to change ownership of /var/www.  That is of course only the default and if you would like to move it or add additional virtual hosts, then you can have other directories.

Apache and MySQL get started automatically when your machine starts.  You can look in /etc/init/ if you are curious about the Upstart script that runs them.  You can start or stop them the same way you would start any other services on your machine.

---

### Post by matt_symes on 2013-01-20
Hi

As [[COLOR=#DD4814]**mörgæs**[/COLOR]]("http://ubuntuforums.org/member.php?u=939075") stated, the default folder is /var/www but this can be changed by editing the file...

```
/etc/apache2/sites-available/default
```

This is the default virtual host for apache. You can add other virtual hosts easily enough.

The apache service can be started, stopped and restarted with..
```

sudo service apache2 stop
sudo service apache2 start
sudo service apache2 restart
```You also have

```
sudo service apache2 reload
```Here is some information to get you started.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Kind regards

---

