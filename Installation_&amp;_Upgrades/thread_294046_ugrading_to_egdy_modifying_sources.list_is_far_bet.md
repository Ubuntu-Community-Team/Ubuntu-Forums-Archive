---
title: "ugrading to egdy modifying sources.list is far better..."
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by bullgr on 2006-11-06
hi...

i am ubuntu user since hoary and i upgrade until dapper always
modifying the file sources.list and then i do
sudo apt-get update
sudo apt-get dist-upgrade
and i newer had problems upgrading...

i upgrade with this method from hoary to breezy and
from breezy to dapper.

a few days ago i wanted to upgrade from dapper to edgy with the same method, and when i saw in the forum this sticky post

[http://www.ubuntuforums.org/showthread.php?t=286599](http://www.ubuntuforums.org/showthread.php?t=286599)

> [I]Please, people; if you plan on upgrading to Edgy Eft 6.10, use the OFFICIAL upgrade method:

$ gksu "update-manager -c"

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.[/I]


i was thinking that they know's something more...
and so, i desided to use the gksu "update-manager -c" method.

but after that, the x server was broken (ati drivers?)
and i must restore the dapper ghost image back...

after the restoring i upgrade with the "traditional" method and
all wend perfect!!! no broken x server (like many users,
as i read in the forum using gksu "update-manager -c").

finaly i trust more the terminal apt-get method even in the updates too... i don't know if it's good to encourage users to upgrade with gksu "update-manager -c" than apt-get...

for me it's wrong...

---

### Post by neildarlow on 2006-11-06
I did the apt-get update, apt-get dist-upgrade method but there were a number of issues in doing it:

1) xserver-xorg was removed from my system
2) A number of xorg packages were held-back and needed manual resolution
3) A number of python2.4-* packages which had been superseded by python-* packages were held-back
4) gnome-keyring-manager was not installed
5) I was left with a significant number of obsolete packages which needed manual resolution

I was able to fix these issues but others might not. If the official upgrade procedure addresses such problems then it is to be recommended.

---

### Post by reyfer on 2006-11-06
The thing is that BOTH procedures are official, since BOTH procedures are being recommended by Ubuntu and Kubuntu developers
 The "Update manager -c" method  [http://www.ubuntuforums.org/showthread.php?t=286599](http://www.ubuntuforums.org/showthread.php?t=286599)
 
 The apt-get method [http://www.ubuntuforums.org/showthread.php?t=285099](http://www.ubuntuforums.org/showthread.php?t=285099)

Plus BOTH procedures appear here [https://wiki.ubuntu.com/EdgyReleaseNotes#head-b07f8bdf28ae0444c03e1a61110c683c77e56cd0](https://wiki.ubuntu.com/EdgyReleaseNotes#head-b07f8bdf28ae0444c03e1a61110c683c77e56cd0)

---

