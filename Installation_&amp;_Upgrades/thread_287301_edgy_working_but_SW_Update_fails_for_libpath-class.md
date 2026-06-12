---
title: "edgy working but SW Update fails for libpath-class-perl , acidbase , python-xmpp"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by sjs7 on 2006-10-28
Hi,
My dapper->edgy update worked but i had some failures...

at this point my Software Update no longer works.

it is clogged up by a couple of ungettable packages for some reason.

I did:
gksu "update-manager -c -d"
It got 90% through.

I tried
gksu "apt-get -f install"
same results, below....

Software Update now says I need to update this:
libpath-class-perl
from version 0.15-1 to 0.15-1 

Everytime I get whats below.  Can someone help me decipher this?  Thank you.
What does this mean?

dbconfig-common: flushing administrative password
dpkg: error processing acidbase (--configure):

```

(Reading database ... 130615 files and directories currently installed.)
Preparing to replace libpath-class-perl 0.15-1 (using .../libpath-class-perl_0.15-1_all.deb) ...
Unpacking replacement libpath-class-perl ...
Setting up acidbase (1.2.5-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/acidbase.conf
Replacing config file /etc/acidbase/database.php with new version
dbconfig-common: flushing administrative password
dpkg: error processing acidbase (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-xmpp (0.3.1-1.1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/xmpp/session.py
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/xmpp/session.py
dpkg: error processing python-xmpp (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libpath-class-perl (0.15-1) ...
Errors were encountered while processing:
 acidbase
 python-xmpp
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up acidbase (1.2.5-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/acidbase.conf
Replacing config file /etc/acidbase/database.php with new version
dbconfig-common: flushing administrative password
^Adpkg: error processing acidbase (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-xmpp (0.3.1-1.1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/xmpp/session.py
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/xmpp/session.py
dpkg: error processing python-xmpp (--configure):
 subprocess post-installation script returned error exit status 1


```

---

### Post by sjs7 on 2006-11-01
Anyone, please?

I am stuck with a functioning Edgy but I can't use Software Update any more
Thank you.

---

### Post by sjs7 on 2006-11-01
whoops delete this post please (not this thread, still need help)

---

### Post by curly_nostrill on 2007-03-03
I get this error (or something similar) whenever I install 'slimserver' from the slimdevices repo.  This started to happen after I upgraded dapper to edgy in place from a custom dapper distribution, 'ubuntu mmc'.  I've un/re installed slimserver a few times.  I don't remember if I tried the 'official' ubuntu version since I do remember being afraid it might foo things up from my 6.5.1 install.

In my case I get a software update notification for libpath-class-perl 1.5.1 > libpath-class-perl 1.5.1 and it never actually updates.  I assume there is some file diff between the lib provided by slimdevices and the file in the Universe repository since when I commented out the slimdevices repo the notification remained. I commented out the Universe repo in synaptic and the update note finally goes away.  

I had slimserver installed and working well in an official dapper install and in ubuntu mmc.  I don't think I ever tried it with a straight up clean edgy install.

I'm thinking of compiling slimserver again like in the old days.

---

