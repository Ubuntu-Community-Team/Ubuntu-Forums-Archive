---
title: "No virtual terminals: ctrl-alt-f1 etc give just blinking cursor"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by spookypeanut on 2007-04-19
I upgraded to feisty last night (before the rush :)), and mostly it went well. However, when I press ctrl-alt-f1 - f6 now, I don't get my beloved virtual terminals. On most of them I just get a blinking cursor, and f1 gives me what I'd expect, the "Booting 'Ubuntu..." message. The last line, I don't know if it's relevant, says

mdadm: No devices listed in conf file were found.

I've had a look in /etc/inittab, and it all looks fine, e.g.

1:2345:respawn:/sbin/getty 38400 tty1

Which I believe is right. Anyone got any suggestions what might be going on?

---

### Post by louieb on 2007-04-19
I know there a bug using ALT+F# when using switch user to have two users logged on at the same time. I can make my Feisty install lock up so tight I have to power off. I've see it reported launchpad. Haven't had a problem  with Alt +F1 yet but don't use it very much.   But maybe it related to the same problem.

---

### Post by neoaddict on 2007-04-23
[http://brianpwns.com/2007/04/15/fixing-your-gettyvirtual-terminal-pt-ii/](http://brianpwns.com/2007/04/15/fixing-your-gettyvirtual-terminal-pt-ii/)

That worked for me only when you're logged in, but what I'd recommend is doing a clean install to replace your tty files - that's what I did during my dist-upgrade.

---

### Post by spookypeanut on 2007-08-15
Apologies for dredging this up, but I just stumbled on this thread again, so thought I'd give the solution that I eventually found in case it's useful to others. It was a problem with a migration:

[https://bugs.launchpad.net/ubuntu/+bug/89314/comments/10](https://bugs.launchpad.net/ubuntu/+bug/89314/comments/10)

Hope it's helpful!

---

