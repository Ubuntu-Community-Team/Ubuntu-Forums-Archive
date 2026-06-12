---
title: "Error Upgrading Feisty Fawn to Gutsy Gibbon"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by mattmarq on 2007-11-03
When upgrading from Feisty Fawn to Gutsy Gibbon I get this error in the console:
warning: could not initiate dbus
extracting '/tmp/tmpj9WMSh/gutsy.tar.gz'
authenticate '/tmp/tmpj9WMSh/gutsy.tar.gz' against '/tmp/tmpj9WMSh/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

In the update manager it indicates the following repositories could not be reached:

[http://mirror.randumb.org/darkmagez/repo/dists/feisty-darkmagez/Release.gpg:](http://mirror.randumb.org/darkmagez/repo/dists/feisty-darkmagez/Release.gpg:) Could not resolve 'mirror.randumb.org'
[http://mirror.randumb.org/darkmagez/repo/dists/feisty-darkmagez/games/i18n/Translation-en_CA.bz2:](http://mirror.randumb.org/darkmagez/repo/dists/feisty-darkmagez/games/i18n/Translation-en_CA.bz2:) Could not resolve 'mirror.randumb.org'
[http://mirror.randumb.org/darkmagez/repo/dists/feisty-darkmagez/games/binary-i386/Packages.gz:](http://mirror.randumb.org/darkmagez/repo/dists/feisty-darkmagez/games/binary-i386/Packages.gz:) Could not resolve 'mirror.randumb.org'
[http://www.nicotine-plus.org/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://www.nicotine-plus.org/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found
[http://wxpython.wxcommunity.com/apt/ubuntu/feisty/Packages.gz:](http://wxpython.wxcommunity.com/apt/ubuntu/feisty/Packages.gz:) 404 Not Found
[http://wxpython.wxcommunity.com/apt/ubuntu/feisty/Sources.gz:](http://wxpython.wxcommunity.com/apt/ubuntu/feisty/Sources.gz:) 404 Not Found

I am 100% my internet connection is working... so I am not sure what is going on. Any help would be greatly appreciated. I AM SO EXCITED FOR GUTSY!!!!

Sincerely,
Matthew

---

### Post by linuxwizard on 2007-11-03
Try removing or disable any repos you added to your source. Than try to upgrade again.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or [COLOR="Red"]complicate your upgrade.[/COLOR]
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

