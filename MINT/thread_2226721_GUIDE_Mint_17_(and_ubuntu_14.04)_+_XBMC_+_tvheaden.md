---
title: "GUIDE: Mint 17 (and ubuntu 14.04) + XBMC + tvheadend"
date: 2014-05-28
forum: MINT
---

### Post by Janiporo on 2014-05-28
Usable for 32 bit operating systems.

EDIT: Edited to more "wiki" like layout:

I tried to update repository "the normal way" from terminal but it would not work, so here we go (this is known and reported bug) so I made this:
```
sudo gedit /etc/apt/sources.list
```
and I added to the end of it these two lines:
deb [http://apt.tvheadend.org/beta](http://apt.tvheadend.org/beta) saucy main 
deb-src [http://apt.tvheadend.org/beta](http://apt.tvheadend.org/beta) saucy main

(At this time I installed "sudo apt-get install debian-archive-keyring", but I think it is not mandatory)

GPG-key thingie was not mandatory in Mint, Ubuntu reminded that it is missing.
To recive the GPG key:
```
sudo gpg --keyserver subkeys.pgp.net --recv-keys B42317285E12C7CF
``` 

To add the key to the key ring:
```
sudo gpg --armor --export B42317285E12C7CF | sudo apt-key add -
``` 

Then install tvheadend:
```
sudo apt-get update
sudo apt-get install tvheadend
```

Installed XBMC version 13 (Gotham) like so:
```
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install xbmc xbmc-bin xbmc-pvr-tvheadend-hts
```

 Now they are both installed and work perfectly together. "xbmc-pvr-tvheadend-hts" is needed, without it XBMC will freezes when enabling live TV.

---

### Post by Janiporo on 2014-05-29
Installed mint 17 -64bit and got another problem, can not add ppa's (for example sudo add-apt-repository ppa:team-xbmc/ppa), I got error: "'Cannot add PPA: 'No JSON object could be decoded'", and later on another error --> so I will do that manually like this:

add these also to the sources.lst also
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main
 deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main

receive and install pgp-key:

 ```
gpg --keyserver keyserver.ubuntu.com --recv-keys 91E7EE5E
gpg --export --armor 91E7EE5E | sudo apt-key add -
```

 Also had to change saucy --> trusty / and beta to stable.
deb [http://apt.tvheadend.org/stable](http://apt.tvheadend.org/stable) trusty main 
deb-src [http://apt.tvheadend.org/stable](http://apt.tvheadend.org/stable) trusty main

I fixed the ppa adding but do not remember how. Anyway, this is one way to do it. The hard way :D

---

