---
title: "Fresh reinstall of Mediatomb"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by mocka on 2011-04-04
As I tried to stream with an old install of Mediatomb this evening, I noticed I couldn't stream certain files. So I looked into the config.xml and found that it missed some lines necessary.

Therefore I tried to reinstall mediatomb (apt-get reinstall mediatomb-common etc.). However this did not change the config.xml in any way, so I thought that if I just deleted the file, I'd surely get a new one. If it'd just been as easy as that.. :P

So what happens when I now try to start mediatomb is the following:
```
* Starting upnp media server mediatomb                                  [fail]
```

Are there any good souls out there who might have an answer to my agonies?

Is it possible to do a completely fresh reinstall of mediatomb?

---

### Post by Wickd on 2012-04-16
Hi

Know this post is already a year old. But just found the solution to this. When mediatomb is installed, it also installs mediatomb-common and mediatomb-daemon

So basically you want to run:

Apt-get remove --purge mediatomb
Apt-get remove --purge mediatomb-common
Apt-get clean

Rm -r /usr/local/mediatomb
Rm -r ~/.mediatomb
Rm -r /etc/mediatomb

This should clean all. Also restarted to be safe.

** Note ignore the caps in the above commands. Typed this from my tab and the bloody thing just adds auto caps :(

---

