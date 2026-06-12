---
title: "upgrade error 6.06 LTS to 8.04 LTS"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by low-res on 2008-07-30
Hi i'm getting the following error trying to upgrade.

Don't have a clue what it is...

Fout tijdens het updaten

Tijdens de update is er iets misgegaan. De oorzaak is meestal een of
ander netwerkprobleem. Controleer uw netwerkverbinding en probeer het
opnieuw.

W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.bz2)
Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or
old ones used instead.


De oorspronkelijke toestand wordt hersteld

Afbreken
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done

---

### Post by Pumalite on 2008-07-30
You might want to try this:
sudo sed -i 's/dapper/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by low-res on 2008-07-31
Thanks for your response! Still running into issues though...

The upgrade hangs on trying to restart the kernel log deamon..

Setting up klogd (1.5-1ubuntu1) ...
Installing new version of config file /etc/init.d/klogd ...
 * Stopping kernel log daemon...                                         [ OK ]
 * Starting kernel log daemon...

Should I Ctrl-C it or try logging in trough port 9004 (yes, i'm upgrading via ssh, sorry should have mentioned it earlier.)

---

### Post by gjoellee on 2008-07-31
download and burn the hardy CD, and put it in while running Ubuntu and then upgrade

---

### Post by low-res on 2008-07-31
> **gjoellee said:**
> download and burn the hardy CD, and put it in while running Ubuntu and then upgrade

It's a VPS so I'm not able to put a CD-ROM in :(

---

### Post by low-res on 2008-07-31
The upgrade was finished after having some trouble starting the kernel log deamon. But it said it went ok.

So, I gave the machine a reboot... 

It works now :D 

Thanks very much Pumalite! Can you tell me what "sed -i 's/dapper/hardy/' /etc/apt/sources.list" actually does? I know sed is a kind of filter thing but can't figure out what the -i option does and the 's... Can you explain, please? Does it rename the lines in my sources.list or somthing? (Sorry, i'm still kinda n00b...)

---

### Post by Pumalite on 2008-07-31
> **low-res said:**
> Thanks for your response! Still running into issues though...

The upgrade hangs on trying to restart the kernel log deamon..

Setting up klogd (1.5-1ubuntu1) ...
Installing new version of config file /etc/init.d/klogd ...
 * Stopping kernel log daemon...                                         [ OK ]
 * Starting kernel log daemon...

Should I Ctrl-C it or try logging in trough port 9004 (yes, i'm upgrading via ssh, sorry should have mentioned it earlier.)
It probably happened because your Dapper was not fully updated before the upgrade.

---

