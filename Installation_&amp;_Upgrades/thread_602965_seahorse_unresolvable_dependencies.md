---
title: "seahorse unresolvable dependencies"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by ketzie on 2007-11-04
Hi all,

I've been trying to install seahorse  2.20 for Gutsy, and I get the following:

Depends: libgpgme11 (>=1.0.1) but it is not installable


How do I resolve these dependencies? seahorse:
 
Regards,

Ketzie

---

### Post by TechnoJunky on 2007-11-15
Why do you say that it's not installable?  Is it because you can't find it in adept?  have you tried aptitude?

---

### Post by meurrens on 2007-11-19
Hello,

**the last version of seahorse is : 2.20.1**

[http://live.gnome.org/Seahorse](http://live.gnome.org/Seahorse)
[http://www.gnome.org/projects/seahorse/download.html](http://www.gnome.org/projects/seahorse/download.html)
[http://ftp.gnome.org/pub/GNOME/sources/seahorse/2.20/seahorse-2.20.1.tar.gz](http://ftp.gnome.org/pub/GNOME/sources/seahorse/2.20/seahorse-2.20.1.tar.gz)

I recently compiled it on Ubuntu 7.10 . Here are my related notes.

[B]list of packages installed before compiling seahorse 2.20.1
(probably really too much...:()
use synaptic to make sure these packages are installed :
[/B]
make
gcc
g++ (will install libc6-dev)
libc6 , libc6-i686 , libc6-dev
zlib1g , zlib1g-dev
libgtk2.0-0 , libgtk2.0-dev
libgpgme11 , libgpgme11-dev (1.1.5)
gnupg
dbus , libdbus-1-3 , libdbus-glib-1-2 , libdbus-glib-1-dev
libgnomeui-0 , libgnomeui-dev
libglade2-0 , libglade2-dev
gconf2 
libgnomevfs2-0 , libgnomevs2-dev
openssh-client
firefox
epiphany-browser
libnautilus-extension1 , libnautilus-extension-dev 

**configure, compile and install :**

cd Desktop
cd seahorse-2.20.1
./configure --prefix=/usr
make
sudo make install

Hope this helps,

---

