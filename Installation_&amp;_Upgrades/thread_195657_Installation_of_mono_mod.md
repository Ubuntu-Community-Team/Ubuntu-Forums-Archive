---
title: "Installation of mono_mod"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by tbresson on 2006-06-13
Just a little curious thing I noticed.

There are two different packages to choose from, the regular one, and the "version 2" one.

Like this:
libapache-mod-mono
mono-apache-server

and
libapache-mod-mono2
mono-apache-server2

Now I want to run the "version 2" so I select the libapache-mod-mono2 and it says it is dependent of the mono-apache-server.

But if I choose to install the mono-apache-server2 and then select the libapache2-mod-mono there's no dependencies.

I would think that when selecting the "version 2" component that it would be dependent of the "version 2" packages, but it's not.

I don't know if this has any consequences or not, but I thought I'd let someone know about it.

---

### Post by tbresson on 2006-06-13
can't delete this.. therefore this message.

---

### Post by ubnoobie on 2006-06-13
use aptitude interactively (sudo aptitude) to install the packages or package versions you want. you can deselect mono-apache-server and install mono-apache-server2 instead, after you've selected libapache2-mod-mono.

aptitude step by step:
[LIST=1]
[*]sudo aptitude
[*]/ (search box pops up)
[*]2-mod-mono (search term) & hit enter
[*]libapache2-mod-mono should be highlited, hit enter
[*]hit + to select package
[*]arrow down to mono-apache-server, hit enter
[*]hit - on mono-apache-server
[*]hit + then shift-M on mono-apache-server2 (+ to select, shift-M to turn it back into a 'dependancy installation')
[*]hit G to "GO" to summary screen
[*]examine changes to be made
[*]hit G to "GO" again, this starts the install
[/LIST]


or, try two separate apt-get commands:

sudo apt-get install mono-apache-server2

then

sudo apt-get install libapache2-mod-mono

---

### Post by tbresson on 2006-06-14
I just found out it seems to create problems when not selecting the packages that synaptec suggests.

It's weird though.
When selecting the mod_mono for apache2 all the dependencies it chooses are for Apache 1.x but it seems to only work when I do that.

I couldn't get it to work when I choose the apache 2 modules by myself.

Also I think the developers should add a dir (virtual?) to e.g. /var/www/asp and pre-config the httpd.conf with the loading of the mono-mod module and setting up the location of the asp.net files. It would then work out of the box.

Like this: 
LoadModule mono_module /usr/lib/apache2/modules/mod_mono.so
Alias /asp "/var/www/asp"
AddMonoApplications default "/asp:/var/www/var"
<Location /asp>
     SetHandler mono
</Location>

---

