---
title: "easily share files on ubuntu"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-02-12
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

alt + f2

gnome-terminal

run

in that terminal drop this block of code

```

sudo apt-get install apache2

```

then give it your su password.... and say YES install apache

now to get cleaver with the symlinking...

```

sudo mv /var/www $HOME/www
sudo ln -s $HOME/www /srv/www
sudo ln -s /srv/www /var/www
sudo mv /usr/lib/cgi-bin /usr/lib/cgi-bin.backup
sudo ln -s /var/www/cgi-bin /usr/lib/cgi-bin

```

now any files you move to /home/$USER/www will show up @ 127.0.0.1....

to browse your systems files

alt + f2

nautilus

run

it will also show up at your ip address shown by running this block of code

```

sudo ifconfig

```

---

