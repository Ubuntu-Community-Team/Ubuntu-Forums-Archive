---
title: "trying to get Apache2 to work"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by spaceW on 2007-06-24
i want to start Apache and view the "It Works!" page at [https://localhost](https://localhost), but it's not working for me...

my immediate goals:
-see the "It Works!" page on http or https. (i think i might have it set up for SSL)
-know that i am doing something when i give this command: "sudo /etc/init.d/apache2 restart"

some installed packages: 
apache2, apache2-mpm-worker, apache2-utils, apache2.2-common, libapache2-svn
openssl, ssl-cert, libssl0.9.8

clues:
-i am new to ubuntu and could be missing something very basic
-when i try to start or restart Apache (sudo /etc/init.d/apache2 start) i get no output
-both access.log and error.log in "/var/log/apache2/" are blank
-there is no apache2.pid in "/var/run" (should there be?)
-i see nothing about Apache or httpd in the System Monitor
-i got nginx to host a "Welcome to nginx!" page on port 81 at [http://localhost:81](http://localhost:81)
-there is no "ssl" folder in /etc/apache2... one tutorial seemed to think there should be
-i got it to work on WindowsXP (not with secure socket layer though)

information about my system:
-i installed the Feisty 7.04 Server edition
-i got GNOME by apt-getting x-window-system-core and gnome-core rather than installing ubuntu-desktop
-i haven't installed very many other programs.  just MySQL and a few other random ones

longer term goals for my ubuntu machine:
-get a subversion repository working with Apache
-get Trac set up with that repository
-figure out some free DynamicDNS service to get a nice url
-maybe set up something like CruiseControl for a Ruby on Rails app in the svn repository
-and, if all goes well, host a modest home-made Rails app

so, am i just missing some package?
should i install libapache2-mod-ssl?
will i need PHP for anything?

i would really appreciate any help.

thanks,
space W

---

### Post by bbyte on 2007-06-26
I am also a novice user so my suggestions are rather limited.

You can go to System tab then Administration drop down and then Synaptic Package Manager.

I put apache in the search box and then scroll through the results and put a checkmark in Apache2 and it will pick up all the other necessary files and install them.  Sweet!  The localhost It works! comes right out of the box.

Hope this helps.

---

### Post by cmoman on 2007-06-28
is [http://localhost](http://localhost) working? not [https://localhost](https://localhost)

you're making a request for a ssl connection, you'll need the additional ssl modules for that.

---

### Post by Modernity on 2007-07-24
Out of the box Apache uses local host. To try it after install, open Firfox or web browser and use local host like this ```
 http://127.0.0.1
```, this might be easier for novice users.

---

