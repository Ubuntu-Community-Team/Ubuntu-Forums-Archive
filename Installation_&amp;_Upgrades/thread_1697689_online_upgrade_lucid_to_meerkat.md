---
title: "online upgrade lucid to meerkat"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by nuffink666 on 2011-03-01
have got the instructions to upgrade lucid to meerkat so :-


[LIST]
[*]changed update manager to release mode "normal releases" and complied with request for admin password
[*]get new upgrade to 10.10 option avail in update manager
[*]select upgrade
[*]get dialogue box with release notes and terms - pressed "upgrade"
[*]get distribution upgrade dialogue box which says its preparing upgrade
[*]fetch completes on 74 from 74 files
[*]Aaaaaaaaargh dialogue box disappears so next activity of selecting channels doesnt invoke and that's all I get..............NOTHING happens!!!!!! no messages, no reason, tried 2 different internet connections to make sure wasn't a authority issue
[/LIST]
any ideas where to look for possible reasons why or if anyone had same issues. Have all the latest lucid "fixes" etc installed. :confused:

---

### Post by zvacet on 2011-03-01
```
cat /etc/apt/sources.list
```and see if it changed from Lucid to Maverick.If it is

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by nuffink666 on 2011-03-01
ZVACET - cheers for the reply but the output of sources.list file is still very much lucid x64 and no mention of meerkat. it seems to download these 74 files but then nothing just literally disappears

---

### Post by nuffink666 on 2011-03-07
Morning ppl,

Still have not resolved this issue for upgrading via update manager from lynx to meerkat, if i was to do it via iso or DVD will it work as well? as have read many threads where people have had issues, kinda wondering what or where i can look to see why the download didnt work or upgrade - looked in syslog but not 100% sure what i was looking for

---

### Post by mörgæs on 2011-03-07
You are investing a lot of time in this project. I guess that the fast and secure method is a fresh install:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

