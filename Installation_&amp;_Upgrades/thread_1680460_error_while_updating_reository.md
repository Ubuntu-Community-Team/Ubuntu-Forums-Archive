---
title: "error while updating reository"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by debd on 2011-02-02
I have a problem regarding package updates.
whenever I try 
sudo apt-get update
it returns an error 
[QUOTE
[http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6[/QUOTE]



the complete output is here:


> Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick Release.gpg
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/main Translation-en 
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/main Translation-en_IN 
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/multiverse Translation-en 
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/multiverse Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/restricted Translation-en 
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/restricted Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/universe Translation-en 
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/universe Translation-en_IN
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates Release.gpg 
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/main Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/main Translation-en_IN
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg 
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en 
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_IN 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg 
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en 
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B] 
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en 
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_IN 
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/multiverse Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/universe Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/universe Translation-en_IN
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security Release.gpg 
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/main Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/main Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/multiverse Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release 
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/multiverse Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/restricted Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/restricted Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/universe Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/universe Translation-en_IN
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick Release 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates Release 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security Release 
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B] 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/main Sources 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/restricted Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/universe Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/multiverse Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/main i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/restricted i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/universe i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/multiverse i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/main Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/restricted Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/universe Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/multiverse Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/main i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/restricted i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/universe i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/multiverse i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/main Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/restricted Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/universe Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/multiverse Sources 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/main i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/restricted i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/universe i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/multiverse i386 Packages 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages 
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg 
Ign [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable/non-free Translation-en 
Ign [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable/non-free Translation-en_IN 
Hit [http://deb.opera.com](http://deb.opera.com) stable Release 
Hit [http://deb.opera.com](http://deb.opera.com) stable Release 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release 
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,087B] 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources 
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]
Ign [http://ppa.launchpad.net/fta/ubuntu/](http://ppa.launchpad.net/fta/ubuntu/) lucid/main Translation-en
Ign [http://ppa.launchpad.net/fta/ubuntu/](http://ppa.launchpad.net/fta/ubuntu/) lucid/main Translation-en_IN 
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources/DiffIndex 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages/DiffIndex 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages 
Fetched 2,939B in 9s (323B/s) 
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
any help is appreciated.

---

### Post by debd on 2011-02-02
please help somebody.....

by the way I cant install evnyng-qt

whenever I enter
sudo apt-get install evnyng-qt

it returns:
> E: Unable to locate package envyng-qt

does it have to do anything with the repository update problem?
....I already have the universe repository enabled needed for the envy installation.

thanks in advance for any help. :)

---

### Post by bapoumba on 2011-02-02
Looks like you have maverick installed and that ppa giving you the error is for lucid.
Please try to remove the ppa from your sources.list (or from the repositories in Synaptic) and reload the file before trying an update.

---

### Post by Old_Grey_Wolf on 2011-02-02
Try entering the following in a terminal and updating again:
```
gpg --keyserver keyserver.ubuntu.com --recv 632D16BB0C713DA6
gpg --export --armor 632D16BB0C713DA6 | sudo apt-key add -
```
To update enter the following in the terminal;
```
sudo apt-get update
```

debd,

Let me know if it worked for you.

---

### Post by debd on 2011-02-03
thank u all for your effort and help.

the thing is ..I had more problems in my Ubuntu installation. so I just did a reinstall and now it doesn't show any error.

thanks.

but what about the envy installation error? is still shows the same info:

> sudo apt-get install envyng-qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package envyng-qt


help?

---

### Post by arpanaut on 2011-02-03
envyng-qt has been discontinued.

jockey-gtk, AKA-> hardware drivers/additional drivers has replaced it.

Alberto Milone is still involved in jockey and bringing better driver integration into Ubuntu.

---

