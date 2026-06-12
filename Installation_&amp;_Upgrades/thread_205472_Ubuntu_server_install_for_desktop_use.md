---
title: "Ubuntu server install for desktop use?"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by nameiwantistaken on 2006-06-28
I'm building an Ubuntu machine that will be used mostly for desktop use but I want to use the server install for the easy install of LAMP.  I'm not sure why this wasn't included in the desktop build (most people I know work on things locally before deploying them), but my worry is that the server won't have things contained in the desktop build.  Will it have a GUI I can use and all of the normal features of Ubuntu?  Anyone have any input?

---

### Post by az on 2006-06-28
[QUOTE=nameiwantistaken]I'm building an Ubuntu machine that will be used mostly for desktop use but I want to use the server install for the easy install of LAMP.  I'm not sure why this wasn't included in the desktop build (most people I know work on things locally before deploying them), but my worry is that the server won't have things contained in the desktop build.  Will it have a GUI I can use and all of the normal features of Ubuntu?  Anyone have any input?[/QUOTE]
You can install the turn-key LAMP server.  The boot into your box, log in and run


sudo apt-get install linux-386 ubuntu-desktop

and you have both the desktop and the LAMP server.

They do not conflict.  The server install cd does not contain the desktop because 
1. it is not needed to run the server, in fact it is preferable to not run unneccesary services on a production server.
2. The ubuntu-desktop packages can easily be installed from the repositories.

---

### Post by nameiwantistaken on 2006-06-28
OK, so server install and then the apt-get of the desktop.  That's some good azz advice.  Thanks.  :)

---

### Post by BakCompat on 2006-06-28
I've installed Dapper Server on a couple machines already, but have wanted to do desktop installs as well. I did apt-get the desktops once i figured out the package name.. ubuntu-desktop, kubuntu-desktop, or edubuntu-desktop. What i'd like ot know, tho, is if there is a way to install the desktop from local files, rather than having to apt-get them.. Downloading 400 megs or so isn't a network problem with bandwidth, but a time issue. How can i install a desktop on top of a server install (if i feel the need to) other than via apt-get over internet? I surmise that remastering a server cd with the necessary packages would be possible.. But changing the sources.list to point to say, the desktop install cd, won't work because those are compiled for a different kernel right? Or am i thinking in a completely weird turn here and need to approach it from a different mentality?

---

### Post by az on 2006-06-28
[QUOTE=BakCompat]Downloading 400 megs or so isn't a network problem with bandwidth, but a time issue. How can i install a desktop on top of a server install (if i feel the need to) other than via apt-get over internet? I surmise that remastering a server cd with the necessary packages would be possible.. But changing the sources.list to point to say, the desktop install cd, won't work because those are compiled for a different kernel right? Or am i thinking in a completely weird turn here and need to approach it from a different mentality?[/QUOTE]

I can fetch 400 megs in about the same time it would take to get each package from a cdrom.

You cannot add the Desktop cd as a complete repo since it is a pre-installed system and not just a repository of uninstalled packages.  You can do it with the alternate install cd.  Download it, install using your server cd and then boot, log in and type

sudo apt-cdrom add

and then insert the alternate cd when asked.

You now have the alternate cd as part of your repos.

---

### Post by PaulWhyteGelWorks on 2006-06-29
[QUOTE=azz]You can install the turn-key LAMP server.  The boot into your box, log in and run


sudo apt-get install linux-386 ubuntu-desktop

and you have both the desktop and the LAMP server.

They do not conflict.  The server install cd does not contain the desktop because 
1. it is not needed to run the server, in fact it is preferable to not run unneccesary services on a production server.
2. The ubuntu-desktop packages can easily be installed from the repositories.[/QUOTE]

This looks great just what I was looking for to get a desktop for my LAMP server install currently with just a command line.
Tried it and got after the Reading package lists ...then Building dependency tree...
E: Couldn't find package ubuntu-desktop

Have I missed something? Is there a way to allow access to more packages over the net?

Experienced users help would be greatly appreciated! New User :confused:

---

### Post by az on 2006-06-29
[QUOTE=PaulWhyteGelWorks]This looks great just what I was looking for to get a desktop for my LAMP server install currently with just a command line.
Tried it and got after the Reading package lists ...then Building dependency tree...
E: Couldn't find package ubuntu-desktop

Have I missed something? Is there a way to allow access to more packages over the net?

Experienced users help would be greatly appreciated! New User :confused:[/QUOTE]
I forgot to mention to you to add the main and restricted repositories to your /etc/apt/sources.list.

Just uncomment the appropriate line, save and the run

sudo apt-get update


and then continue.

Sorry.

---

### Post by Gwystyl on 2006-06-29
I want to do it the other way around. I have de desktop CD installed and now want to install LAMP. I installed apache2, mysql, php and myphpadmin apart from each other, but I can t seem to get mysql to work.
I tried to follow both the mysql and phpmyadmin install pages, but they are probably for another linux distro. After some searching I think I found all the necessary files, but it won t work.
Is there a step-by-step how-to to install and setup mysql and phpmyadmin on Ubuntu desktop?
Im quite a linux n00b but I want to try some web-based applications which require mysql and php....

---

### Post by az on 2006-06-29
[QUOTE=Gwystyl]
Is there a step-by-step how-to to install and setup mysql and phpmyadmin on Ubuntu desktop?
Im quite a linux n00b but I want to try some web-based applications which require mysql and php....[/QUOTE]
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by nudaz on 2006-06-29
Thankyou azz - the alternate desktop cd, and apt-cdrom worked a treat!
Still can't get past proxy 407 errors trying to use apt-get, so thank you heaps!

---

### Post by Gwystyl on 2006-06-30
[QUOTE=azz][https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)[/QUOTE]

I found that one a little while after my last post. It still gave some problems, but when I installed mysqladmin I could finally set a password for root and after that install phpmyadmin.
Apparantly it dous make a difference if you choose 'properties --> permissions' on a directory in nautilus and mark all options or do 'chmod 777 dirname' in a root terminal. The latter worked.

---

