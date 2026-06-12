---
title: "Move Drupal Site from Windows to Ubuntu"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by eroeurbano on 2010-06-05
Dear all,
after a long thinking I decided to move my working web-site based on Drupal from a Windows Machine to an Ubuntu one.
I followed these steps:
1)put the Drupal website offline
2) backed up the mysql database using mysqldump
3) copied the "htdocs" directory containing my Drupal website.

On the Ubuntu machine I installed a LAMP server using the preconfigured installation from Synaptic.
I created the username for drupal Mysql user,
imported the database in mysql.
I copied all the drupal files in the /var/www
directory.
I enabled the rewrite module (a2enmol rewrite)
and restarted the Apache server.

When trying to access my website [http://localhost/](http://localhost/)
firefox ask me if I want to download the PHTML file.

I know is something to do with the fact that I have to enable
the index.php file, but I have no idea on how to do it.

Also it would be great if some of you might give me advices about
some wrong step I made in moving the website,
and give advices on how to make the migration from one machine to an other as painless as possible.

I thank all of you in advance for your help.

Cheers, -Luca

---

