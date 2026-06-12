---
title: "[SOLVED] Update Manager on Previous Internet settings"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by rayyan on 2008-04-07
hello. 

well i know this has been addressed before but i think my problem is different.

ubuntu@ubuntu-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg                               
  Could not connect to 10.110.10.1:8080 (10.110.10.1). - connect (113 No route to host)
Err [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty Release.gpg                        
  Could not connect to 10.110.10.1:8080 (10.110.10.1). - connect (113 No route to host)
Err [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Translation-en_US             
  Could not connect to 10.110.10.1:8080 (10.110.10.1). - connect (113 No route to host)
20% [Connecting to 10.110.10.1 (10.110.10.1)] [Connecting to 10.110.10.1 (10.11




10.110.10.1 is the server of the previous lan network i was on that i used to use to connect to the internet. now I am on  dsl, ethernet modem (has usb as well). I can surf the itnernet easily, but the packet manager/update manager is still trying to use the previous internet settings i guess.

I am an ubuntu noob, so I have no idea what to do, help needed! 

thanks!

---

### Post by Partyboi2 on 2008-04-07
If you were/are using proxy setttings check in Synaptic Package Manager under network settings that they are set correctly. (System>Admin>Synaptic Package Manager>Settings>Preferences)

---

### Post by rayyan on 2008-04-08
> **Partyboi2 said:**
> If you were/are using proxy setttings check in Synaptic Package Manager under network settings that they are set correctly. (System>Admin>Synaptic Package Manager>Settings>Preferences)

its set to direct connect, i don't have proxy settings :?

---

### Post by rayyan on 2008-04-08
my friend just told me what to do:

solved it by checking the system\preferences\network proxy, it was put it to proxy

---

