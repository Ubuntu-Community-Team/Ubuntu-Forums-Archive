---
title: "Gui install on Ubuntu server"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by Goonie on 2006-09-23
Hi all

This is probably very silly but here goes... I wanted to try setting up a machine to function as a mail/web/ftp server for close friends and family. So I popped in a Ubuntu Server CD and chose to install a LAMP server (not sure what I was doing). That went fine I guess but being a complete newbie in most things Linux and even more clueless when it comes to servers, I decided I needed a gui to get things done. I then installed kdm and kde via apt but I can't get the gui started. What more needs to be done to get it running and also I wanted to ask you if you could recommend a simple setup for my particular server needs? I want to put up a web which allows users to log in and see a message board, a blogging option, image database, web mail and an ftp server.

If anyone can get me started in the right direction I would greatly appreciate it.

Thx
Goonie

P.s. Sorry if this post is in the wrong forum section, wasn't sure where to put it.

---

### Post by xolot1 on 2006-09-23
sudo apt-get install kubuntu-desktop

should install the kde ubuntu packages.
at least, sudo apt-get install ubuntu-desktop
worked for me 2 days ago for installing the gnome environment.

---

### Post by Goonie on 2006-09-23
thx for the quick reply :D

I did apt-get install ubuntu-desktop and things are happening now. I'll post my results after it's done.

Thx
Goonie

---

### Post by crazymonkey on 2006-09-23
If you really want to run a gui on your server i would recommend XFCE instead of KDE since its less hungry on ressources. If you only want it to manage the server you might want to take a look at [webmin]("http://www.ubuntuforums.org/showthread.php?t=195093"), it provide a web interface to manage the different part of your server and is much more light than a whole desktop.

Here are some sites you might take a look at for the different parts of you server, as for putting to whole thing together with login and password you will have to do some search because i have no clue.

Message board : [phpBB]("http://www.phpbb.com/")
Blog : [Wordpress]("http://wordpress.org/")
Photo gallery : [Coppermine]("http://coppermine-gallery.net/index.php")
FTP Server : there is alot of choice, [proftpd]("http://www.proftpd.org") have a nice admin gui
WebMail : That is something hard to setup, but you can start with [this thread]("http://flurdy.com/docs/postfix/") there is also [OpenXChange]("http://www.open-xchange.com/EN/developer/") and [Zimbra Mail]("http://www.zimbra.com/")

Good luck!

---

### Post by Goonie on 2006-09-24
Thx alot !

This will definately get me going :)

Goonie

---

### Post by crazymonkey on 2006-09-24
Just found this howto :[http://www.howtoforge.com/perfect_setup_ubuntu_6.06]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")
Hope it helps!

---

### Post by Goonie on 2006-09-25
Thx :)

I'll check this out for sure

Goonie

---

### Post by az on 2006-09-25
See here:
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

I would suggest Drupal for everything (blog, photo gallery, forums, etc...)
[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

---

### Post by crazymonkey on 2006-10-01
thanks azz, its the first time i hear about Drupal and it seems very nice!

---

