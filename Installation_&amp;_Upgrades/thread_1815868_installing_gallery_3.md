---
title: "installing gallery 3"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-08-01
first download the latest gallery source from [http://gallery.menalto.com/](http://gallery.menalto.com/)

unpack, move gallery 3 to web site directory....  usually /var/www  (i have $HOME/web/www directory symlinked to /srv/www and /var/www as a symlink of that....  so i can have my user edit its own folder and have the system spit it out as web and have the files locked down to powerless user....)

while in website directory

mkdir var
sudo chown www-data var/
sudo chgrp www-data var/

because were keeping this as locked down as possible.  trying to avoid chmod 777 as much as possible because its really insecure....


then enter your mysql root pass and it will create your password and username for gallery3, change that immediately to your password.  making a mysql user that is locked down for this would be a good idea.....  im going to rebuild this post to include that.


--------------------experimental------------------------------
turn on phpmyadmin....  phpmyadmin is insecure and should be disabled when you are done manipulating databases with it.

add a locked down user named gallery.  log into phpmyadmin as your mysql root user, go to the privileges tab and add new user.  name the user gallery, and tell phpmyadmin to create a database with the same name.  go into the database settings and "grant" admin to gallery over the specific database.

then go back to the gallery webinstaller and use gallery for database and gallery for user.

all looks well, adding comment to phpmyadmin alias...

ill return to clean this up in a few

---

