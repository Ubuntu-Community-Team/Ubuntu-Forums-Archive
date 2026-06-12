---
title: "upgrade/installation error"
date: 2006-04-04
forum: Installation &amp; Upgrades
---

### Post by ayandyan on 2006-04-04
i'm an newbie to ubuntu or linux in general. i appended sources to the sources.list file in order to update my ubuntu as instructed by the site: 
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
then as root, i ran: apt-get update
ubuntu began to download updates, packages, etc. now, when i try to install the packages or softwares, these error(s) occurs:

Gdk-WARNING **: locale not supported by Xlib at /usr/share/perl5/FrontEnd/Gnome.pm line 47, <> line 100.
Gdk-WARNING **: cannot set locale modifiers at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 47, <> line 100.
Gdk-WARNING **: locale not supported by Xlib at /usr/share/perl5/FrontEnd/Gnome.pm line 53, <> line 100.
Gdk-WARNING **: cannot set locale modifiers at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 53, <> line 100.
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: `install-info' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.

the filesystem however does contain the corresponding folders when i checked it.i dont know what d problem is. do i need to do something for Xlib to support it?or does it really have something to do with Xlib?what's install-info?did the update process not allocate it in the right place?sorry, for my questions.i just hope somebody can help me.
thank u very much.

---

### Post by localzuk on 2006-04-05
Could you please, firstly, show us a copy of your sources.list file?

---

