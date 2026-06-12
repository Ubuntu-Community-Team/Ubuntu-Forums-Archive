---
title: "Proxy problem"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by unknownlaopoet on 2007-06-21
I had set up my proxy wrong earlier, but after changing proxy in pereferences it still sees the old proxy when i try to update

here is what i did



usr@usr:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
18% [Connecting to 16.101.160.111 (16.101.160.111)] [Connecting to 16.101.160.1
usr@usr:~$ sudo gedit /etc/apt/apt.conf
Password:
use@usr:~$
use@usr:~$

my apt.conf file shows which is the correct proxy

Acquire::http::Proxy "16.111.160.101";


is there another file that i should edit to fix this


Synaptic -> Settings -> Preferences -> Network, and select Manual Proxy Configuration

i also restarted the pc a couple of times after changing proxy to see if the settings were set.. which showed up after a few reboots so i did change it correctly

---

### Post by unknownlaopoet on 2007-06-22
> **unknownlaopoet said:**
> I had set up my proxy wrong earlier, but after changing proxy in pereferences it still sees the old proxy when i try to update

here is what i did



usr@usr:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
18% [Connecting to 16.101.160.111 (16.101.160.111)] [Connecting to 16.101.160.1
usr@usr:~$ sudo gedit /etc/apt/apt.conf
Password:
use@usr:~$
use@usr:~$

my apt.conf file shows which is the correct proxy

Acquire::http::Proxy "16.111.160.101";


is there another file that i should edit to fix this


Synaptic -> Settings -> Preferences -> Network, and select Manual Proxy Configuration

i also restarted the pc a couple of times after changing proxy to see if the settings were set.. which showed up after a few reboots so i did change it correctly


STILL NO ANSWER, JUST REPOSTING SINCE NO1 RESPONDED YET

---

### Post by dannyboy79 on 2007-06-22
you don't ever need to yell within these forums and actually it's specifically written in the code of conduct not to. So please refrain from capitalizing your statements next time.

Have you verified that your proxy setting is not anywhere else, like within resolve.conf or /etc/network/interfaces?  Have you checked within the normal Network preferences, meaning not the Synaptic Prefs?

---

### Post by airtonix on 2007-07-04
opposite problem here. 

apt-get and thus synaptic are throwing errors about a proxy config i have already removed.

its crying it cant find a proxy server on such and such ip : port...

thus i search for config....and find that no such config specifying any such ip : port..

am i missing the proper config file for gnome-proxy?


worth noting i have also removed the nautilus and gnome-panel

---

### Post by mooha on 2007-07-04
Check this out:

[http://ubuntuforums.org/showthread.php?p=2964196#post2964196](http://ubuntuforums.org/showthread.php?p=2964196#post2964196)


this is something is missing in Ubuntu ... some thing like a control center which every software depend on it's configuration, that why I love the Yast2 it's fantastic in the same network Opensuse worked much better with proxy specially the software installation. yes there is a proxy configuration on Synaptic but in my opinion that's a joke. there ain't no Proxy configuration with Synaptic... many people got confused.

Good luck

---

### Post by Offoffoff on 2007-07-06
Just go to the System/Preferences/Network Proxy and do everything U want with proxy.

> **mooha said:**
> Check this out:

[http://ubuntuforums.org/showthread.php?p=2964196#post2964196](http://ubuntuforums.org/showthread.php?p=2964196#post2964196)


this is something is missing in Ubuntu ... some thing like a control center which every software depend on it's configuration, that why I love the Yast2 it's fantastic in the same network Opensuse worked much better with proxy specially the software installation. yes there is a proxy configuration on Synaptic but in my opinion that's a joke. there ain't no Proxy configuration with Synaptic... many people got confused.

Good luck

---

