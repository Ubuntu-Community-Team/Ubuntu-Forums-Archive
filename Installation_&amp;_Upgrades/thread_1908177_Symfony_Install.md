---
title: "Symfony Install"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by OldManRiver on 2012-01-12
All,

I was looking for right place for this thread and thought that "3rd Party Projects" was the right place, but there is no "New Thread" capability there, so posting here.

I installed Symfony and have some weird problems and errors.  The default version, in Synaptic is 1.4.16, in installs error free but does not work.  So I created a script to install it and create the projects
```

#! /bin/bash
# symfony-setup.sh
# Install Symfony and Create Initial Project
# Must be execute from sudo su user

apt-get install php-pear
pear channel-discover pear.symfony-project.com
pear install symfony/symfony-1.4.16

cd /var/www
mkdir proj1
cd proj1
symfony generate:project proj1
symfony configure:database "mysql:host=localhost;dbname=proj1" UID PWD
symfony generate:app frontend
cd web
ln -s /usr/share/php/data/symfony/web/sf/

cd /var/www
mkdir proj2
cd proj2
symfony generate:project proj2
symfony configure:database "mysql:host=localhost;dbname=proj2" UID PWD
symfony generate:app frontend
cd web
ln -s /usr/share/php/data/symfony/web/sf/

```

I get these errors of:

> There are no tasks defined in the "doctrine" namespace.  
                                           
Task "configure:database" is not defined.  


Additionally the config.php file that comes with Symfony gives errors on the folders:

app/cache/
app/logs/

On IRC and in the manuals they say to set permissions to 777, which is outright insult and total security violation.

There has to be a work arround on this, so hope some advance user knows it as this no one should ever even suggest 777 let alone implement it.

This config file is also calling for SQL-Lite, but I went to the .ini file and changed the DB to MySQL, so wondering why I still get this message.

I also went back to IRC and was told the commands they are issuing are "helper scripts", but if it is not web-enabled, why would someone call this a more advanced framework platform?

Where are the GUIs and automation needed for this platform?

Anyway making this write-up of the problem so I can direct people wanting to help including those from IRC to this thread.

All help appreciated!

Thanks!

OMR

---

### Post by raja.genupula on 2012-01-12
Hi actually i am not sure about this , not much aware .but i got this [http://ailoo.net/2009/03/set-up-symfony-12-on-debian-ubuntu/](http://ailoo.net/2009/03/set-up-symfony-12-on-debian-ubuntu/)

hope it will help you

---

### Post by OldManRiver on 2012-01-12
All,

Was actually using HOWTOs from:

[http://smronju.wordpress.com/2010/07/21/getting-started-with-symfony/](http://smronju.wordpress.com/2010/07/21/getting-started-with-symfony/)

and 

[http://bikramkawan.com.np/install-symfony-ubuntu-1004-1104-step-step/](http://bikramkawan.com.np/install-symfony-ubuntu-1004-1104-step-step/)

because the install from snaptic, though error free, did not produce anything.

Those did not cover setting up apache for hanling projects, had to find that from:

[http://www.symfony-project.org/cookbook/1_0/en/web_server](http://www.symfony-project.org/cookbook/1_0/en/web_server)

Since I'm getting task related errors, think my answer is on:

[http://www.symfony-project.org/reference/1_4/en/16-Tasks#chapter_16_sub_doctrine_build](http://www.symfony-project.org/reference/1_4/en/16-Tasks#chapter_16_sub_doctrine_build)

but none of this is making sense to me just yet, so still fishing for answers.

Thanks!

OMR

---

### Post by OldManRiver on 2012-01-16
All,

OK down to trying to get bundles to work and not working, so still need help.

Thanks!

OMR

---

### Post by garak on 2012-01-20
> **OldManRiver said:**
> All,

OK down to trying to get bundles to work and not working, so still need help.

Thanks!

OMR

There's no bundles in symfony 1.4, that uses plugins instead.
Bundles are for Symfony2

---

### Post by OldManRiver on 2012-04-02
All,

I think I stated that I was attempting to upgrade to 2.x, but not sure.

OMR

---

