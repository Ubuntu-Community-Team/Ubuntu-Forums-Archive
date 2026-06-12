---
title: "quickie: ubuntuy warty -&gt; ubuntu hoary"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by aroldo on 2005-07-30
I am a desktop user and work with ubuntu in order to do as little os admninistration as possible. I want to upgrade from ubuntu warty to ubuntu hoary. Is it enough just to overwrite "ubuntu  ... warty" with "ubuntu ... hoary" everywhere  in "/etc/apt/sources.list" and then call "apt-get update" and then  "apt-get dist-upgrade"? Am I missing something here?

---

### Post by bored2k on 2005-07-30
[QUOTE=aroldo]I am a desktop user and work with ubuntu in order to do as little os admninistration as possible. I want to upgrade from ubuntu warty to ubuntu hoary. Is it enough just to overwrite "ubuntu  ... warty" with "ubuntu ... hoary" everywhere  in "/etc/apt/sources.list" and then call "apt-get update" and then  "apt-get dist-upgrade"? Am I missing something here?[/QUOTE]
 Yes

1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
* To avoid any trouble *
2. sudo apt-get install ubuntu-desktop
3. sudo apt-get dist-upgrade

---

