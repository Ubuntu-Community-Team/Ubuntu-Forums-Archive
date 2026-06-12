---
title: "What's the preferred method for offline updating?"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by aguy2 on 2014-07-25
There are quite a few offline update methods out there, e.g. apt-offline, apt-get, AptMedium, Keryx, etc. Is there any differences in terms of convenience, integrity, or security? Which one is preferred? Which one should be stayed away?

---

### Post by ibjsb4 on 2014-07-25
I do not update off-line so really can't say whats good.  I do think that the Keryx project is no longer maintained.  Here's whats in the forum:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=offline+update&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=offline+update&as_qdr=all&sa=Google+Search&lang=en)

I can give you a tip.  Clean up your software sources so you won't be downloading unnecessary stuff. If you want, post your sources list (please use code tags) so we can have a look at it.

Open a terminal and enter:
```
cat /etc/apt/sources.list
```
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

