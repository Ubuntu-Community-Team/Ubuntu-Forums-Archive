---
title: "Gutsy Upgrade Unsuccessful: &quot;Unable to resolve packages&quot;"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by nkwu on 2007-10-20
When I'm upgrading from Feisty 7.04 to Gutsy using the update manager I get this error:

"Error Occured during update <blah blah>:"

> Failed to fetch http://packages/dfreer.org/dists/feisty/Release.gpg Could not resolve 'packages'
Failed to fetch http://packages/dfreer.org/dists/feisty/main/i18n/Translation-en_CA.bz2 Could not resolve 'packages'
Failed to fetch http://packages/dfreer.org/dists/feisty/main/binary-i386/Packages.gz Could not resolve 'packages'


when i run

```
sudo aptitude -update
```

I get the following:

> Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_CA
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_CA
[B]Err http://packages feisty Release.gpg                                          
  Could not resolve 'packages'
[/B]Get:1 http://ubuntu.mirror.rafal.ca feisty Release.gpg [191B]                   
Ign http://ubuntu.mirror.rafal.ca feisty/main Translation-en_CA
Ign http://ubuntu.mirror.rafal.ca feisty/restricted Translation-en_CA
Ign http://ubuntu.mirror.rafal.ca feisty/universe Translation-en_CA
Ign http://ubuntu.mirror.rafal.ca feisty/multiverse Translation-en_CA
Get:2 http://ubuntu.mirror.rafal.ca feisty-updates Release.gpg [191B]
Ign http://ubuntu.mirror.rafal.ca feisty-updates/main Translation-en_CA
Ign http://ubuntu.mirror.rafal.ca feisty-updates/restricted Translation-en_CA
Get:3 http://ubuntu.mirror.rafal.ca feisty-security Release.gpg [191B]
Ign http://ubuntu.mirror.rafal.ca feisty-security/main Translation-en_CA
[B]Err http://packages feisty/main Translation-en_CA 
  Could not resolve 'packages'[/B]
Ign http://ubuntu.mirror.rafal.ca feisty-security/restricted Translation-en_CA
Ign http://ubuntu.mirror.rafal.ca feisty-security/universe Translation-en_CA
Ign http://ubuntu.mirror.rafal.ca feisty-security/multiverse Translation-en_CA
Hit http://ubuntu.mirror.rafal.ca feisty Release  
Ign http://packages feisty Release                                     
Ign http://packages feisty/main Packages                               
Hit http://ubuntu.mirror.rafal.ca feisty-updates Release
Hit http://ubuntu.mirror.rafal.ca feisty-security Release
Hit http://ubuntu.mirror.rafal.ca feisty/main Packages                 
[B]Err http://packages feisty/main Packages                               
  Could not resolve 'packages[/B]'
Hit http://ubuntu.mirror.rafal.ca feisty/restricted Packages           

[...]

Hit http://ubuntu.mirror.rafal.ca feisty-security/multiverse Packages
Fetched 573B in 1s (472B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache


I know the problems are related but I have no clue where to start to solve it. Any help? I'm relatively new to Ubuntu, I wasn't sure if I was supposed to put this in the newb forum.

Thanks!

---

### Post by nkwu on 2007-11-03
^^?

---

### Post by zvacet on 2007-11-04
```
gksudo gedit /etc/apt/sources.list
```

Put # in front of every third party repo and save and close.
```
sudo aptitude update
```

In system>administration>software sources select main server.

---

