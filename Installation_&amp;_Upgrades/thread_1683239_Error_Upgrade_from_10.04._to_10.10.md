---
title: "Error Upgrade from 10.04. to 10.10"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by AbangBoltok on 2011-02-07
This is the error message:

```
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
```i tried this trick:
 ```
[http://www.linuxforums.org/forum/debian-linux/59318-package-problem-broken-dependency-more.html](http://www.linuxforums.org/forum/debian-linux/59318-package-problem-broken-dependency-more.html)
``````

apt-get  clean 
apt-get  autoclean
apt-get  update
apt-get  upgrade
apt-get dist-upgrade
 
```but it seems don't work.

i hope you guys want to help me.
thanks.

---

### Post by mikewhatever on 2011-02-07
A log in /var/log/dist-upgrade/ should have the detailed answer for you.

---

### Post by AbangBoltok on 2011-02-07
this is the content of main.log.

[http://tinypaste.com/169422](http://tinypaste.com/169422)

i dont quite understand. :(

---

### Post by AbangBoltok on 2011-02-07
I tried to comment some lines on source.list that i think they are not from ubuntu or not supported by ubuntu.
and after that I cleared the cache, update, upgrade,

doesn't work either.

anyone..?

---

### Post by AbangBoltok on 2011-03-17
I gave up fixing this error.
but i kept upgrading my kernel and system software,,, whatever they are... then now i can upgrade my Ubuntu without any magic trick. :D

[IMG]http://img340.imageshack.us/img340/7819/screenshot8wr.png[/IMG]

---

